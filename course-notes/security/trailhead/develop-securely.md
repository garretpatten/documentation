# Develop Securely Trailhead

- Implement Security Fundamentals
  - A self-inflicted cybersecurity threat is one that comes from inside
    your organization
    - These internal attacks can be from a malicious insider
    - They can also arise when an employee accidentally allows attackers
      to compromise their user account or unknowingly downloads dangerous
      malware onto their workstation
  - Self-inflicted incidents also burn up a substantial number of
    resources.
    - This includes time spent by your legal, public relations,
      technology, communications, support, and incident response teams,
      who typically have to pause their regular workloads to attend to
      security breaches.
  - Select employees at your organization, such as developers,
    engineers, and documentation teams, may have access to systems in
    production to manage, apply, and verify configuration settings - a
    vulnerability introduced through a change to the security controls
    of a production environment is known as a Change-Induced Incident
- Three Security Pillars
  - CIA Triad of Confidentiality, Integrity, Availability
  - Confidentiality is the security principle that controls access to
    information — it ensures that access to sensitive information is
    given only to those who need it
  - Integrity ensures that sensitive data is trustworthy and accurate
    and that it is maintained in a consistent, correct, and reliable
    manner across its lifecycle
    - It also means protecting sensitive data in transit (when data is
      moved, such as across a network of the internet) and at rest (when
      data is stored, such as in a database) to make sure it is not
      altered when implementing security measures such as file
      permissions and user access controls
    - Backups and Redundancy Plans are a key element of integrity
      - These ensure that if a file has been modified or corrupted, it
        can be reset to the most recent, accurate, and trustworthy
        version
      - Redundancy controls are also crucial in case of a
        nonhuman-caused event, such as a server crash or an
        environmental failure
  - Availability means that authorized users have reliable access to
    the systems and resources they need and that systems are upgraded
    on a consistent and prompt basis
    - You can enable availability by having quick and adaptive disaster
      recovery plans for worst-case scenarios
      - These plans help safeguard against interruptions in connections
        and data loss in case of a natural disaster, fire, or even
        malicious activities such as denial-of-service (DoS) attacks
        and network intrusions
- Learn the OWASP Top 10
  - OWASP (Open Web Application Security Project) is an open-source
    project spreads the word about application security vulnerabilities,
    best practices, and remediations
    - The project provides free tools, libraries, and application
      programming interfaces (APIs) to help developers build secure and
      robust applications
    - Every few years, the project compiles a list of the 10 most
      common and dangerous types of web attacks, known as the OWASP Top
      10
- OWASP Top 10:
  - Broken Access Control
  - Cryptographic Failures
  - Injection
  - Insecure Design
  - Security Misconfiguration
  - Vulnerable and Outdated Components
  - Identification and Authentication Failures
  - Software and Data Integrity Failures
  - Security Logging and Monitoring Failures
  - Server-Side Request Forgery
- Bug Bounty, OWASP, and You
  - Bug bounty programs work by offering a monetary reward, or bounty,
    to security researchers who responsibly disclose security issues (or
    bugs) they find on your systems
    - This helps your security and product teams secure your products
      and minimizes the impact of zero-day attacks, those that result
      from unknown vulnerabilities in an organization
  - HackerOne Platform maintains one of the most comprehensive lists of
    Bug Bounty Programs on the internet — discovered vulnerabilities in
    2020 fall into the following buckets:
    - Cross-Site Scripting (XSS): 23%
    - Information Disclosure: 18%
    - Improper Access Control: 10%
    - Improper Authentication: 7%
    - Violation of Secure Design Principles: 6%
  - Companies such as Checkmarx, Snyk, and WhiteSource provide tools
    for software composition analysis (SCA)
    - These scan source code and identify security vulnerabilities such
      as buffer overflows, SQL injection, XSS, and information
      disclosure vulnerabilities, as well as the rest of the OWASP Top
      10, SANS 25, and other standard awareness documents used in the
      security industry
