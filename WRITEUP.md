# Project 1  _Analyze the resource options for deploying the CMS app_

## Comparison of VM or App Service solution for the CMS app

### App Service
Azure App Service is a PaaS service.
Platform-as-a-Service (PaaS) provides a fully managed platform, where you deploy your app without needing to manage VMs or networking resources.
You can build web apps created with frameworks .NET, Node.js, Java, PHP, Ruby, or Python.
Azure App Service allows developers to focus on their app development while Azure takes care of the infrastructure.

### Virtual Machine
Infrastructure-as-a-Service (IaaS) provides on-demand, high-scale, secure, virtualized infrastructure.
You can create Linux and Windows virtual machines.
Then you deploy whatever software and applications you want onto those VMs.
This infrastructure is like a traditional on-premises environment, except that Microsoft manages the infrastructure.

## Analysis

### Costs
Costs for both are dependant on both the tier and within a tier the instance. *1
To narrow down the options somewhat  I will consider VMs and App Services in the *Standard* tier option

Looking at VMs just in this one tier we have over a hundred options ranging from:
```
A0 with 1 Cores, 0.75 GB RAM, 20 GB Temporary storage, costs $0.02/hour
...
M416s v2 with 416 Cores, 5700 GB RAM, 8192 GB Temporary storage, $83.59/hour
```

Comparing that to the App service *Standard* tier with just three instances to choose from
```
S1: 1 Cores(s), 1.75 GB RAM, 50 GB Storage, $0.100
S2: 2 Cores(s), 3.5 GB RAM, 50 GB Storage, $0.200
S3: 4 Cores(s), 7 GB RAM, 50 GB Storage, $0.400
```

*1 https://azure.microsoft.com/en-us/pricing/calculator/

### Scalablity
The VM solution has greater flexibilty in managing computing cores, ram and temporary storage.

### Availablity
Both VM and App service models have Service Level Agreements (“SLA”).

For App service Microsoft guarantee that Apps running in a customer subscription will be available 99.95% of the time. No SLA is provided for Apps under either the Free or Shared tiers. *2
For VM it is of course, more complicated, with the various configures availablity maybe as high as 99.99% down to 95%. *3

If they do not achieve and maintain the Service Levels for each Service as described in this SLA, then you may be eligible for a credit towards a portion of your monthly service fees. 

*2  https://azure.microsoft.com/en-us/support/legal/sla/app-service/v1_4/
*3  https://azure.microsoft.com/en-us/support/legal/sla/virtual-machines/v1_9/

### Workflow
The workflow is simialar between VM and App service model.
The main difference is the additional responsiblity of maintaining a VM
where you need to do continuous maintainence like applying OS patches for example.

## Select the appropriate solution for the CMS app

I have decided to make the CMS app an App Service Solution

## Justification

The main reason to go with App Service is simplicity.
For this app there is no need for any feature of a VM, therefore, it would be better to use the much simpler App Service solution.
The price for running this app is negligible in either case, but, as inexpensive as a VM is, the App Service has a Free tier.

### Assess app changes that would change your decision.
One reason I would consider changing to a VM model if I had a need to change associated networking or storage components.
Another reason would be if I need to deploy any additional software or applications
