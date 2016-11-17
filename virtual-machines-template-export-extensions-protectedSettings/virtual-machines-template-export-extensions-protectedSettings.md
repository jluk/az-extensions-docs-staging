<properties
	pageTitle="How to export and redeploy ARM Templates in Azure Portal | Microsoft Azure"
	description="Learn how to export your resource group into an ARM template"
	services="virtual-machines"
	documentationCenter=""
	authors="jluk"
	manager="timlt"
	editor="tysonn"
	tags="azure-resource-manager"/>

<tags
	ms.service="virtual-machines"
	ms.workload="infrastructure-services"
	ms.tgt_pltfrm="vm-linux"
	ms.devlang="na"
	ms.topic="article"
	ms.date="11/07/2016"
	ms.author="juluk"/>

In this article, we detail how to export an existing Azure Resource Group into an [Azure Resource Manager (ARM)] (https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview) Template.
ARM templates provide custom configuration of Azure resources in order to build custom solutions. You can read more about [Authoring ARM templates here] (https://docs.microsoft.com/en-us/azure/resource-group-authoring-templates).

**Automation Script** is an Azure portal feature that supports education of ARM templates. With the ability to export existing Resource Groups, you can now augment replicatations of existing configurations without starting from scratch.
The process entails navigating to your resource group, selecting Automation Script, adjusting the template as necessary, and selecting deploy.

# Find the resource group to export
1. Sign in to the Azure Portal
2. On the Hub Menu, click **Resource Groups**
3. Select the resource group from the list
4. In the Resource Group blade, click **Automation Script**

![][1]

# Edit your ARM template
In the Azure portal you can view the machine-generated ARM template built from the chosen resource group. This is a good opportunity to read through the template to understand how to utilize Azure resources.

1. Select **Deploy** in the top left-hand corner

![][2]

2. Select **Edit** at the top right-hand of the blade

![][3]

3. Edit the template to desired configuration ( [More information on making ARM templates] (https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview) )

**Note** If your Resource Group uses an extension that requires sensitive information, you will need to edit the ARM template before it can successfully redeploy.

## Redeploy Extensions with protected settings

In this example we will replace the protected settings for the **IaaSDiagnostics Extension**.

1. Open the [ARM Schema repository] (https://github.com/Azure/azure-resource-manager-schemas/blob/master/schemas/2015-08-01/Microsoft.Compute.json)
2. Search for IaaSDiagnostics and copy the properties of the **protectedSettings** object in the IaaSDiagnostics schema

![][4]

3. Return to the Azure Portal template and remove the default parameterized **protectedSettings** property value

![][5]

4. Paste the properties from **Step 2** from the ARM Schema repository

![][6]

5. Remove the default protectedSettings parameter in the **parameters** object at the beginning of the template

![][7]

6. Add a parameter for each protectedSetting property you pasted in from **Step 4**

![][8]

7. Select **Save**

# Deploy your ARM template

The final step is to provide parameters for the ARM template to deploy with.

1. Fill out the UI form

Required parameters in the form UI correspond to parameters in the ARM template without default values to fall back on.

**Note** For nested resource types such as Extensions, you must prepend the nested resource name with the parent resource. In the Extensions example, since Extensions are a resource of virtualMachines the Extension name expects the virtualMachine it is to be deployed on to be prepended. Below is an example input for the VM name and extension name.

![][9]

2. Select **Purchase**

When you are happy with the naming and configurations, acknowledge the terms of service and click deploy.
Congratulations, you have just created and deployed your own ARM template!

[1]: ../media/virtual-machines-template-export/find-rg.png
[2]: ../media/virtual-machines-template-export/portal-script.png
[3]: ../media/virtual-machines-template-export/before-ui-form.png
[4]: ../media/virtual-machines-template-export/iaasdiagnostics-protectedSettings.png
[5]: ../media/virtual-machines-template-export/old-protectedProperty.png
[6]: ../media/virtual-machines-template-export/new-properties.png
[7]: ../media/virtual-machines-template-export/remove-protectedParameter.png
[8]: ../media/virtual-machines-template-export/new-params.png
[9]: ../media/virtual-machines-template-export/new-ui-form.png