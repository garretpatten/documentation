# Principles of Security

- The CIA triad is an information security model that is used in
  consideration throughout creating a security policy
  - This model has an extensive background, ranging from being used in 1998
- Consisting of three sections: Confidentiality, Integrity and Availability
  (CIA), this model has quickly become an industry standard today
- Whilst the three elements to the CIA triad can arguably overlap, if even
  just one element is not met, then the other two are rendered useless
  (similar to the fire triangle)
  - If a security policy does not answer these three sections, it is seldom
    an effective security policy
- Confidentiality: This element is the protection of data from unauthorized
  access and misuse
  - Organizations will always have some form of sensitive data stored on
    their systems
  - To provide confidentiality is to protect this data from parties that it
    is not intended for
- Integrity: The CIA triad element of integrity is the condition where
  information is kept accurate and consistent unless authorized changes are
  made
  - In the CIA triad, integrity is maintained when the information remains
    unchanged during storage, transmission, and usage not involving
    modification to the information
  - Steps must be taken to ensure data cannot be altered by unauthorized
    people (for example, in a breach of confidentiality)
- Availability: The main concern in the CIA triad is that the information
  should be available when authorized users need to access it -- in order
  for data to be useful, it must be available and accessible by the user
  - Availability is very often a key benchmark for an organization
  - When a system is unavailable, it often results in damage to an
    organization's reputation and loss of finances
  - Availability is achieved through a combination of many elements,
    including:
    - Having reliable and well-tested hardware for their information
      technology servers (i.e. reputable servers)
    - Having redundant technology and services in the case of failure of
      the primary
    - Implementing well-versed security protocols to protect technology
      and services from attack
- The levels of access given to individuals are determined on two primary
  factors:
  - The individual's role/function within the organization
  - The sensitivity of the information being stored on the system
- Two key concepts are used to assign and manage the access rights of
  individuals, two key concepts are used:
  - Privileged Identity Management (PIM): used to translate a user's role
    within an organization into an access role on a system
  - Privileged Access Management (PAM): management of the privileges a
    system's access role has
- The Bell-La Padula Model is used to achieve confidentiality
  - The model works by granting access to pieces of data (called objects)
    on a strictly need to know basis
  - This model uses the rule "no write down, no read up"
- The Bell LaPadula Model is popular within organizations such as
  governmental and military
  - This is because members of the organizations are presumed to have
    already gone through a process called vetting (a screening process
    where applicant's backgrounds are examined to establish the risk they
    pose to the organization)
- The Biba model is arguably the equivalent of the Bell-La Padula model but
  for the integrity of the CIA triad
  - This model applies the rule to objects (data) and subjects (users) that
    can be summarized as "no write up, no read down"
  - This rule means that subjects can create or write content to objects at
    or below their level but can only read the contents of objects above
    the subject's level
- The Biba model is used in organizations or situations where integrity is
  more important than confidentiality
- For example, in software development, developers may only have access to
  the code that is necessary for their job (they may not need access to
  critical pieces of information such as databases, etc)
- Threat modeling is the process of reviewing, improving, and testing the
  security protocols in place in an organization's information technology
  infrastructure and services
  - A critical stage of the threat modeling process is identifying likely
    threats that an application or system may face, the vulnerabilities a
    system or application may be vulnerable to
- The threat modeling process is very similar to a risk assessment made in
  workplaces for employees and customers. The principles all return to:
  - Preparation
  - Identification
  - Mitigations
  - Review
- It is, however, a complex process that needs constant review and
  discussion with a dedicated team. An effective threat model includes:
  - Threat intelligence
  - Asset identification
  - Mitigation capabilities
  - Risk assessment
- Threat Modeling frameworks:
  - STRIDE (Spoofing identity, Tampering with data, Repudiation threats,
    Information disclosure, Denial of Service, and Elevation of Privileges)
  - PASTA (Process for Attack Simulation and Threat Analysis)
- A breach of security is known as an incident
  - Actions taken to resolve and remediate the threat are known as Incident
    Response (IR) and are a whole career path in cybersecurity
  - An incident is responded to by a Computer Security Incident Response
    Team (CSIRT) which is prearranged group of employees with technical
    knowledge about the systems and/or current incident
