# Get Started with Application Security Trailhead

* The Role of Application Security
    * Security Engineers aim to ensure that an application provides what is commonly referred to as CIA: confidentiality, integrity, and availability.
        * For example, application security engineers help developers design and deploy the application in a way that requires proper authentication (to protect the confidentiality of data), transfers sensitive information securely to prevent it from being modified (integrity), and ensures that users can access their data (availability). 
* Application Security Engineer Skills
    * An application security engineer must have a good grasp of many technical skills, which include:
        * Threat modeling: Think about how attackers can compromise a system and what protections are needed against them
        * Secure Software Development Life Cycle (SSDLC): Help developers write secure code that minimizes vulnerabilities by implementing secure coding standards, techniques, and best practices
        * Security code reviews: Identify security vulnerabilities in source code before an application is deployed to production
        * Vulnerability testing and analysis: Discover weaknesses once an application is deployed and advise development teams on remediation
* On top of the skills listed above, the following certifications can bolster an application security engineer’s knowledge.
    * GIAC Web Application Defender (GWEB)
    * GIAC Secure Software Programmer (GSSP)
    * Certified Secure Software Lifecycle Professional (CSSLP)
    * Secure Software Practitioner (SSP)
    * Certified Application Security Engineer (CASE)
    * Advanced Web Attacks and Exploitation 
* Protect the Software Development Lifecycle
    * Because security issues can be introduced or discovered at any phase of an application’s lifecycle, the application security engineer has a continuous role to play in order to protect the confidentiality, integrity, and availability of the application’s data. Security is often thought of as a weakest link problem. Just as a strong metal chain can be broken if one link is compromised, each phase of the SDLC must be secured to secure the development, deployment, and maintenance of the application as a whole.
* Security Engineers use a variety of tools and techniques to help the development team protect the application and their customers’ data from attacks:
    * Source Code Review
    * Static Testing
    * Dynamic Testing
    * Automation Testing
    * Separation of Commands and Queries
        * Keeps data separate from commands and queries. The idea is that every method should either be a command that performs an action or a query that returns data to the caller, but never both. A query should never change the state of an application or its data and a command can change the state, but should never return a value.
    * Allowlists
        * Implementing allowlists of allowable characters or commands can validate user input and ensure that URL and form data can’t execute commands that use these characters or execute unallowed commands.
* Application Authentication and Access
    * The concept of granting and restricting access to resources is called authorization
    * The entire process of identifying, authenticating, and authorizing users is known as access control
    * Engineers run applications using the fewest privileges possible (a concept known as least privilege
    * Access control issues:
        * Horizontal: A horizontal issue occurs if one user can view/modify information of another user
        * Vertical: A vertical issue occurs if the user can gain administrative access inappropriately.
    * Broken Authentication: This occurs when an attacker gains unauthorized access to accounts and compromises a system.
    * Application security engineers protect applications against this risk by using several strategies.
        * Deny by default: If a request is not specifically allowed, it is denied. For example, if an administrator creates a new user account, the account should have minimal or no access by default until it is configured.
        * Least privilege: All users are given as little access as possible.
        * Enforce record ownership: Only certain users create, read, update, or delete any record.
        * Log access control failures: Create a record and alert admins when an incorrect password is entered.
        * Token management: Set expiration times for tokens and delete stored tokens upon log out. This prevents tokens from being used indefinitely and protects from an attacker tampering with tokens to elevate privileges.
        * Test early and often: Finally, the application security engineer tests for these access control protections during the quality assurance process and throughout the SDLC.
* Protect Sensitive Application Data from Exposure
    * Engineers work to secure all data transmissions, encrypt data at rest and in transit, and use strong algorithms and proper key management when implementing encryption.
    * Engineers implement encryption at the storage level in a server; at the database level in tables, columns, and rows; over transportation protocols such as Secure Hypertext Transport Protocol (HTTPS) or Transport Layer Security (TLS) and on the client (browser side). 
