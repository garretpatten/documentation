# GPG Commit Signing for GitHub on macOS

## 1. Install GPG

```sh
brew install gnupg pinentry-mac
mkdir -p ~/.gnupg
echo "pinentry-program $(which pinentry-mac)" >> ~/.gnupg/gpg-agent.conf
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/*
gpgconf --kill gpg-agent
```

## 2. Generate Key

```bash
gpg --full-generate-key
```

When prompted:

- Select **RSA and RSA** with **4096 bits**
- Use your **GitHub-verified email address**
- Set a strong passphrase

## 3. Identify Your Key ID

```bash
gpg --list-secret-keys --keyid-format=long
```

Look for the line starting with `sec`. The key ID is the string after the `/` (e.g., `sec   rsa4096/ABC123DEF456 2024-01-01` → key ID is `ABC123DEF456`).

## 4. Add Public Key to GitHub

```bash
gpg --armor --export <KEY_ID>
```

Copy the entire output (including `-----BEGIN PGP PUBLIC KEY BLOCK-----` and `-----END PGP PUBLIC KEY BLOCK-----`), then:

1. Go to GitHub → Settings → SSH and GPG keys
2. Click "New GPG key"
3. Paste the exported key and save

## 5. Configure Git

```bash
git config --global user.signingkey <KEY_ID>
git config --global commit.gpgsign true
git config --global gpg.program gpg
```

Replace `<KEY_ID>` with your actual key ID from step 3.

## 6. Verify Setup

```bash
git commit --allow-empty -m "test"
git log --show-signature -1
```

You should see `Good signature` in the output. Check your GitHub commits to see the "Verified" badge.

## 7. Generate Revocation Certificate

```bash
gpg --output revoke-<KEY_ID>.asc --gen-revoke <KEY_ID>
```

Store this certificate securely. Use it to revoke your key if it's compromised or lost. You'll need to upload it to GitHub or a keyserver.
