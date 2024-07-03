# Git Cheat Sheet

## Configuration

### Caching Credentials

- Generate PAT in GitHub through Developer Settings
- Copy token to secure place
- Configure git credential cache
    - `git config --global credential.helper cache`
    - `git config --global user.name "garretpatten"`
    - `git config --global user.email "garret.patten@proton.me"`
- Pull or push to a private repository
    - Enter username and personal access token
- The credentials should now be cached
