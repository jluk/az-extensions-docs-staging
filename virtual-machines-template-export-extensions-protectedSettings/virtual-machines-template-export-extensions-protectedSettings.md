<properties
	pageTitle="Template Export and Redeploy | Microsoft Azure"
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

Automation script supports education of ARM templating and duplication of existing resource group configurations.
This article will cover how to export ARM templates from existing resource groups and how to redeploy the exported template.

#Exporting your Resource Group
To begin you need to login to the Azure portal. Navigate to the existing Resource Group you want to export and select "Automation Script".

#Editing your ARM template

Note: If your Resource Group uses extensions that require sensitive information, you will need to edit the ARM template.
You can find the required parameters for the extension at the ARM Schema repository. Search for the extension relevant to you and copy/paste the protectedSettings json object into your template.

Now you can paramaterize the properties you have just added by replacing the parameters like this:

#Deploying your ARM template
Click the "deploy" button to deploy the template.

Fill out the UI form created from your ARM template.

Note: For nested resource types such as Extensions, you must specify the resource name with the parent resource prepended to the string. For example:
"testVM/testExtensionName"

When you are happy with the configurations, acknowledge the terms of service and click deploy.
Congratulations, you have just created and deployed an ARM template!