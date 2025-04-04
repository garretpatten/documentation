# AWS Security Best Practices

## Guidance

- Great follow up courses to this one
    - Architecting on AWS
    - Security Engineering on AWS

## Intro

- Instructor: Jacques Pace
- Labs will take place in AWS Builder Labs
- Course Materials: <https://online.vitalsource.com/reader/books/200-SISCBP-15-EN-SG-E/pageid/0>
    - Will be accessible for a year (until 12/15/24)

## Module 1: Security Overview

- AWS is responsible for the security OF the Cloud, and customers are reponsible for security IN the Cloud
    - Exactly where the line is drawn between AWS's and the customer's responsibility can depend on the service being consumed
- Security services (up to customer to use/enable):
    - AWS Inspector
    - AWS Guard Duty
    - AWS Cloud Trail: monitors API calls and user activity within your account
    - KMS: encryption
    - Firewalls, etc
- Self-Managed Service vs AWS-Managed Service
    - Self-Managed DB on EC2, you're responsibe for:
        - Backups
        - High Availability
        - OS upgrades
        - Service/image upgrades
        - Fault tolerance
        - Security
        - etc
    - AWS-Managed Service
        - Allows you to create an identical instance where AWS handles all of the above sub-bullets for you
- **Wherever possible, use an AWS-Managed Service**
- **Wherever possible, make use of a serverless service**
- AWS Cloud Adoption Framework
    - A set of rules/ideas critical for cloud adoption
    - Control and governance for the Cloud
- AWS Well-Architected Framework: [Framework Pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html)
    - Guidelines and best practices for AWS Cloud deployment
    - 6 Pillars (along with some examples)
        - Operational Excellence
            - Deploying infrastructure as code
        - Security
            - Apply security at all layers
        - Reliability
        - Performance Efficiency
        - Cost Optimization
        - Sustainability
- Security is like an onion
    - There are many layers
    - As you get closer to the center, the security gets tigher
    - Security should be applied thoughtfully at each layer
- NIST CSF (National Institute of Standards & Technology Cyber Security Framework)
    - Designed to be size, sector, and country agnostic
    - References globally accepted standards, guidelines, and practices
    - Organizations across the world can use it to efficiently operate in a global environment
- 3 A's of Security
    - Authentication (Who You Are)
    - Authorization (What You Can Do)
    - Accounting (Logs - What You Did)
- CIA Triad AWS Examples
    - Confidentiality: EBS encryption
    - Integrity: Cloud Trail log file validation
    - Availability: ELB
- Global Concerns:
    - AWS WAF
        - Deny (based on IP source)
        - SQL Injection prevention
        - XSS prevention
        - User-agent blocking
        - Bad bot blocking
        - Content scraper blocking
    - Amazon Route 53
        - AWS DNS
            - Route based on origin location of DNS query
                - Can block requests from certain geographic locations
            - Route to static or dynamic resources
    - Amazon CloudFront
        - AWS CDN
            - Can configure allow or block lists for different regions/countries
    - Amazon Edge locations
- All the above services under Global Concerns sit outside the VPC and falls under the customer's responsibilty; your VPC (LAN) is managed by AWS though
- In the Cloud:
    - Network ACL (Access Control List)
        - Deny or block by IP
        - Use port blocking
    - Security Groups
- Diversified Security Layers
    - Apply many layers of controls
    - Target distinct layers with distinct controls
    - Use different technologies
- It is customer's responsibility to understand what controls are available, understand what's important to their app, choose the right controls, and deploy them properly
- Only AWS contracted auditors are allowed to access AWS data centers
    - If your company has a need to audit data center for secure storage purposes, AWS gets audited every 6 months and provides artifacts and reports to facilitate downstream auditing by consumers
- AWS Trusted Advisor will scan you infrastructure and make recomendations around:
    - Cost optimization
    - Performance
    - Security
    - Fault Tolerance
    - Service limits
    - Operational excellence

## Module 2: Securing the Network

- VPC: Network architecture is your foundation
    - Good design builds in security
    - Customers have full control over their VPC
    - Stakeholder input helps develop the strategy
