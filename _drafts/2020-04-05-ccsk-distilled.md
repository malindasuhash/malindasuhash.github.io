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
- Management plane is the interface to connect to metastructure and configure the cloud.
