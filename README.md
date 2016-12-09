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
  * Additional resources

Please enumerate all operating systems your extension is supported on, this is important to stop users from attempting an extension deployment on an unsupported operating system.
Also include any additional resources required by your extension such as external storage, access to internet, or other cost-incurring resources required by your extension.

###Configuration
  * Public configuration settings
  * Protected configuration settings

For users to deploy extensions properly, you must define and describe each parameter required by your extension and whether it can/should be used as a public or protected configuration.

###Template Deployment

This section describes the extension ARM schema. This is required for users to deploy your extension in custom ARM templates if necessary.

###Azure CLI Deployment
  * azure vm extension set <resource-group> <vm-name> <extension-name> <extension-publisher-name> <extension-version> <public-settings-file> <private-settings-file>

This refers to the CLI 1.0 version written in Node.js as of today.

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