- Every VPC must have a CIDR range
    - Once you've created your primary CIDR, it cannot be modified
        - You can add more IP addresses, but that will overcomplicate your routing
        - It is very important to think ahead and allocate the proper number of IP addresses when creating your primary CIDR range
- **Always use a `/16` for your CIDR range (which will give you 65,000 or so IP addresses)**
- You segregate IP addresses by creating subnets
- When a subnet is created, AWS will create a NACL (firewall at subnet level)
    - Can then create a security group in the subnet around your resource to only allow inbound traffic to a specific port
- **Use subents to group the tiers of your application (for example, web/app/db within a single VPC)**
- **Avoid opening SSH or RDP for instances in production environment wherever possible**
    - Use SSM instead
- Designing a Network
    - Monitor at boundaries
    - Subet to create isolation
    - Connect through Firewalls and Load Balancers
- Inside VPC
    - Plan for unique CIDR range for each VPC
    - Use RFC 1918 addressing (class A/B/C)
    - Plan for growth ...
- Outside the VPC
    - ...
- Amazon Route 53 using DNSSEC
    - Domain Name Security Extensions (DNSSEC) helps prevent DNS attacks like DNS cache poisoning and DNS spoofing
        - Sign public hosted zones or use DNSSEC validation
        - Store private keys in AWS KMS
        - Use a single key across multiple public hosted zones
- Route 53 Resolver DNS Firewall
    - Define domain name filtering rules to control access to sites and block DNS-level threats
    - Customize the responses for blocked DNS queries
    - Filter on a domain ...
    - ...
    - ...
    - Firewall Manager
- Overall guidance
    - Layer security groups and NACLs together
    - Use multiple AZ deploymnents and ELB for high availability
    - Use out-of-band management whenever possible
        - SSM instead of SSH
    - Use Amazon CloudWatch to monitor your VPC components
    - Use flow logs to caputre information about traffic in your VPC
    - Always use IAM to limit access to your resources, including the VPC and related components
- Network filtering methods
    - Stateless
        - Focus on content in packets
        - Use info from headers
        - Generally fast and has no issue with heavy traffic loads
        - NACLs

## Stateful

- Rules in NACL apply in order
    - If Deny Any Any first and then Allow HTTPS Any, all traffic will be denied
    - If order is reversed, HTTPS will be allowed in, but other protocols like HTTP will not
- Network ACLs
    - Remember the default NACL (Allow Any Any)
    - Monitor and audit network ACLs for ineffective "Deny" rules
    - Consider limitations
    - Do not ignore outbound rules on network ACLs
- Must allow UDP for DNS
- When a subnet is created, a default Security Group is created
    - Permits all inbound traffic from members of Security Group
    - Permits all outbound traffic
- Custom Security Group
    - Permits no inbound traffic
    - Permit outbound traffic
- Security Groups Best Practices
    - Never keep unattached security groups
    - Track rate of change in production environments
    - Ensure that security groups do not have a large range of ports open
    - Use security groups with ELBs, to restrict access to the internet
    - Limit modifications to only certain IAM roles
    - Do not ignore outbound rules of security groups
- **Only ever open the REQUIRED ports**
- A good pattern for secure infrastructure is where:
    - You have a single public subnet with a load balancer
    - You have a web server in a private subnet
    - A security group allows HTTPS to public subnet and out to web server subnet
    - Another security group allows for inbound traffic to web server in private subnet from public subnet's load balancer
    - Optionally, you could move everything down and only have a NAT in the public subnet which then points to a Load Balancer in a private subnet that then forwards traffic to web server in same private subnet
- If you must utilize SSH, use a Bastion Host in a public subnet that bounces you to the desired server
- AWS Network Firewall is a managed protection service that provides:
    - Stateful firewall
    - Web filtering
    - Intrusion protection
    - Central management and visibility
    - Rule management and customization
    - Partner integrations
- For SSM usage, must allow HTTPS outbound to facilitate SSM Agent to connect with Systems Manager
    - SSM is still widely used for AWS Systems Manager, but it really stands for Simple Systems Manager which is the deprecated service that predated AWS Systems Manager
