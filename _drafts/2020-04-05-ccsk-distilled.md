---
layout: post
title:  "CSSL distilled"
date:   2019-03-23 21:03:36 +0530
categories: Security CCSK
---
The Cloud Security is an essential skills for IT professionals and Certificate of Cloud Security Knowledge offers an excellent initial step. There is more to discover about CCSK from [Cloud Security Alliance](https://cloudsecurityalliance.org/education/ccsk/) who administer it. 

This goal of this post is to summarise the key knowledge expected by CCSK if you are thinking of taking the exam.

# 1. Cloud concepts 

* There are number of definitions for Cloud Computing. NIST defines it as "Cloud computing is a model for enabling ubiquitous, convenient, **on-demand network** access to a **shared pool** of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be **rapidly provisioned** and released with minimal management effort or service provider interaction".

### Essential characteristics (NIST)
- Broad Network access 
- Rapid Elasticity
- Measured service (metered)
- On-demand (self-service)
- Multitenancy (included in ISO)

### Service Models (Sometimes called "SPI")
- Software as a Service (SAAS) (Application hosted and mananged by provider). Multitenant applications. Provider is responsible for all aspect of application security (except for user management - authorisations and entitlements).
- Platform as a Service (PAAS) (Database as a service, File storage, application and development platforms). Such platforms are built on IAAS and offered to customers for consumption by APIs. Provider is responsible for platform and customer is responsible for everythin built on the platform. Think about securing a database with firewall or user access control. 
- Infrasturcture as a Service (IAAS) (Bare VMs, physical facilities and infrastructure hardware). Provider is responsible for foundational security and customer is responsible for everything built on the infrastructure. 

### Deployment models
- Public cloud (AWS, Azure, GCP)
- Private cloud (sorely operated for a single organisation, managed by a third-party perhaps)
- Community cloud (Gov cloud)
- Hybrid cloud (infrastructure composed of two or more clouds e.g. private/public)

### Logical model
- Infrastructure - Core building blocks of the computer system (e.g. compute, storage, networks) (Protection by Infrasturcture security)
- Metastructure - Interface between infrastructure and other layers (e.g. **cloud management plane**). 
- Infostructure - Data and information. (Protection by Data Security)
- Applistructure - Applications deployed and underlying application services used to build them (e.g. message queues, AI, notification systems) (Protection by Application Security)

### Key notes
- Techniques used to create cloud are abstraction and orchestration. Cloud abstract the resources from the underlying phyiscal infrastructure to create pools and use orchestration to carve out and deliver set of resources from pools.  
- Note that traditional virtualisation abstracts the underlying resources but lacks orchestration to pool them. It is a manual process but in cloud it is automated. 
- The **cloud management plane** offers a web interface to manage cloud resources (e.g. launch instances, configure virtual networks)
- Protection of the cloud management plane is top priority when designing a cloud security program. If an attacker managed to gain access to the cloud management plane, then the whole infrastructure is at risk of compromise.
- The metastructure is the key difference between traditional IT and Cloud. Think self-service/on-demand. 
- Provider manage the physical infrastructure while customer manage portion of the virtual infrastructure.
- Shared responsibility model. There must be clear responsibility matrix that describe who is implementing which control from security perspective. 
- **Concensus Assessment Initiative Questionnaire (CAIQ)** - Standard documentation for providers to document their security and compliance controls.
- **Cloud Controls Matrix (CCM)** - Lists cloud security controls that maps to various security and compliance standards. 
- **Cloud Security Models** are tools to help guide security decisions.
- **Reference architectures** are templates for implementin cloud security.
- The first step of implementing a cloud security process model is to identify necessary requirements. 

# 2. Governance and Enterprise risk management

### Governance
- Policy
- Process
- internal controls 
determine how an organisation is run.

### Enterprise risk management
- Management of overall risk of the organisation that is aligned to the governance and risk tolerance. 
- Information risk management - Management of risk of information (includes IT). Information is one of the assets of the organisation.
- Information security - Tools and practices to manage risk to information.
- Primary role of Information security is to **provide processes** and **controls** to protect electronic information and the systems use to access it. 
- Primary goal of Information security is to protect the fundamental data that power systems and applications. 
- Governance --> Enterprise risk management --> Information risk management --> Information security
- Risk tolerance is the amount of risk that the leadership and stakeholders of an organisation are willing to accept. 
- Moving to the cloud does not change the risk tolerance but changes how risk is managed. 

### Key notes
- Cloud computing impacts goverance as it introduce a third-party into the process.
- Remember: **an organisation can never outsource the responsibility of governance**.
- Responsibilities and mechanisms for governance are defined in contract with the provider. 
- Customer has to address any governance gap is there is an area that is not covered in the contract. Customer is expected to adjust their own processes to close this gap.

### Tools for governance
- Contract - Primary tool/relationship document between customer and provider. 
- Supplier assessments - Performed by customer using available information. (manual research, third-party attestations - **legal statement used to communicate result of an assessment or audit**).
- Compliance reporting - Providers internal and external compliance assessments.
- CSA STAR Registry is an assurance program and documentation registry for cloud provider assessments based on CCM and CAIQ.

### Service and deployment model
- SAAS require the most need for a negotiated contract.
- PAAS Likelihood of a fully negotiated contract is low.
- IAAS is closer to traditional data centre and existing governance and risj management activities are transferable. 
- In public cloud, ability to govern the operation is very low because provider is responsible for it. 
- There is no room adjusted contracts as everything runs on one set of resources. 

### Cloud risk management trade-offs
- Less physical control 
- Greater reliance on contracts. audits and assessments
- Management of relationship
- Reduced need to manage risk as provider will manage some under shared responsibility model.

### Tenents of risk management
- Manage
- Transfer
- Accept
- Avoid
- Cloud risk management requires 
  1. Acquire documentation
  2. Review provider security program
  3. Review legal, regulatory and contractual and jurisdictional requirements
  4. Evaludate contracted services
  5. Evaluate provider (finance, stability etc)
- Periodically review audits and assessments (scheduled or automated)
- Residual risk - what is left after managing risk maybe able to manage through controls (e.g encryption).Options are above (transfer/accept/avoid). 
- Risk transfer is enabled by insurance.

# 3. Legal, contracts and electronic discovery
- Legal frameworks
  - Data controller - has the relationship with the user
  - Data processor - proces data behalf of the data controller
  - Data owner - Also the data subject, the customer who owns the data (you and me)
  - Data controller must ensure the data processor has adequate controls and safe guards. 
  - What legal frameworks used depends on each country.
- Security of personal data is essential for individual's privacy.
- Data importer and exporter may need to sign a contract to ensure maintainance of privacy rights of users. 
- Privacy laws
  - Australia (Privacy Act, Consumer Law)- Require notification in case of a breach that may cause serious harm. 
  - China - Cyber Security law
  - Japan - APPI limits transfer of personal data to third-parties. 
  - Russia - Data localisation law - require storage of citizen information within its borders. 
  - EU/EEA - GDPR applies when processing data of EU citizens. Establishment of controller or processor in EU/EEA. Data subjects given explicit concent to process data. Applies when data of EU/EEA citizens are processed anywhere. Privacy by design/default for applications. Data breach must be reported with 72 hours.
- NIS directive - applies **Digital Service Providers (DSP)** to protection of networks and information systems in EU/EEA. Security requirements for essential services. Appies to providers who offer services in EU/EEA who are based outside EEA is in scope.
- Data custodian - Similar to data controller must ensure security and protection of personal data especially when transferring to a third-party.
- Customer is expected to have a written contract with the provider with resonable security measures. 
- The FTC and State attorneys general in USA are able to conduct enforcement actions against companies whose privacy practices are inconsistent with claims made in public disclosures. 
- Data must be used only for the purposes for which it was collected.
- Always look for adequate protection when data is being transferred across borders. 
- Periodic monitoring, testin and evaluation of cloud services are required as they evolve and need to ensure the control efficacy.
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
- The process which an opposing party obtain private documents for use in litigation. Admissible in court. Admissible evidence means applicable and relevant. 
- Hosting data in a cloud platform does not oblivate the obligation to produce information. Therefore important to understand what data is not available to the client from the outset. 
- If the application platform or environment is at fault or relevant to the investigation, then the request has to be raised with the provider itself. 
- Some e-discovery tools used in traditional infrastructure may not be usable/applicable in the cloud. This means extra time and monitory impact expected to be considered and perhaps included in the contract. 
- Litigation hold - Using resonable steps to prevent the distruction of information in possesion that maybe used for a pending litigation. 
- Data may need to be retained for legal reasons which means storage and cost must be considered. (Large amount of data for an extended period).
- Scope of preservation - Party may need to retain data that is resonable for the litigation but client may over-preserve if granular preservation is not supported.
- Data collection (Electronically Stored Information "**ESI**")
  - Data collection can be hard as customer may not have the required access.
  - Access and bandwidth costs - Prevents collection of large amount of data quickly. Establish a protocol to handle this.
  - Bit byt bit imagin - Not generally possible due to multitenancy. Usually mandated due to resource pooling. 
  - No direct access - IT equipment seizures for the purpose of evidence preservation.
  - Standard formats (e.g. PDF) - Favour this over proprietary unless some evidence is lost during conversion. 
  - Storing data in the cloud not does prevent its being used as evidence. Should not be considered more or less admissible or credible merely because they were created or stored in the cloud.
  - Discovery by design - data in the cloud is available during e-discovery. 
  - [Sedona Conference](https://thesedonaconference.org/) - Recommendations for handlin ESI. (non-profit organisation)
 
 # 4. Compliance and audit management
 - Compliance audit and assurance should be continous.
 ### Goverance, Risk and Compliance (GRC)
  - Compliance managenent is a tool of governance, it is how an organisation proves it is meeting internal and external obligations. 
  - Information security is coupled with compliance.
  - Customer is ultimately responsible for their compliance.
  - Customer has to depend on third-party attestations of provider to understand their compliance and alignment/gaps.
  - Pass-through audit - form of compliance inheritance. Providers services including infrastructure has gone through an audit to a compliance standard. Provider maintains their compliance.
  - Customer must understand where their data and services are.
  - Note that not all services are audits aganist all compliance regimes, customer must make sure they use the vetted services to build their compliant solution.

### Audits
- Audit and assessments are mechanisms to document compliance with internal and external requirements. It is expected to include compliance determination (what is the outcome). 
- Audit management include management of all activities related to audits and assessmenets.
  - Determines requirements
  - Scope
  - Scheduling
  - Responsibilities
- Customer may need to sign NDA before gainining access to attestations from providers.
- Attestations and certifications are point in time activities. 
- Audit artifacts are:
  - Logs
  - Documentation
  - Materials needed for audits and compliance
  - System configuration details
  - Activity reporting
  - Change managemnent details

- Attestation is a legal statement from a third-party which describe their statement of audit findings. 
- CSA CCM can be used to maintain requirements and current status.

# 5. Information governance
- Information is data with value.
- Ensures that data and information complies with organisational policies, standards and strategy including regulatory, contractual and business objectives. 
- Determines how data is handled in accordance with goals and requirements. 
- By hosting data in cloud, a third-party is introduced to the governance model. 

### Things that impact 
- Multitenancy - Data is stored in shared infrastructure.
- Shared reponsibility model - customer and provider responsibilities
  - Data ownership - who owns the data. Defines rules how data is managed.
  - Custodianship - who is managin the data. Implements the rules.
- Information classification 
- Information management policies - what is allowed to go and where in cloud?
- Location and jurisdictions -legal requirements are hard lines.
- Authorisatins
- Privacy - sum of regulatory, contractual and commitments to customer
- Contractual - legal tool for extending governance to cloud
- Security controls - tools to implement data governance

### Data security lifecycle
- Describes the phases information passes through but does not address its location or how it is accessed.
- Information lifecycle does not map well to needs of security professionals.
- Data security lifecycle maps to needs of the security audience.
- Phases (note; things that can be done (functions) to data are **Read**, **Process** and **Store**). Access is controlled by entitlements.
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
- Ensure stronge perimeter security for API gateways and web consoles.

### Consideration for BC/DR
- Continuity and recovery within the provider itself (less multi-cloud)
- BC/DR is shared responsibility too
- Must account for entire logical stack
- Prepare for provider outage.
- Seek/consider options for portability (Containers)
- Architect for failure
- Use multi-zone deployments to address high availability
- Keep a note that single resource is less resilient in cloud than in private due to fragility of virtualised resources running in complex environments.
- Life and shift to cloud without architectural changes can reduce resiliency.
- Design for RTO and RPO in traditional environments.
- Take a risk based approach.

### Preparation for DR
- Metastructure - Backup configuration (IaC)
- Software defined infrastructure - Template where possible
- Any custom images are available in right regions
- Infostructure - data synchonisation
- Applistructure - message queues and code is available, PAAS limitaions (dont forget key management services)
- Real-time failover may not be possible - design apps and RPO appropriately.
- SAAS providers have the bigest outage concern. Extracting data periodically might be the only way.
- Data residency is a key factor.

### Interaction with cloud
- Usually through APIs which are REST, CLI and SDKs.
- Uses variety of authentication mechanisms (e.g. OAuth, Federation)
- Identity and Access management (IAM) used to manage access to management console. 
- RBAC allows super or low-level administrative roles/permissions. 
- All priviledge account must use multi-factor (MFA). Most effective security control to prevent wide range of attacks.

# 7. Infrastructure security
- Foundation for operatin securely in the cloud. Lowest layer of security from customer perspective.
- Macro-layers
  - Fundamental resources that pooled together to create a cloud. (raw compute, networks and storage)
  - Virtual abstracted infrastructure
- Networks in cloud (they are separate physical networks)
  - Management network - traffic from management plane
  - Storage network - connects virtual storage to virtual machines
  - Service network - communication beween virtual networks. Build the network resource pool for customers.
- Network virtualisations
  - Virtual Local Area Networks (VLANs) - Designed for single tenant networks (separate different departments/business units). Not suitable for cloud-scale networks.
  - Software defined networking (SDN) - Complete abstraction over physical networks. Offers higher flexibility and isolation. Security isolation boundary. Uses packet encapsulation to move packets around the network and virtual machines are unaware instead they connect using a standard networking interface. 
- Note that customer looses the direct management of underlying physical network. 
- Normal practice of inserting appliances between communication paths is not always possible as networking is virtualised.
- Customers expected to use in-line virtual appliances or software agents for security. 
  - Virtual appliances can become bottlenecks as they cannot fail-open (all traffic must be intercepted).
  - Cost of resources to meet network requirements
  - Virtual appliance is expected to auto-scale to match elasticity (metered service and rapid provisioning)
  - Keep up with velocity of changes in the virtual network.
  - Virtual IP assignments changes frequently, therefore traffic is expected identify by unique ID than IP. This could impact alerting and monitoring. Dynamic environment. 

### SDN benefits
- Ability to build many virtual networks without the constraints imposed by physical hardware. No more address conflicts as each network is isolated (two networks with the same CIDR blocks). Think micro-segmentation.
- SDN firewals (security groups) - Defines a set of policies (egress and ingress traffic rules).
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
- Microsegmentation (hypersegmentation) - usng virtual networks to run smaller isolated networks.
  - Option was not available previously because of cost.
  - Reduce blast radius. (maintains segregation and isolation)
  - Lateral movement is difficult 
  - Increase operational cost
  - Greater flexibility and security for evolving network topologies
  - Note that providers are responsible for perimeter security
  - Implement cloud firewalls per-workflow instead of per-network basis.
- Hybrid connections may reduce the security of cloud networks (hybrid - between private to public cloud)
- **Bastion** or **transit** networks are an emerging standard
- Compute abstractions
  - Virtual machines - host level isolation offered. 
  - Containers - code execution isolation, shares resources from the operating system. Runs segregated processes. Container configuration provides capabilities available for the container. Process isolation technique.
  - Platform-based workloads - running solutions on shared PAAS (e.g. procedures on a database platform).
  - Serverless computing - executes application code directly. Provider manage all the underlying layers including foundation security.
- Immutable workloads
  - No longer make any changes to the runnin workflow (no image change). Update the underlying image and redeploy replacing the old. There is degree of immutability (e.g. centralised configuration management pushing changes to instances).
  - Enable stronger security - no remote login, file integrity monitoring
  - Reduced vulnerability scanning on running workloads.
  - Consistent image creation process is required (automation to update deployments)
  - Security testing integrated into imagine building process
- Impact on standard workloads
  - No agents on non-VM based workloads
  - Traditional agents may impede performance
  - Agents expected to be cloud-ready (some agents maybe unaware of runnin environment or auto-scaling)
  - Agents might require additional ports to be opened.
  - IP addresses are dynamically assigned to multiple systems in a short duration (elastic)
  - Logs should be collected externally due to high velocity of change.
  - Logging architecture has to account for cloud storage and cost
- Vulnerability assessement
  - Require notification of asssessments (pen testing)
  - Default deny will prevent assessements (require opening up ports)
  - Assessements maybe able to run during image creation
 
# 8. Virtualisation and containers
- Key building block (categories)
  - Compute
  - Network
  - Storage
  - Containers
- Virtualisation is essential for cloud and adds two further layers of security
  - Security of virtualisation technology
  - Security controls for virtual assets
- Provider responsible for physical and virtualisation platform
- Customer is responsible for available virtual security controls and understanding risks. 
  - When to encrypt cloud storage
  - When to configure virtual firewalls
  - When to use dedicated or shared hosts  
- Provider must assure **isolation** and **virtualisation infrastructure**. Virtualisation of cloud users so that volatile memory security is secured from each tenent (referring back to isolation concept). 
- Customer must implement security for the workload.
  - Secure cloud management portal
  - Monitor and logging
  - Image asset management
  - Dedicated hosting where appropriate
  - Responsible for security within virtualised resources
 ### Networks
 - Route traffic to a virtual network monitoring or filter so that communication between VMs in a same physical host can be monitored. Or bridge network traffic back out to the network via a virtual appliance on the same network. Note that both will create bottle-necks and less-efficent routing.
 - Provider is expected to disable packet sniffing and metadata leaks that could expose configuration between tenents. Neither tagging or SDN-level metadata.
### Storage
- Achieved through Storage Area Networks (SAN) and Network Attached Storage (NAS).
- Data is replicated across different locations (encrypted)
### Containers
- Isolated userspace but shared kernel space
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
- Prepartion for IR is the key.
- Stages
  - Preparation - Setup IR capability in the organisation
  - Detection and analysis - Alerting, scope of the incident, use platform logs, SAAS is difficult. Data sources is quite different; feed off management plane when data not available. Limited network visibility. Usually network logs from provider tend to be flow logs not full packet capture. Instrumentation when provider logs are not available. Validate whether provider logs meet chain of custody requirements. Greater need to automate forensic due to dynamic nature of the cloud.
  - Containment and eradication - Take systems offline, data loss vs service availability, chain of custody. Break-glass procedure to use root master credentials to ensure full visibility (as security trimming might make some log not accessible or visible). SDN helps to build clean environment and isolate attacks (think micro-segmentation) using virtual firewalls. No need to immediately eradicate attacker, instead isolate using virtual firewalls. With SAAS and PAAS quite hard since there is no access to VMs.
  - Post-moretem - What could be done? could we have detected early, if so how?. Understand data limitations and see for improvements.
- All stages/phases of IR is impacted by cloud.
  - SLAs and governance - Understand these and require coordination with provider.
- Built security into the code that runs in the container
- Need to know what data and logs are available for investigation
- Cloud jump kit - Tools needed to investigate in a remote location
- Architect for faster detection (containment and recoverability)
- Things to help investigation
  - Enable instrumentation
  - Utilise isolation
  - Use immutable servers
  - Implement application stack map
  - Threat modeling and tabletop exercise
- Testing of IR expected to be carried out annually or after a significant change.

# 10. Application security
- Early designs to maintaining and defending production applications.
- Higher baseline security - offered by provider as they need to maintain standards and compliance to regulations.
- Responsiveness - automation via APIs.
- Isolated environments - hyper-segregation
