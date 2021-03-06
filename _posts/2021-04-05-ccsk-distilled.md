---
layout: post
title:  "102: CCSK"
date:   2021-04-05 21:03:36 +0530
categories: Security CCSK
---
The **Cloud Security** is an essential skill for IT professionals and Certificate of Cloud Security Knowledge offers an excellent initial step. There is more to discover about CCSK from [Cloud Security Alliance](https://cloudsecurityalliance.org/education/ccsk/) who administer it. 

The following are the notes I jotted down as part of my learning towards CCSK.

# 1. Cloud concepts 

* There are a number of definitions for Cloud Computing. NIST defines it as "Cloud computing is a model for enabling ubiquitous, convenient, **on-demand network** access to a **shared pool** of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be **rapidly provisioned** and released with minimal management effort or service provider interaction".

### Essential characteristics (NIST)
- Broad Network access 
- Rapid Elasticity
- Measured service (metered)
- On-demand (self-service)
- Multitenancy (included in ISO)

### Service Models (aka "SPI")
- Software as a Service (SAAS) (Application hosted and managed by provider). Multi tenant applications. Provider is responsible for all aspects of application security (except for user management - authorisations and entitlements).
- Platform as a Service (PAAS) (Database as a service, File storage, application and development platforms). Such platforms are built on IAAS and offered to customers for consumption by APIs. Provider is responsible for the platform and the customer is responsible for everything built on the platform. Think about securing a database with firewall or user access control. 
- Infrastructure as a Service (IAAS) (Bare VMs, physical facilities and infrastructure hardware). Provider is responsible for foundational security and the customer is responsible for everything built on the infrastructure. 

### Deployment models
- Public cloud (AWS, Azure, GCP)
- Private cloud (sorely operated for a single organisation, managed by a third-party perhaps)
- Community cloud (Gov cloud)
- Hybrid cloud (infrastructure composed of two or more clouds e.g. private/public)

### Logical model
- Infrastructure - Core building blocks of the computer system (e.g. compute, storage, networks) (Protected by Infrasturcture security)
- Metastructure - Interface between infrastructure and other layers (e.g. **cloud management plane**). 
- Infostructure - Data and information. (Protected by Data Security)
- Applistructure - Applications deployed and underlying application services used to build them (e.g. message queues, AI, notification systems) (Protected by Application Security)

### Key notes
- Techniques used to create clouds are abstraction and orchestration. Cloud abstract the resources from the underlying physical infrastructure to create pools and use orchestration to carve out and deliver set resources from pools.  
- Note that traditional virtualisation abstracts the underlying resources but lacks orchestration to pool them. It is a manual process but in the clouds it is automated. 
- The **cloud management plane** offers a web interface to manage cloud resources (e.g. launch instances, configure virtual networks)
- Protection of the cloud management plane is top priority when designing a cloud security program. If an attacker managed to gain access to the cloud management plane, then the whole infrastructure is at risk of compromise.
- The metastructure is the key difference between traditional IT and Cloud. Think self-service/on-demand too. 
- Providers manage the physical infrastructure while the customer *manage portions* of the virtual infrastructure. So it is a shared responsibility.
- Shared responsibility model. There must be a clear responsibility matrix that describes who is implementing which control from a security perspective. 
- **Consensus Assessment Initiative Questionnaire (CAIQ)** - standard documentation for providers to document their security and compliance controls.
- **Cloud Controls Matrix (CCM)** - sists cloud security controls that maps to various security and compliance standards. 
- **Cloud Security Models** are tools to help guide security decisions.
- **Reference architectures** are templates for implementing cloud security.
- The first step of implementing a cloud security process model is to identify necessary requirements. 

# 2. Governance and Enterprise risk management

### Governance
- Composed of
  - Policy
  - Process
  - Internal controls 
- Determines how an organisation is run.

### Enterprise risk management
- Management of overall risk of the organisation that is aligned to the governance and risk tolerance. 
- Information risk management - Management of risk of information (includes IT). Information is one of the assets of the organisation.
- Information security - Tools and practices to manage risk to information.
- Primary _role_ of Information security is to **provide processes** and **controls** to protect electronic information and the systems used to access it. 
- Primary _goal_ of Information security is to protect the fundamental data that power systems and applications. 
- Governance --> Enterprise risk management --> Information risk management --> Information security
- Risk tolerance is the amount of risk that the leadership and stakeholders of an organisation are willing to accept. 
- Moving to the cloud _does not change the risk tolerance_ but changes how risk is managed. 

### Key notes
- Cloud computing impacts governance as it introduces a third-party into the process.
- Remember: **an organisation can never outsource the responsibility of governance**.
- Responsibilities and mechanisms for governance are defined in contract with the provider. 
- Customers have to address any governance gap if there is an area that is not covered in the contract. Customers are expected to adjust their own processes to close this gap.

### Tools for governance
- Contract - Primary tool/relationship document between customer and provider. 
- Supplier assessments - Performed by customer using available information. (manual research, third-party attestations - **legal statement used to communicate the result of an assessment or audit**).
- Compliance reporting - Providers internal and external compliance assessments.
- CSA STAR Registry is an assurance program and documentation registry for cloud provider assessments based on CCM and CAIQ.

### Service and deployment model
- SAAS requires the most need for a negotiated contract.
- PAAS likelihood of a fully negotiated contract is low.
- IAAS is closer to traditional data centres and existing governance and risk management activities are transferable. 
- In the public cloud, ability to govern the operation is very low because the provider is responsible for it. 
- Appreciate that there is no room for adjusted contracts as everything runs on one set of resources. 

### Cloud risk management trade-offs
- Less physical control 
- Greater reliance on contracts, audits and assessments
- Management of relationship
- Reduced need to manage risk as providers will manage some under **shared responsibility models**.

### Tenets of risk management
- Manage
- Transfer
- Accept
- Avoid
- Cloud risk management requires 
  1. Acquire documentation
  2. Review provider security program
  3. Review legal, regulatory and contractual and jurisdictional requirements
  4. Evaluate contracted services
  5. Evaluate provider (finance, stability etc)
- Periodically review audits and assessments (scheduled or automated)
- Residual risk - what is left after managing risk may be able to manage through controls (e.g encryption). Options are above (transfer/accept/avoid). 
- Risk transfer is enabled by insurance.

# 3. Legal, contracts and electronic discovery
- Legal frameworks
  - Data controller - has the relationship with the user
  - Data processor - process data behalf of the data controller
  - Data owner - Also the data subject, the customer who owns the data (you and me)
  - Data controller must ensure the data processor has adequate controls and safeguards. 
  - What legal frameworks used depends on each country.
- Security of personal data is essential for an individual's privacy.
- Data importer and exporter may need to sign a contract to ensure maintainance of privacy rights of users. 
- Privacy laws
  - Australia (Privacy Act, Consumer Law)- Require notification in case of a breach that may cause serious harm. 
  - China - Cyber Security law
  - Japan - APPI limits transfer of personal data to third-parties. 
  - Russia - Data localisation law - requires storage of citizen information within its borders. 
  - EU/EEA - GDPR applies when processing data of EU citizens. Establishment of controller or processor in EU/EEA. Data subjects given explicit consent to process data. Applies when data of EU/EEA citizens are processed anywhere. Privacy by design/default for applications. Data breach must be reported within 72 hours.
- NIS directive - applies **Digital Service Providers (DSP)** to protection of networks and information systems in EU/EEA. Security requirements for essential services. Appies to providers who offer services in EU/EEA who are based outside EEA is in scope.
- Data custodian - similar to the data controller, must ensure security and protection of personal data especially when transferring to a third-party.
- Customers are expected to have a written contract with the provider with reasonable security measures. 
- The FTC and State attorneys general in the USA are able to conduct enforcement actions against companies whose privacy practices are inconsistent with claims made in public disclosures. 
- Data must be used only for the purposes for which it was collected.
- Always look for adequate protection when data is being transferred across borders. 
- Periodic monitoring, testing and evaluation of cloud services are required as they evolve and need to ensure the control efficacy.
- Note that third-party audits and attestations are used by customers to build their own compliance systems. Therefore it is important to understand the scope of these audits and attestation to ensure its applicability.  
- Due diligence may include
  - Quality of service
  - Stability of service
  - Completeness of service
  - Applicable service level (e.g. 99.5%)
  - Security disclosures
  - Price of service
  - Proof of compliance with applicable legal requirements
  - Availability of certain level of support
  - Responsiveness of customer service
  - Speed of network 
  - Location of data centres
  - Also interview customers to obtain insight
  - Review reports of litigation
  - Online searches to evaluate vendor reputation

### Electronic discovery
- The process in which an opposing party obtains private documents for use in litigation. Admissible in court. Admissible evidence means *applicable and relevant*. 
- Hosting data in a cloud platform does not oblivate the obligation to produce information. Therefore important to understand what data is not available to the client from the outset. 
- If the application platform or environment is at fault or relevant to the investigation, then the request has to be raised with the provider itself. 
- Some e-discovery tools used in traditional infrastructure may not be usable/applicable in the cloud. This means extra time and monetory impact expected to be considered and perhaps included in the contract. 
- Litigation hold - Using reasonable steps to prevent the destruction of information in possession that may be used for a pending litigation. 
- Data may need to be retained for legal reasons which means storage and cost must be considered. (large amount of data for an extended period).
- Scope of preservation - Party may need to retain data that is reasonable for the litigation but client may over-preserve if granular preservation is not supported.
- Data collection (Electronically Stored Information "**ESI**")
  - Data collection can be hard as customers may not have the required access.
  - Access and bandwidth costs - Prevents collection of large amounts of data quickly. Establish a protocol to handle this.
  - Bit by bit image - Not generally possible due to multitenancy. Usually mandated due to resource pooling. 
  - No direct access - IT equipment seizures for the purpose of evidence preservation.
  - Standard formats (e.g. PDF) - Favour this over proprietary unless some evidence is lost during conversion. 
  - Storing data in the cloud does not prevent its being used as evidence. Should not be considered more or less admissible or credible merely because they were created or stored in the cloud.
  - Discovery by design - data in the cloud is available during e-discovery. 
  - [Sedona Conference](https://thesedonaconference.org/) - Recommendations for handling ESI. (non-profit organisation)
 
 # 4. Compliance and audit management
 - Compliance audit and assurance should be continuous.
 ### Governance, Risk and Compliance (GRC)
  - Compliance management is a tool of governance, it is how an organisation proves it is meeting internal and external obligations. 
  - Information security is coupled with compliance.
  - Customer is ultimately responsible for their compliance.
  - Customers have to depend on third-party attestations of providers to understand their compliance and alignment/gaps.
  - Pass-through audit - form of compliance inheritance. Providers services including infrastructure have gone through an audit to a compliance standard. Provider maintains their compliance.
  - Customers must understand where their data and services are.
  - Note that not all services are audits against all compliance regimes, customers must make sure they use vetted services to build their compliant solution.

### Audits
- Audit and assessments are mechanisms to document compliance with internal and external requirements. It is expected to include compliance determination (what is the outcome). 
- Audit management includes management of all activities related to audits and assessments.
  - Determines requirements
  - Scope
  - Scheduling
  - Responsibilities
- Customers may need to sign NDA before gaining access to attestations from providers.
- Attestations and certifications are point in time activities. 
- Audit artifacts are:
  - Logs
  - Documentation
  - Materials needed for audits and compliance
  - System configuration details
  - Activity reporting
  - Change management details

- Attestation is a legal statement from a third-party which describes their statement of audit findings. 
- CSA CCM can be used to maintain requirements and current status.

# 5. Information governance
- Information is data with value.
- Ensures that data and information complies with organisational policies, standards and strategy including regulatory, contractual and business objectives. 
- Determines how data is handled in accordance with goals and requirements. 
- By hosting data in the cloud, a third-party is introduced to the governance model. 

### Things that impact 
- Multitenancy - Data is stored in shared infrastructure.
- Shared responsibility model - customer and provider responsibilities
  - Data ownership - who owns the data. Defines rules how data is managed.
  - Custodianship - who is managing the data. Implements the rules.
- Information classification 
- Information management policies - what is allowed to go and where in the cloud?
- Location and jurisdictions -legal requirements are hard lines.
- Authorisations
- Privacy - sum of regulatory, contractual and commitments to customer
- Contractual - legal tool for extending governance to cloud
- Security controls - tools to implement data governance

### Data security lifecycle
- Describes the phases information passes through but does not address its location or how it is accessed.
- Information lifecycle does not map well to the needs of security professionals.
- Data security lifecycle maps to needs of the security audience.
- Phases (things that can be done (functions) to data are **Read**, **Process** and **Store**). Access is controlled by entitlements.
  - Create - Note that updating data creates new data.
  - Store
  - Use
  - Share
  - Archive
  - Destroy

# 6. Management plane and business continuity (BC)
- Management plane is the interface to connect to metastructure and configure the cloud. Part of Broad network access, metered service (self-service).
- Metastructure is used to create resources using resource pools (note in cloud resources are pooled).
- Provider is responsible for ensuring the management plane is secure.
- Customer is responsible for configuring its use. Include securing and managing credentials.
- Ensure strong perimeter security for API gateways and web consoles.

### Consideration for BC/DR
- Continuity and recovery within the provider itself (less multi-cloud)
- BC/DR is shared responsibility too
- Must account for entire logical stack
- Prepare for provider outage.
- Seek/consider options for portability (Containers)
- Architect for failure
- Use multi-zone deployments to address high availability
- Keep a note that a single resource is less resilient in the cloud than in private due to fragility of virtualised resources running in complex environments.
- Life and shift to cloud without architectural changes can reduce resiliency.
- Design for RTO and RPO in traditional environments.
- Take a risk based approach.

### Preparation for DR
- Metastructure - Backup configuration (IaC)
- Software defined infrastructure - Template where possible
- Any custom images are available in right regions
- Infostructure - data synchonisation
- Applistructure - message queues and code is available, PAAS limitations (don't forget key management services)
- Real-time failover may not be possible - design apps and RPO appropriately.
- SAAS providers have the biggest outage concern. Extracting data periodically might be the only way.
- Data residency is a key factor.

### Interaction with cloud
- Usually through APIs which are REST, CLI and SDKs.
- Uses variety of authentication mechanisms (e.g. OAuth, Federation)
- Identity and Access management (IAM) used to manage access to the management console. 
- RBAC allows super or low-level administrative roles/permissions. 
- All privilege accounts must use multi-factor (MFA). Most effective security control to prevent wide range of attacks.

# 7. Infrastructure security
- Foundation for operating securely in the cloud. Lowest layer of security from a customers perspective.
- Macro-layers
  - Fundamental resources that pooled together to create a cloud. (raw compute, networks and storage)
  - Virtual abstracted infrastructure
- Networks in cloud (they are separate physical networks)
  - Management network - traffic from management plane
  - Storage network - connects virtual storage to virtual machines
  - Service network - communication between virtual networks. Build the network resource pool for customers.
- Network virtualisations
  - Virtual Local Area Networks (VLANs) - Designed for single tenant networks (separate different departments/business units). Not suitable for cloud-scale networks.
  - Software defined networking (SDN) - Complete abstraction over physical networks. Offers higher flexibility and isolation. Security isolation boundary. Uses packet encapsulation to move packets around the network and virtual machines are unaware instead they connect using a standard networking interface. 
- Note that the customer loses the direct management of the underlying physical network. 
- Normal practice of inserting appliances between communication paths is not always possible as networking is virtualised.
- Customers expected to use in-line virtual appliances or software agents for security. 
  - Virtual appliances can become bottlenecks as they cannot fail-open (all traffic must be intercepted).
  - Cost of resources to meet network requirements
  - Virtual appliance is expected to auto-scale to match elasticity (metered service and rapid provisioning)
  - Keep up with velocity of changes in the virtual network.
  - Virtual IP assignments change frequently, therefore traffic is expected to be identified by unique ID than IP. This could impact alerting and monitoring. Dynamic environment. 

### SDN benefits
- Ability to build many virtual networks without the constraints imposed by physical hardware. No more address conflicts as each network is isolated (two networks with the same CIDR blocks is possible). Think micro-segmentation.
- SDN firewalls (security groups) - Defines a set of policies (egress and ingress traffic rules).
  - Ability to assign security groups based on tags. 
  - Default deny
  - Granular rules
  - Allows application between hosts as they are (security groups) managed outside of hosts.
  - Isolation of each virtual machine is possible without any additional hardware costs.
  - Many network attacks are eliminated by default compared to physical networks.
  - Packet encryption is possible.
- Host firewalls
  - Difficult manage at scale
  - If a system is compromised, then easy to alter the host firewall too.
- Microsegmentation (hypersegmentation) - using virtual networks to run smaller isolated networks.
  - Option was not available previously because of cost.
  - Reduce blast radius. (maintains segregation and isolation)
  - Lateral movement is difficult 
  - Increase operational cost
  - Greater flexibility and security for evolving network topologies
  - Note that providers are responsible for perimeter security
  - Implement cloud firewalls **per-workflow** instead of per-network basis.
- Hybrid connections may reduce the security of cloud networks (hybrid - between private to public cloud)
- **Bastion** or **transit** networks are an emerging standard
- Compute abstractions
  - Virtual machines - host level isolation offered. 
  - Containers - code execution isolation, shares resources from the operating system. Runs segregated processes. Container configuration provides capabilities available for the container. Process isolation technique.
  - Platform-based workloads - running solutions on shared PAAS (e.g. procedures on a database platform).
  - Serverless computing - executes application code directly. Provider manages all the underlying layers including foundation security.
- Immutable workloads
  - No longer make any changes to the running workflow (no image change). Update the underlying image and redeploy replacing the old. There is a degree of immutability (e.g. centralised configuration management pushing changes to instances).
  - Enable stronger security - no remote login, file integrity monitoring
  - Reduced vulnerability scanning on running workloads.
  - Consistent image creation process is required (automation to update deployments)
  - Security testing integrated into imagine building process
- Impact on standard workloads
  - No agents on non-VM based workloads
  - Traditional agents may impede performance
  - Agents expected to be cloud-ready (some agents may be unaware of running environment or auto-scaling)
  - Agents might require additional ports to be opened.
  - IP addresses are dynamically assigned to multiple systems in a short duration (elastic)
  - Logs should be collected externally due to high velocity of change.
  - Logging architecture has to account for cloud storage and cost
- Vulnerability assessment
  - Require notification of asssessments (pen testing)
  - Default deny will prevent assessments (require opening up ports)
  - Assessments may be able to run during image creation
 
# 8. Virtualisation and containers
- Key building block (categories)
  - Compute
  - Network
  - Storage
  - Containers
- Virtualisation is essential for cloud and adds two further layers of security
  - Security of virtualisation technology
  - Security controls for virtual assets
- Providers responsible for physical and virtualisation platform
- Customer is responsible for available virtual security controls and understanding risks. 
  - When to encrypt cloud storage
  - When to configure virtual firewalls
  - When to use dedicated or shared hosts  
- Provider must assure **isolation** and **virtualisation infrastructure**. Virtualisation of cloud users so that volatile memory security is secured from each tenant (referring back to isolation concept). 
- Customers must implement security for the workload.
  - Secure cloud management portal
  - Monitor and logging
  - Image asset management
  - Dedicated hosting where appropriate
  - Responsible for security within virtualised resources

### Networks
 - Route traffic to a virtual network monitoring or filter so that communication between VMs in a same physical host can be monitored. Or bridge network traffic back out to the network via a virtual appliance on the same network. Note that both will create bottle-necks and less-efficient routing.
 - Provider is expected to disable packet sniffing and metadata leaks that could expose configuration between tenants. Neither tagging nor SDN-level metadata.
 - 
### Storage
- Achieved through Storage Area Networks (SAN) and Network Attached Storage (NAS).
- Data is replicated across different locations (encrypted)
- 
### Containers
- Isolated user pace but shared kernel space
- Offers task segregation over full security isolation
- Three components
  - Execution environment
  - Orchestration and scheduling
  - Repository for container images
- Providers responsibility to secure physical infrastructure - given
- Secure orchestrator management plane
- Secure image repository
- Tasks with the same security context can sit together in the same virtual or physical host

# 9. Incident response
- Usually part of the information security program.
- Access to forensic data and governance is different in cloud

### Incident response lifecycle
- Preparaion for IR is the key.
- Stages
  - Preparation - Setup IR capability in the organisation
  - Detection and analysis - Alerting, scope of the incident, use platform logs, SAAS is difficult. Data sources are quite different; feed off management plane when data is not available. Limited network visibility. Usually network logs from providers tend to be flow logs not full packet capture. Instrumentation when provider logs are not available. Validate whether provider logs meet chain of custody requirements. Greater need to automate forensic due to the dynamic nature of the cloud.
  - Containment and eradication - Take systems offline, data loss vs service availability, chain of custody. Break-glass procedure to use root master credentials to ensure full visibility (as security trimming might make some log not accessible or visible). SDN helps to build a clean environment and isolate attacks (think micro-segmentation) using virtual firewalls. No need to immediately eradicate attackers, instead isolate using virtual firewalls. With SAAS and PAAS quite hard since there is no access to VMs.
  - Post-mortem - What could be done? could we have detected early, if so how?. Understand data limitations and see for improvements.
- All stages/phases of IR are impacted by the cloud.
  - SLAs and governance - Understand these and require coordination with the provider.
- Built security into the code that runs in the container
- Need to know what data and logs are available for investigation
- **Cloud jump kit** - Tools needed to investigate in a remote location
- Architect for faster detection (containment and recoverability)
- Things to help investigation
  - Enable instrumentation
  - Utilise isolation
  - Use immutable servers
  - Implement application stack map
  - Threat modeling and tabletop exercise
- Testing of IR expected to be carried out annually or after a significant change.

# 10. Application security
- Early designs for maintaining and defending production applications.
- Higher baseline security - offered by providers as they need to maintain standards and compliance to regulations.
- Responsiveness - automation via APIs.
- Isolated environments - hyper-segregation
- Elasticity - greater use of immutable infrastructure
- Automation through DevOps.
- Management plane security is important too
- Areas
  - Secure software development lifecycle (SSDL)- from design to deployment
  - Design and architecture - trends in designing applications in cloud
  - DevOps - CI/CD in development environment
  - Secure design and development - training and development organisation-wide standards
  - Secure deployment - security and testing activities
  - Secure operations - securing and maintaining applications
- Cloud impact every phase of SSDL
- Metastructure and management plane security is part of application security
- Phases
  - Training - Secure coding, Security tests
  - Define - Code standards, Security functional requirements
  - Design - **Threat modeling**, secure design
  - Develop - Code review, unit testing, static and dynamic analysis
  - Test - Vulnerability assessments, QA, functional tests and dynamic analysis
- Deployment
  - Code review - manual activity
  - Unit, regression and functional testing - addition of new security testing
  - Static application security testing - checks for embedded credentials (never do this)
  - Dynamic application security testing - tests running applications (web vulnerability, fuzzing)
- Vulnerability assessments can be integrated into CI/CD. 
  - Running assessments against images/containers
  - Test the entire infrastructure in the test environment and test it (as infrastructure as code). 
  - Host based vulnerability assessments - no permission from provider required
- Pen testing
  - Testing firms that has experience in the cloud provider
  - Include developers and administrators
  - Test for tenancy isolation by providing access as a tenant to the system.
- CI expected to include
  - Functional tests
  - Non-functional tests
  - Security tests
- Design and architecture
  - **Segregation by default** - applications runs on isolated environments
  - Immutable infrastructure - disable remote logins, file integrity monitoring (FIM)
  - Use of microservices - auto-scaling groups for scalability/elasticity
  - Serverless - running workflow on providers platform. 
  - Software defined security and event driven security

# 11. Data security and encryption
- Enforcement tool for information and data governance. Risk based.
- Controls
  - Controlling what goes into the cloud
  - Access control, encryption, architecture, monitoring/alerting, DLP and rights management
  - Enforcing information lifecycle management - location/residency
  - Compliance including audits
  - Backups and business continuity
  - Use CASB to monitor data flowing into SAAS.
- Storage types (data dispersion/fragmentation of bit splitting to chunk/break up data to store in multiple places for higher availability/durability). Physically dispersed.
  - Object store - typically files
  - Volume store - virtual hard-disks for VMs
  - Databases
- Other factors
  - Identify key data repositories (database and file activity monitoring). Detection of large data transfers.
  - Monitor cloud usage (Cloud Access and Security Broker - CASB, identification of cloud service usage by network, integration with network gateways or DNS queries. Offers DLP controls too. URL filtering - helps determine which services are being used.)
  - Application/platform - CDNs, caching
- Securing transfers
  - Client side encryption - data is encrypted before sending
  - Transport layer encryption
  - Proxy encryption - encryption whilst be migrated
  - Remember - access control and encryption is building blocks of data security
- Three levels of access control
  - Management plane - directly accessing the cloud management console
  - Public and internal sharing controls
  - Application level controls - design and implementation of application specific controls  
- Entitlement matrix - defines which users, groups and roles should have access to which resources and functions. Make sure to validate your controls frequently (ideally continuously).
- Encryption and tokenisation
  - Key management is as important as encryption. (**Data** --> **encryption engine** --> **key management**)
  - Encryption and decryption (plain text --> ciphertext)
  - Tokenisation replaces data with random value - Used when format of the data is important
- Volume storage encryption - Instance and externally managed encryption. Model depends on where the key is managed (instance itself or external system but issued to instance on-demand)
- Object and file storage - Client-side (keys managed by client) and server-side encryption (after data is transferred in, the provider has access to the keys). Proxy encryption where a proxy handles crypto operations. 
- SAAS recommended to use per-customer keys where possible to enforce multi-tenancy isolation. 
- Considerations for key management
  - Performance
  - Accessibility
  - Latency
  - Security
- Key management options
  - HSM - Hardware security module
  - Virtual appliance - software based key manager
  - Provider offered - Key management service offered by the provider
  - Hybrid - Combination of HSM and Virtual
- Customer managed keys - Customer manages the keys whereas provider offers the encryption engine. 
- Key management and data storage systems should be separate. 
- Consider air-gap between systems (e.g. use provider based messaging or object storage so that attacker must compromise cloud systems to gain access)
- Data segregation between test and production is important. 

# 12. Identity, entitlement and access management (aka Identity management IdM)
- Both provider and customer are responsible for this.
- Maps and **entity** to an identity. Entity could be a userm system, device or code. Identity is an unique expression of an entity within a namespace.
- Then makes decisions on what this identity can do using various attributes. 
- Federation is used for map single identity to multiple services. This is achieved by building trust relationships between organisations and using standard protocols for integration. *Federation at scale*.
- Identifier - means by which an identity can be asserted.
- Authentication (AuthN) - process of confirming identity
- Authorisation (AuthZ) - allowing identity to access something. Permission to do something. 
- Federated identity management - process of asserting identity across different systems (think single signon).
- SAML - for authentication and authorisation - federation 
- OAuth - authorisation (widely used for web services) - delegating access control/authorisation between services.
- OpenId - standard for federated authentication. 
- XACML - standard for **attribute** based access controls and authorisations. 
- SCIM - standard for exchanging identity information between domains. (for provisioning and deprovisioning accounts in external systems)
- HTTP request signing - authenticating to REST APIs.
- Federation is good, but there might be accounts created only in the cloud for break-glass scenarios (or backup operators, accounts to help debug federation).
- Identity broker - hub and spoke identity. Internal identity provider communicates with a central broker which federates identity to other systems (federation between identity providers and relying parties). 
- MFA offers the strongest option for reducing account takeovers. 
  - Hard tokens - generated by hardware devices
  - Soft tokens - generated by application, risk of device compromise.
  - Out-of-band passwords - SMS 
  - Biometrics - readers installed in mobile devices itself.
- Attribute-based access control (ABAC) - greater flexibility, Multiple factors (role, location, authentication mode) are used for authorisation. 
- Privileged identity should use MFA. 

# 13. Security as a service 
- Service delivered as a cloud service - meets all the properties of cloud.
- Make sure to validate data retention needs with the provider.
- Benefits
  - Cloud computing service - scale, elasticity, cost etc
  - Expertise - provider offered staff and capabilities
  - Intelligent sharing - as provider maybe serving multiple customers 
  - Deployment flexibility 
  - Insulation of clients - provider intercept attacks
- Concerns
  - Lack of visibility 
  - Regulation difference
  - Handling of regulated data - are data that is captured as part of security inspection are handled appropriately.
  - Potential lock-in
- Available services
  - Federated brokers
  - CASB - cloud security gateways (detect, assess and potentially block)
  - Web security - anti-malware, secure browsing
  - Email security - security for inbound and outbound, phishing and malicious attacks
  - WAF
  - SIEM - Security Information and Event Management - aggreate log events
  - Encryption and key management
- Security assessments
  - Traditional security/vulnerability assessments (for assets deployed in the cloud)
  - Application security assessments (traffic inspection, and anti-DDOS)
  - IPS/IDS - rule bases, heuristics and behaviour models
  - Cloud assessment tools (to checks cloud configuration)

# 14. Related technologies
- Technologies seen in cloud
  - Big data - extremely large datasets - **high volume**, **high velocity** /or **high variety**.
  - Internet of Things (IoT) 
  - Mobile devices 
  - Serverless computing
- Big data
  - Data collection - ingestion, different tools and platforms is a concern for security and privacy.
  - Data storage - ability to store large datasets
  - Processing - distributed processing, tools capable of distributing processing jobs.
  - Encryption should be used in **primary**, **intermediary** and **backup** storage (collection and storage pipelines)
- Internet of Things (IoT)
   - Used for tracking purposes
   - Connected healthcare and lifestyle applications
   - Data collection and sanitisation
   - Device registration, authentication and authorisation (**stored credentials** is an issue).
   - Weak encryption protocols
   - Ability to patch devices in the field
- Mobile
  - Device registration, authentication and authorisation
  - Data stored in the device should be protected too
  - Certificate pinning and validation within the device to overcome connectivity security.
- Serverless computing
  - Servers and their configuration is hidden away from customers hence serverless
  - Examples: Object storage, cloud load balancers, cloud databases, machine learning, message queues
  - Higher security burden on provider
  - Lack of visibility and network logs
  - High use of cloud management console
  - Reduced opportunity for security testing as the code is hosted in provider infrastructure
  
# 15. Cloud Control Matrix (CCM) and Consensus Assessment Initiative Questionnaire (CAIQ)
- CCM - a list of controls and guidances that map to standards such as PCI, ISO. It can be used as a tool for the systematic assessment of a cloud implementation, and provides guidance on which security controls should be implemented by which actor within the cloud supply chain.
- CAIQ - list of questions that document what security controls exists in IAAS, PAAS and SAAS by providers. 
- STAR registry - a collection of questionnaires completed by providers that demonstrate their security posture. Essentially answers to CCM and CAIQ. [Registry](https://cloudsecurityalliance.org/star/registry/)
