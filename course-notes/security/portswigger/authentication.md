# Authentication Vulnerabilities

## Vulnerabilities in Password-Based Login

- First, use Burp Suite Sniper attack to try different usernames
  (regardless of the password)
  - Note if responses are different for valid vs invalid usernames (Invalid
    username vs incorrect password, for example)
- If the error message is more generic, check to see if you can produce
  subtle differences
  - Maybe "Invalid username or password" where a period exists on one but
    not the other
    - Grep extract can help to automate this check
- If IP is blocked for too many attempts, see if IP spoofing is an option
  - Try using the `X-Forwarded-For` header changing the value to a
    different number each time
    - If this header is supported, this will bypass the IP block
- If given valid credentials in the scenario where an IP block exists and
  IP spoofing is not available, see if a valid login resets the IP block
  - If so, simply set up your attack to periodically login successfully
    with a request to allow you to continue brute forcing other login
    credentials
- Account locking can sometimes reveal valid vs invalid accounts. If you
  brute force potential usernames several times each, you may find that
  only some become locked with some sort of "You have made too many
  incorrect login attempts"
- If the credentials are passed through a DTO, try adding an array of
  passwords instead of a single value -- this may exploit a flaw in the
  authentication logic

## Vulnerabilities in Multi-Factor Authentication

- While it is sometimes possible for an attacker to obtain a single
  knowledge-based factor, such as a password, being able to simultaneously
  obtain another factor from an out-of-band source is considerably less
  likely
  - For this reason, two-factor authentication is demonstrably more secure
    than single-factor authentication
  - However, poorly implemented two-factor authentication can be beaten, or
    even bypassed entirely, just as single-factor authentication can
- If the user is first prompted to enter a password, and then prompted to
  enter a verification code on a separate page, the user is effectively in
  a "logged in" state before they have entered the verification code
  - In this case, it is worth testing to see if you can directly skip to
    "logged-in only" pages after completing the first authentication step
  - Occasionally, you will find that a website doesn't actually check
    whether or not you completed the second step before loading the page
- If you enter a valid username and password, you may see a request that
  generates a 2FA code given a username
  - You may be able to use this request to generate a token for another
    account -- do so
  - If a token is generated, capture the next request that submits a code
    to log a user in given that username and 2FA code
    - Use this request to brute force the 2FA code -- open the 302
      response in the browser to access the user's account having never
      provided a password
- If you have a username and password but cannot brute force the token
  because the process restarts given multiple incorrect attempts, create a
  macro to continue logging in before each brute force attempt
  - Project Options
  - Sessions
  - Session Handling Rules > Add
    - There will be two tabs, Details and Scope
    - Use Scope to set All URLs and select the requests needed to trigger
      a new attempt -- for the Expert lab, it's a Get /login, a POST
      /login, and a GET /login2
    - Once the Macro is created, test it. If it works, press OK until
      you've exited the Macro creation
  - Attempt to try a 2FA code and capture the POST /login2
    - Now, use an Intruder Sniper attack to brute force the 2FA code where
      the Macro runs before each request (make sure that the Resource Pool
      only has one concurrent thread at a time