- Prevent Cross-Site Scripting and Injection Attacks
  - External attacks occur when someone outside your organization's
    systems manages to gain entry in order to inflict damage
  - 3 Types of XSS Attacks:
    - Stored XSS — occurs when malicious input is permanently stored on
      a server and later returned to users who browse the site normally,
      such as with a message board post or data in a user profile
    - Reflected XSS — occurs when malicious input is sent to a server
      and reflected back to the user on the response page
    - DOM-based XSS — occurs as a result of modifying the DOM in the
      user's browser; with a DOM-based XSS attack, the web page isn't
      changed, but its client-side code executes in a malicious way due
      to the DOM modifications
  - XSS is caused by weak separation between code context (the actual
    commands and variables used in a program) and user data (the input
    from a user)
  - Input Filtering — based on the idea that malicious attacks are
    best caught at the point of user input
  - Output Encoding — prevents unwanted code in the system from
    executing such that a server takes all characters that are
    meaningful in a specific context (HTML, uniform resource locator
    (URL), JavaScript), and replaces them with a text version
  - Other types of injection:
    - Lightweight directory Access Protocol (LDAP) injection
    - Operating System (OS) command injection
    - Extensible Markup Language (XML) Path (XPath) injection
    - Structured Query Language (SQL) injection
  - You can mitigate the risk of SQL injection with the following:
    - PreparedStatement (Java user input data type enforcement)
    - ParameterizedStatements (.NET user input data type enforcement)
    - Stored Procedures
      - You can avoid dynamic SQL statements by using stored procedures
        — when passing user input from a web application to stored
        procedures, you can only pass the information through
        PreparedStatements or ParameterizedStatements
    - Escaping
      - Escaping is a method that instructs a computer to do something
        special with the text you supply or to ignore the special
        function of a character — developers can use escaping routines
        to prevent the database from mistaking user input for SQL code
- Prevent Extensible Markup Language External Entity Attacks
  - Extensible Markup Language (XML) is a markup language, much like
    Hypertext Markup Language (HTML), that stores and transports data
  - An XML parser is a software library or package that provides an
    interface for an application running on a user's machine to work
    with XML documents
    - It checks for proper format of XML documents and may also validate
      these. A parser's goal is to transform XML into readable code
  - An XXE attack occurs when a weakly configured XML parser processes
    XML input containing a reference to an external entity
    - An attacker can use this flaw to extract data, execute a remote
      request from the server, scan internal systems, and more
    - The attack could disclose internal content via Hypertext Transfer
      Protocol Secure (HTTPS) requests or even launch a Cross-Site
      Request Forgery (CSRF) attack
  - The safest way to prevent XXE attacks is to always disable DTDs
    (Document Type Definitions — external entities) completely
    - Disabling DTDs also secures the parser against denial of service
      (DoS) attacks; if DTDs can't be disabled completely, then
      external entities and doctypes must be disabled in a way specific
      to each parser.
- Secure Your Organization’s Internal Resources
  - Internal resources are the safety features you build into your code
    to ensure that your processes, policies, and procedures protect your
    organization's assets and the trust your customers place in you
  - 3 Internal Resource Controls (OWASP):
    - Broken Authentication and Session Management
    - Sensitive Data Exposure
    - Broken Access Control
  - Authentication is the process of proving or showing something to be
    true, genuine, or valid
  - Session management refers to the process of securely handling
    multiple requests to a web application or service from a single
    user or entity
  - Session management attacks usually occur when attackers gain access
    to unexpired session tokens
    - Example: Let's say that an application does not rotate session IDs
      after successful login or isn't properly invalidating session IDs
      during logout or a period of inactivity. A user accesses the
      application on a public computer. Instead of selecting "log out,"
      the user closes the browser tab and walks away. An attacker uses
      the same browser an hour later and the user is still authenticated.
      Their sensitive data has been exposed.
  - Strong Authentication Mechanisms
    - Strengthening Your Password Controls — MFA & Weak Password Checks
    - Limiting Password Attempts
    - Avoiding Verbose Failure Messages
  - System with weak session management include those that do the following:
    - Expose session IDs in the Uniform Resource Locator (URL)
    - Fail to rotate session IDs after successful login
    - Fail to properly invalidate session IDs or authentication tokens
      during logout or after a period of inactivity
  - Strong Session Management
    - Use Strong Tokens
      - Use tokens that contain enough entropy (randomness) to prevent
        attackers from identifying their value
        - Web development frameworks such as Java EE (JEE), .NET, and
          Hypertext Preprocessor (PHP) provide session management
          features and implementation
    - Handle Tokens Securely
      - To protect the session ID exchange from active eavesdropping and
        passive disclosure in network traffic, use an encrypted
        Hypertext Transfer Protocol Secure (HTTPS) Transport Layer
        Security (TLS) connection for the entire web session, not just
        the authentication process
      - To ensure the session ID is exchanged only through an encrypted
        channel, use the secure cookie attribute, an option that can be
        set by the application server when sending a new cookie to the
        user within an HTTP Response
