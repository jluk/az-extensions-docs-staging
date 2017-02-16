
# az-extensions-docs-staging

Welcome to the staging repo for Azure VM Extensions documentation. Please follow the guidelines below to write documentation for your Azure VM Extension.

**Note** You will not be able to publish your extension until the submitted documentation for it has been approved and merged. Documentation is vital to the experience of the user so we appreciate your time in writing this.

The contents for your documentation must follow the appropriate guidelines below. Please refer to the example document for OMS.

##Linux Extension
Azure extensions are written for the specific operating system, thus all Linux documentation must offer the following:

###Overview
  * Brief description of extension
  * Explain common use cases

Please give a brief description of what your extension does, who is offering it, what it does, and how users should expect to use it.

###Prerequisites
  * Supported OS types
  
Please enumerate all operating systems your extension is supported on, this is important to stop users from attempting an extension deployment on an unsupported operating system.

  * Additional resources
  
Also include any additional resources required by your extension such as external storage, access to internet, or other cost-incurring resources required by your extension.

###Configuration
  * Public configuration settings
  * Protected configuration settings

For users to deploy extensions properly, you must define and describe each parameter required by your extension and whether it can/should be used as a public or protected configuration.

##Installing

Please detail all the ways to install your extension (ARM template, CLI, Portal). If your extension is a unique case such as not being able to be manually installed, please detail the circumstances to install and why it cannot be manually installed.

###Template Deployment

This section describes the extension ARM schema. This is required for users to deploy your extension in custom ARM templates if necessary.

###Azure CLI Deployment
  * `foo@bar$ azure vm extension set <resource-group> <vm-name> <extension-name> <extension-publisher-name> <extension-version> <public-settings-file> <private-settings-file>`

This refers to the CLI 1.0 version written in Node.js as of today.

###Portal Deployment (if applicable)

If your extension is available for deployment through the Ibiza portal, document the steps to install the extension. The majority are available through the Extensions Blade:<br>
![][1]
However some are specified through other specific Portal blades such as IaaSDiagnostics and must be called out for users to be aware.<br>
![][2]

###Troubleshooting and Support
  * Troublshooting tips
  * Support contact (email, website, phone)

This must include steps the user can take towards troubleshooting your extension. Often the Azure platform does not have insight for extensions after they are deployed and as a result, it is the responsiblity of the publisher to offer troubleshooting support for the extension.

####Example Linux Extension Documentation
https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-linux-extensions-oms

##Windows Extension

The Windows extension documentation mirrors the above outline for Linux, however you must replace the Azure CLI command with the appropriate Powershell cmdlet.

1. Overview
2. Prerequisites
3. Configuration
4. Template Deployment
5. Powershell Deployment
6. Troubleshooting and Support

####Example Windows Extension Documentation
https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-extensions-oms

[1]: media/readme/ibiza-extensions-blade.png
[2]: media/readme/iaasdiag-ibiza.png