- SSM access must be granted separate from any related service permissions (i.e. If a user has Full EC2 Access, they will need SSM permissions to actually SSM into that EC2)
- Shield Response Team (SRT)
    - Shield Advanced includes the option to receive proactive support from the SRT
    - Helps mitigate risk of DDoS...

## Module 3: Amazon EC2 Security

- Common Vulnerabilities
    - Unintentionally exposing EC2 instances to the public
    - Sensitive information in metadata
    - Unused or unneeded services or software
    - Outdated or nonpatched OS or installed software
    - Application configuration weaknesses (such as startup and configuration scripts containing sensitive information)
    - Overly permissive identity and access management policies
- Hardening your Systems
    - Changing default passwords
    - Remove or disable unnecessary software
    - ...
    - ...
    - ...
    - ...
- You can access Volumes in Console and create Snapshots even if they are attached to an instance that is currently running
- The snapshot can then be used to create an Amazon Machine Image
- AMI Catalog (My AMIs section) will display the AMIs that you have created
- All snapshots are stored in an S3 bucket by default
    - When you create a snapshot, a new bucket is created to hold that snapshot
    - Snapshot buckets are hidden by default (even to `root`) so you cannot change configuration of bucket and make it publicly available
    - The only way you can access snapshot buckets is via the snapshot API
- Delete unneeded snapshots as they do cost money
- 3 Services for Securing Your Workload
    - AWS Systems Manager
    - Amazon Inspector is used for vulnerability scanning
    - AWS Config is used to alert on configuration changes
- AWS Config can detect changes to things like Security Policies that in turn set off alams that trigger emails to relevant parties
    - Provides a detailed view of the resources associated with your AWS account:
        - How they are set up
        - How they relate to each other
        - How that has changed over time
- Keys are region specific in AWS
    - The alias may be shared, but the underlying keys will be specific to the region
- Encryption by default is a best practice to ensure security of data at rest
    - Encryption by default is a region-specific settings
    - You can launch an instance only if the instance type supports Amazon EBS encryption
    - When migrating servers using AWS Server Migration Services (SMS) do not turn on encryption by default
- Key stuff
    - ...
- Management
    - Limit access and authorization for connecting to instances (Session Manager)
    - Securely manage instances at scale using the Run command
    - Regularly patch and updated with defined maintenance windows (Patch Manager)
    - Automate monitoring and remediation of configuration drift (State Manager)
    - Secure, monitor, and rotate secrets (Secrets Manager)
- Can store more secrets in Secrets Manager compared with AWS Parameter Store (although, there is a cost associated with that increased capability)
- Amazon Inspector scans:
    - EC2
    - ECR images
    - AWS Lambda functions
- Amazon Inspector integrates with AWS Organizations, AWS Security Hub, and Amazon EventBridge
- AWS Config automatically discovers and records state and configuration resources
    - Track changes (collect a historical record of changes)
    - Evaluate config
    - Automate remediation activities
    - Create real-time alerts using Amazon SNS and Amazon EventBridge
- **Enable AWS Config in all accounts and regions and record configuration changes to all resources types**
- Record global resources only in 1 region
- Amazon cerifies and provides some AMIs, community AMIs are not certified by Amazon though and they are therefore not recommended
    - If you are going to use a community AMI, test it in a non-production account first

## Module 4: Monitoring and Alerting

- VPC Flow Logs capture:
    - Packet metadata
    - Source IP
    - Destination IP
    - Address
    - Ports
    - Protocol
    - Packet size
    - Other metadata
- They cannot monitor packet contents (payload or application layer data)
- They are not real-time, they use aggregation interval for capture
- They monitor network traffic in and out of:
    - VPC
    - Subnets
    - ENI (Elastic Network Interfaces)
- They are enabled under VPCs > Select VPC > Flow Logs tab
- Traffic Mirroring for detecting network and security anomalies
    - Extract traffic of interest and route it to detection tools of your choice (like copying traffic to a Forensics box in a different subnet)
- Whether using Console, CLI, or something else, everything boils down to API calls in AWS
- Cloud Trail monitors all API calls and user activity and writes encrypted logs to an S3 bucket
- `root` can terminate AWS accounts/organizations, but admin users cannot
    - Best practice to create an admin user to use instead of `root`