- Prevent Data Exposure
  - There are several ways to minimize data exposure:
    - Don't store sensitive data unless it is absolutely necessary. If
      you must do so, make sure it is encrypted and discard it as soon
      as possible.
    - Use up-to-date, strong, standard algorithms, protocols, and keys.
      Not all algorithms are created equal. For instance, the Message
      Digest algorithm 5 (MD5) and Rivest Cipher 4 (RC4) algorithms are
      known to have extensive vulnerabilities and thus should never be
      used to secure data. Use proper key management and encrypt all
      data in transit with transport layer security (TLS) and enforce
      encryption with HTTP Strict Transport Security (HSTS).
    - Disable caching for responses that contain sensitive data. Store
      passwords using strong, nonreversible, adaptive, and salted
      hashing functions with a work factor such as Argon2, scrypt,
      bcrypt, or password-based key derivation function (PBKDF2). A
      salted hash function is one that adds extra random data, which
      further protects the output from common methods of attack. A work
      factor is the number of times an algorithm is run.
- Defend Against Broken Access Control
  - Access Control refers to how you restrict users' permissions —
    access control failure leads to consequences like unauthorized
    information disclosure, modification or destruction of data, and
    performance of business functions outside a user's limits:
    - Bypassing access control checks.
    - Allowing the primary key or unique identifier to be changed to
      another user's record.
    - Elevating a user’s privilege.
    - Manipulating metadata.
    - Forced browsing to authenticated pages as an unauthenticated user
      or to privileged pages as a standard user.
    - Allowing access to application programming interfaces (APIs) with
      missing access controls for POST, PUT, and DELETE Hypertext
      Transfer Protocol (HTTP) methods. These commands correspond to
      create, update, and delete, respectively, and are some of the
      most commonly used HTTP verbs.
- Preventing Broken Access Control Attacks
  - Access control is effective only if enforced in trusted server-side
    code or a serverless API, where attackers can't modify the access
    control check or metadata:
    - Deny by default. Implement access control mechanisms only once,
      then reuse them throughout the application. This creates a single
      location to troubleshoot and prevents conflicting access controls.
    - Set access controls so that users can't create, read, update, or
      delete them.
    - Design your application to function only in the domain it needs
      and ensure that web server directory listings are disabled.
    - Log access control failures and rate limit API and controller
      access.
    - Invalidate JavaScript Object Notation (JSON) Web Tokens (JWT)
      after logout.
    - Include functional access control, unit, and integration tests,
      which test a slice of the program to ensure it is performing as
      expected.

- Use a Secure Development Lifecycle
  - The secure development lifecycle (SDL) integrates security
    throughout all stages of your development cycle
    - From requirements to design, coding to test, the SDL strives to
      build security into a product or application at every step in the
      process
  - Security and privacy are key concerns with cloud computing, and
    using good security protocols is one way to reassure customers that
    web applications running on cloud platforms are doing so in a safe
    and trusted environment
    - Secure public cloud development requires that security
      considerations be integrated into the design and planning phases
      of software development
  - 7 Stages of the SDL:
    - Learn
    - Design
    - Build
    - Verify
    - Release
    - Own
    - Reflect
- Start With a Security Assessment
  - A security assessment checks for vulnerabilities and ranks ongoing
    engineering work by level of risk
    - Implementing a security assessment gives you a formal process to
      examine security risks and define the specific steps required to
      mitigate those issues before release
  - Secure By Design (SBD) is a key cybersecurity principle, and one
    that's crucial to the secure development lifecycle (SDL)
    - SBD means designing software to be secure from the outset to
      reduce the likelihood of flaws that might compromise an
      organization's security
  - A good security assessment program has four goals:
    - Empower engineers with clear security requirements
    - Increase automation to cut down on manual tasks and boost consistency
    - Track security actions and tasking
    - Integrate security into development at every stage
  - Here are some things you’ll want to look for:
    - Questionnaires that are specific to your team
    - Suggested security tasks that are based on your answers
    - Questionnaires and tasks that can be quickly updated as threats change
    - Multiple user stories or an epic that can be attached to one approval
