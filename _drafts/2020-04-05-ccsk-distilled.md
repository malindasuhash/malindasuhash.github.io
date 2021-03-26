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