- Use a dedicated S3 bucket for storage of Cloud Trail logs with MFA enabled
    - `root` user must have an MFA device set up and MFA enabled in order to enable MFA on resources like the Log S3 bucket
- Limit access to the AWSCloudTrail_FullAccess policy
    - Maybe 1 or 2 people having full access while others have just read access
- CloudTrail Lifecycle Management is configured through S3
    - Can conditionally transition to different storage tier
        - After X days, move logs to Y storage
            - Can utilze Glacier deep archive storage
- Integrate Cloud Trail with Cloud Watch
    - Monitor and alert on specific events
    - Simple searching is provided
    - Use AWS Config to ensure CloudTrail is sending events to CloudWatch Logs
        - Can fire Lambda function to reenable CloudTrail if it is ever disabled
- CloudWatch is one of the most important (if not THE) services to provide us visibility into our environment
    - It is agent-driven
    - Agents can monitor resources for various criteria and fire SNS alerts to specific parties when specific conditions are met
        - For example, if CPU utilization is 80+% for over 20 minutes, notify Ops team via email
    - CloudWatch can also fire off processes other than SNS alerts to send emails (run a lambda, for example)
- CloudWatch is Big Brother (it monitors the entire environment)
- AWS Athena is a powerful tool for analyzing and querying your log data
    - Uses SQL queries
- IoC
    - Abnormal high CPU
    - Sudden increases in db reads
    - HTML response sizes
    - Mismatched port-application traffic
    - Unusual DNS requests
    - Unusual outbound network traffic
    - Anomalies in privileged user account activity
    - Geographical irregularities (source of traffic)
    - Unusually high traffic at irregular hours
    - Multiple, repeated, or irregular login attempts
- Can use these Indicators of Compromise and use them to fire off alerts and processes to keep your system secure
    - If a privileged user has tried logging in from an unexpected country or many times or in any suspicious manner, can fire a lambda to disable that user account
- There are specific CloudWatch Alarms AWS recommends as Best Practices
    - Reference in slide deck
- Guard Duty is another great security service similar to AWS Inspector
- AWS Inspector is like someone that comes into your house and looks for possible vulnerabilities from within
- Guard Duty is like someone standing outside that is actively looking for all suspicious activity/traffic/anomalies in your environment (Intrusion detection services)
    - No agents, no sensors, no network appliances to install
    - Malware protection
    - Built-in anomaly detection with machine learning
    - Monitors up to 5,000 member accounts
    - One-click activation
- Guard Duty uses logs from VPC FLow Logs, DNS logs, Aurora, CloudTrail, KDS audit logs, S3 events, etc as data sources and uses analysis/machine learning on those logs to generate High/Medium/Low findings
- AWS customer had no changes but bill doubled; after enabling Guard Duty, they realized that an insider had installed a crypto miner, malicious files in an EC2 instance; trojans, SSH brute forcing, DNS data exfiltration were all detected automatically as well
- AWS Security Hub provides automated security checks for various standards (PCI compliance and AWS Foundational Security Best Practices, for example)
- Manual remediation is slower than automatic remediation (consider an issue that arises at 2am)
    - Manual remediation should be used to test new automatic remediations before they are put into production
- Automatic remediation prevents impact radius from growing
    - You can write simple rules to indicate events you are interested in and specify automated actions for when an event matches a rule
- Automate, automate, and automate some more!
- AWS Audit Manager continuously audits your AWS usage to simplify how you assess risk and compliance
    - Use Evidence Finder to select evidence and then generate report and it will be automatically stored in an S3 bucker
- If Block Public Access is not enabled on a bucket, it will still deny traffic by default if no policy is present
    - If a policy is configured, then certain operations will be explicitly allowed or denied

## Module 5: Course Conclusion

## Questions (to look up later)

- Why are non-relational databases (Dynamo DB) faster than relational databases?
- Does nCino utitilize:
    - AWS Trusted Advisor for our Cloud infrastructure
    - AWS Inspector for Cloud infrastructure
    - AWS Guard Duty