- Practice Security By Design
  - While in the past it was common to leave security features until
    late in the development cycle, it has become clear that designing
    from the start with security in mind reduces the likelihood of flaws
    that might compromise an organization's security
    - SBD is more important than ever as the industry moves to cloud
      computing and increasingly adopts other new technology
  - Take into account:
    - Environment
    - Potential Risks
    - Severity
    - Impact
- Model Your Threats
  - In general, threat modeling involves five steps:
    - Agree on security objectives
    - Describe your architecture by creating a data-flow diagram
    - Identify the threats to your project by examining your
      organization's assets and vulnerabilities
    - Identify mitigations to the threats (possible and verified) that
      you found in your project
    - Build and validate the defenses for your project
- Design and Build Securely
  - Apply Defense in Depth — Design multiple layers of security like
    multi-factor authentication (MFA) and add additional internal
    authentication mechanisms like mutual Transport Layer Security
    (TLS) to help stop attackers if they do manage to compromise part
    of a system
  - Use Least Privilege — Give users, applications, systems, and other
    components only the most restrictive permissions needed to do the
    job and nothing more
  - Use Secure Defaults — Configure your software environment to have
    secure settings by default that users can opt out of, instead of
    requiring them to opt in to secure settings
  - Minimize Attack Surface — Every port you open, every external
    library you use in your code, and every user you give access to
    your data expands the attack surface
  - Use a Positive Security Model — A positive security model or
    safelist approach is one that defines what is allowed and rejects
    everything else
  - Fail Securely — Implement decision logic that puts systems into a
    secure state when errors occur
  - Protect Customer Data — Customers own their data and should have
    control over it; it's important to make sure that customer data is
    always secure, both at rest and in transit
  - Don't Trust External Data or Input — Data must always be handled as
    if it is untrustworthy
- Create Security Acceptance Criteria
  - Acceptance criteria must be expressed clearly, in simple language,
    without ambiguity as to what the expected outcome is
- Test and Verify Securely
  - Security uncovers vulnerabilities in your system so you can fix
    them, and it verifies that the data and resources of the system are
    protected from possible intruders
  - Penetration testing is a procedure for testing the security of a
    system or software application by making a deliberate attempt to
    compromise its security
  - There are two powerful analysis methods that you can also run on
    your development: static analysis and dynamic analysis (each has
    strengths and weaknesses and both can expose security issues in
    your development so that you can fix them before release)
    - Static application security testing (SAST) looks at the source
      code without executing the program
    - Dynamic analysis takes the opposite approach and is executed while
      a program is in operation
      - Dynamic application security testing (DAST) simulates attacks
        against a web application and analyzes the application's
        reactions, determining whether it is vulnerable
  - Dynamic analysis generally has lower code coverage than static
    analysis
    - Some vulnerabilities that dynamic testing can detect include
      cross-site scripting (XSS), SQL injection, command injection,
      path traversal, and insecure server configuration
    - In some cases, like cross-site request forgery (CSRF), dynamic
      testing is much faster than static analysis
  - Static code analysis is usually performed as part of a code review
    - One big advantage of SAST tools is that they provide immediate
      feedback — you want to use these tools during code development so
      you can prevent vulnerabilities as you work
- Maintain Security Post Release
  - Successful ownership requires:
    - Relevant materials from the design stage of your project
    - Documented ownership describing who owns and is responsible for the service
    - Documented escalation paths for product and security issues
    - A service catalog entry that you can submit to the service catalog
      team
    - Consensus on a service-level agreement (SLA) and best practices
      so relevant security patches can be quickly installed
    - Agreement on a roadmap for the remediation of noted risk exceptions
    - Agreement on maintenance and updates of your threat model
  - Part of ownership involves patching the third-party code your project
    lives on
    - Not patching is similar to not mitigating threats during the design
      stage — attackers are out there looking for unpatched
      vulnerabilities

- Learn About Threat Modeling
  - Threat modeling is a structured approach for analyzing a system to
    assess risk, identify threats, and pinpoint mitigations to address
    those threats.
