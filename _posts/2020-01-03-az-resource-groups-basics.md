# Azure Resource Groups - Basics 

The Azure Resource Manager (ARM) is the core building block in the modern Microsoft Azure platform and Resource Groups plays a critical part of it. 

A Resource Group is a multi-faceted construct. It can be thought of as a container for a collection of resources, scope/permission boundary and influences the location of resources. 

The Azure platform makes creating Resource Groups a trivial activity and it’s an aspect that usually glanced over in training videos.  

In addition to creating Resource Groups using the Azure Management Portal, Azure CLI and PowerShell, Azure Blueprints can also be used to create them. 

An Azure resource is created in a Resource Group, which means the Resource Group must be created prior to deployment.   

There is an excellent write-up on [Resource Groups][ms-resource-group] for reference. The key points to takeaway are: 

> Resources in a resource group expected to share the same life-cycle. 

> Resource Groups can contain resources deployed in other regions  

> Resource Groups can be tagged, but resources within a resource group does not automatically inherit them. 

> Maximum of 800 resource types in a single resource group. 

>Resource belongs to one Resource Group only. 

>Resource groups are not communication boundaries (I.e., cross communication between resource groups is allowed). 

>When the region where the Resource Group deployed is temporarily unavailable, then the resources within it cannot be updated (think read-only).  

## Organising Resource Groups 

The resources in a resource group are expected to share the same-life cycle. Best way to think about the organisation is to consider the following. 

 ![Architecture](/assets/az-rg-basics/architecture.png)

 

The principle behind the above organisation is resource ownership. Typically, resources are owned by technology centric teams in a normal enterprise, which maybe arguable in a DevOps world. An alternative for accepting the above organisation is to consider what happens when all the resources are deployed into a single Resource Group. That would lead to resource access permissions being governed at the resource level.  

The “Application” Resource Group in the above diagram is somewhat fat; that is because an application is normally composed of multiple tiers. Typically, these tiers are data storage/databases, public facing web and business/logic/service each having different usage profiles and security. Depending on how much granularity is desired, each tier could be deployed into its own Resource Group. That leads to team autonomy and eliminate the risk of accidental changes to resources owned by other teams. 

## Security 

The Security in the Public Cloud is an important factor to consider and Resource Groups plays a small of that by recommending best practices. You can see the security recommendations by selecting “Security” under Settings (see the following). 

![Security](/assets/az-rg-basics/security.jpeg)

The security recommendations for Resource Groups are powered by Azure Policy. Each Resource Group is associated with an initiative called **“ASC Default”**. An initiative is a collection of policies which audits the desired state of a resource. ASC as you guessed stand for Azure Security Centre! 

Instead of looking through security warnings across the subscription, with Azure Policy linked to a Resource Group you now have the opportunity to understand and incorporate security best practices at far granular level. 

## Monitoring 

Monitoring is the way to ensure your services are operating as expected and alert if deviates from the baseline. The Azure Monitor is the umbrella service that bring all monitoring aspects such as logs, metrics and alerts together. Monitoring is first class citizen in the Azure platform and there is an area dedicated in Resource Group blade (see the following). 

 ![Monitoring](/assets/az-rg-basics/monitoring.jpeg)

The alerts that are specific to the Resource Group can be setup using the “Alerts” area. The Diagnostic setting can be used to enable publishing of logs, and events to Azure Monitor (see the following). 

Take a moment and consider the breadcrumb (Home > Resource Group > cloud-shell-storage-westeurope).  

![breadcrumb](/assets/az-rg-basics/breadcrumb.jpeg)

## Considerations 

Resource Groups can contain resources that are deployed in other regions. Consider the following. 

 

As per the above illustration, during the creation of an Availability Set, it is possible to set the region that is different to the Resource Group.  

But should we do it? I suggest not. Instead, I would suggest using Resource Groups as regional constructs. I think this would lead to a predictable architecture. 

## Conclusion 

In summary, I simply scratched the surface of Azure Resource Groups. It is an invaluable tool within the Azure Platform and not a simple construct that should be glanced over. Take your time and consider the architecture and ownership as moving resources between Resource Group is possible but can be painful.  

[ms-resource-group]: https://docs.microsoft.com/en-gb/azure/azure-resource-manager/management/overview#resource-groups "msdn"