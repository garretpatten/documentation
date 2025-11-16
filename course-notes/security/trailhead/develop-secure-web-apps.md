# Develop Secure Web Apps Trailhead

- Run Health Check
  - Health Check is a dashboard that lets you see how closely the
    security settings in your org align to the settings recommended by
    Salesforce
    - A score of 0–100 is displayed, 100 being the most secure setting
      configuration
  - Enable the following security settings:
    - Require HTTPOnly Attribute
    - Enable User Certificates
    - Enable Clickjack Protection
    - Require HTTPS
    - Session Timeout
    - Enable Cross-Site Scripting (XSS) Protection
    - Use the Latest Version of Locker - Lightning Locker provides
      component isolation and security that allows code from many sources
      to execute and interact using safe, standard APIs and event
      mechanisms
- Protect Apps with Shield
  - Salesforce Shield is a set of security tools that admins and
    developers can use to protect business-critical apps with
    capabilities like enhanced encryption and event monitoring
  - Platform Encryption is designed to let you retain critical app
    functionality—like search, workflow, and validation rules—so you
    maintain full control over encryption keys and can set encrypted data
    permissions to protect sensitive data from unauthorized users
    - Platform encryption allows you to natively encrypt your most
      sensitive data at rest across all of your Salesforce apps
  - Event Monitoring gives you access to detailed performance, security,
    and usage data on all of your Salesforce apps
  - Field Audit Trail lets you know the state and value of your data for
    any date, at any time
- Build Secure Apps with Lightning Web Components
  - LWC is secured with Locker by default, which prevents components from
    accessing the data and Document Object Model (DOM) of other components
    from other namespaces
  - LWC offers its own built-in security features, such as sanitization
    of malformed HTML code and blocking Content Security Policy
    (CSP)-incompatible code
  - Security Features in Lightning Locker:
    - JavaScript Strict Mode Enforcement
    - DOM Access Containment
    - Secure Wrappers
    - eval() Function Limits
    - Analysis of MIME Types
    - Limited Access to API Framework
- LWC Security Best Practices
  - Properly Configured Event Propagation
  - Principle of Least Privilege
  - Secure by Default
  - Separation of Concerns
  - Properly Evaluate Third-Party Dependencies
- Mitigate Cross-Site Scripting
  - Common XSS attack types:
    - Arbitrary Requests
    - Malware Download
    - Log Keystrokes
  - Common Mitigations:
    - Input Filtering
      - Blocklisting
      - Allowlisting
    - Output Encoding — output encoding techniques take the opposite
      approach by preventing malicious payloads already in the system
      from executing
      - In fact, output encoding is often considered more necessary than
        input encoding because it doesn't rely on any upstream or
        downstream protections, and it can't be bypassed by alternative
        input pathways
- Write Content Security Policy-Compatible Code
  - CSP is a computer security standard intended to help web designers
    and server administrators specify how content interacts on their
    websites
  - CSP provides a standard method for website owners to declare approved
    origins of content that browsers are allowed to load on that website
    - Covered content types include JavaScript, CSS, HTML frames, web
      workers, fonts, images, embeddable objects such as Java applets,
      ActiveX, audio and video files, and other HTML5 features
  - CSP is a set of security rules maintained by the World Wide Web
    Consortium (W3C) and is implemented in all major web browsers
- How is CSP Implemented in Salesforce
  - Blocking Inline Script
  - Filtering a Dynamic Script
  - Add Third-Party APIs to Allowlist
  - Securely Load External Scripts
- Write Secure Apex Controllers
  - By default, Apex classes have the ability to read and update all data
    within an organization — therefore, it's crucial that you enforce
    sharing rules, set object and field permissions, and protect against
    CRUD and FLS
    - You will need to determine which code should be run as "system
      mode"—that is, with access privileges to many resources—and which
      code should be run as "user mode," in which the permissions,
      field-level security, and sharing rules of the current user are
      enforced
- Mitigate SOQL Injection
  - SOQL is essentially a customized version of SQL developed specifically
    for the Salesforce platform — SOQL is a language exclusively for
    querying the database rather than modifying data like in traditional
    SQL
  - What SOQL does not have:
    - INSERT, UPDATE, or DELETE statements. It only has SELECT statements.
    - Command execution.
    - Wild cards for fields; all fields must be explicitly typed.
    - JOIN statement; however, you can include information from parent
      objects like Select Name, Phone, and Account.Name from Contact.
    - UNION operator.
    - Ability to chain queries together.
  - There are a number of techniques you can use to prevent SOQL
    injection:
    - Static queries with bind variables
    - String.escapeSingleQuotes()
    - Type casting
    - Replacing characters
    - Allowlisting
- Mitigate Cross-Site Request Forgery
  - CSRF is a common web application vulnerability where a malicious
    application causes a user's client to perform an unwanted action on
    a trusted site for which the user is currently authenticated
    - A CSRF attack requires the targeted user to visit the attack page
      while authenticated with the targeted service, which often requires
      coordinated deception on the part of the attacker (this is most
      commonly seen in phishing campaigns)
  - Keys to prevent CSRF attacks:
    - All sensitive state-changing requests (anything performing database
      operations) must include the token.
    - The token must be unique to the request or user's session.
    - The token must be difficult to predict (long and random).
    - The token must be validated by the server to ensure the request
      originated from the intended user.
- Secure Secrets Storage
  - Secrets are data that can be used to verify what privileges a user
    has in a given situation:
    - Passwords and Passphrases
    - Encryption Keys
    - OAuth Tokens
    - Payment Information (PCI — credit card numbers and PINS)
    - SSNs
  - Secrets must be protected from different types of users:
    - Standard users
    - External users
    - Administrator users with administrative access
  - Salesforce has a number of features to store and protect secrets:
    - Named Credentials
      - A named credential specifies the URL of a callout endpoint and
        its required authentication parameters in one definition
    - Custom Settings (protected, unprotected, unmanaged, and managed)
      - Custom settings let you create custom sets of data that are
        exposed to the application cache, so you avoid repeated queries to
        the database and increase the efficiency of your app
      - Custom settings can have different levels of visibility
    - Custom Metadata Types
      - Custom metadata fields can be utilized for secret storage in a
        similar way to custom settings
      - For proper secrecy, set their visibility to "Protected" and
        contain them within a managed package
      - Protected custom metadata API fields are a great choice for
        storing API keys or other secret keys
- Use Encryption in Custom Applications
  - The Crypto class provides sets of functions that are particularly
    valuable for safeguarding your communications
    - Using these functions, you can effectively shield confidential data
      from eavesdroppers, verify that message data is complete and
      unmodified, and verify the authenticity of senders and receivers
    - Each of these functions support a range of different algorithms
  - The Crypto class provides:
    - Encryption and Decryption to Protect Confidentiality
    - Hash Digests to Protect Integrity
    - Hash-Based Message Authentication Codes (MACs) to Prove
      Authenticity and Integrity
    - Creating a Digital Signature