- What is a Threat
  - A threat is anything that can intentionally or accidentally exploit
    a vulnerability—a weakness or gap in security—to obtain, damage, or
    destroy an asset. Assets are the things you're trying to protect:
    people, property, and information.
  - Your assets depend on your organization, but most organizations'
    greatest assets are collections of information.
    - Your reputation is also an asset, one that hinges on your
      customers' perception of how effectively you protect their
      information.
  - Threat modeling boils down to reducing risk.
    - Risk is the potential for loss, damage, or destruction of an
      asset as a result of a threat taking advantage of a
      vulnerability.
- Threat Modeling Process
  - Overall, you can think of threat modeling as a five-step process.
    - Agree on security objectives.
    - Describe your architecture by creating a data-flow diagram.
    - Identify threats.
    - Identify mitigations to the threats (possible and verified).
    - Build and validate the defenses.
- Agreeing on Security Objectives
  - This involves three steps.
    - Identify the system assets.
    - Define what the attackers are after.
    - Identify any security assumptions.
- Describe the System with a Data-Flow Diagram
  - A data-flow diagram shows how a certain type of data flows from one
    part of a system to another.
  - Core Components:
    - Data Flow (arrow)
    - Entity (rectangle)
      - Divided into sources (users, producers, clients, inputs, IoT
        sensors, etc) and destinations (other users, server systems,
        consumers, IoT output, displays, etc)
    - Process (oval)
    - Data Store (cylinder)
    - Trust Boundary (rectangle with dashed border/dashed line)
- Spot the Threats
  - Attacker Archetypes:
    - Hacktivists - These attackers want to damage a company's
      reputation to make a statement or to further a political agenda.
    - Cybercriminals - Attackers who work together to stealthily obtain
      valuable customer data to sell on the black market
    - Cyber Warriors - Attackers who seek to gain access to
      intellectual property to advance the government interests of a
      nation-state
- The STRIDE Mnemonic
  - STRIDE: a mnemonic that stands for Spoofing, Tampering,
    Repudiation, Information Disclosure, Denial of Service, and
    Elevation of Privilege.
  - Spoofing: an attacker pretends to be someone or something that they’re not
  - Tampering: an attacker can modify of delete data
  - Repudiation: an attacker can perform some action and deny it later
    because there is no record or evidence captured
  - Information Disclosure: an attacker obtains access to data that
    should be protected
  - Denial of Service (DoS): an attacker does something to degrade a
    service or deny it to other entities
  - Elevation of Privilege (EoP): an attacker figures out a way to do
    something or obtain access to something despite not having the
    permissions
- Identifying Mitigations
  - Mitigations are either total or partial
    - Total or full mitigations make threats out of reach for attackers
      in some way—for example, a total mitigation might make a threat
      too expensive or too hard to pull off
    - Partial mitigations are layered or combined to reduce the overall
      amount of risk
      - With partial mitigations, it is important to avoid creating a
        weakest link — attackers often try to exploit the easiest things
        first
  - One vulnerability can make other threats more plausible
  - There are two paths forward when vulnerabilities are known and
    deadlines are approaching — Redesign & Risk Acceptance
  - Redesign means going back to the drawing board — adjusting the
    features to add usable security or to remove problematic areas
  - Risk Acceptance means deciding to live with the risk, either
    temporarily or permanently
    - Perfection is the enemy of good in practical, secure design
    - Achieving 100% security is almost impossible
  - The output of the threat modeling exercise lets you make an
    informed, rational decision on building systems that contain some
    residual risk
    - The exact process of risk acceptance can depend on your team and
      technology and requires executive-level agreement

- What is Privileged Access Management (PAM)
  - Access control decisions govern who should be granted access, what
    they should be granted access to, and the methods of enforcing
    access and restriction.
  - Someone has to be in charge of setting and monitoring these access
    features, and that person is said to have privileged access.
  - Privileged access management (PAM) is the set of cybersecurity
    strategies and technologies that organizations use to control levels
    of access and permissions for users, accounts, processes, and
    systems.
  - Privileged users include:
    - Operating and Network System Admins
    - Database Admins
    - Domain Admins
    - Application Admins
    - Local Admins
      - Users with administrative access to the local systems, such as
        IT staff who perform maintenance or set up new workstations
