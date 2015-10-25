# Towaco
Towaco - Intro to Infrastructure as Code

# Introduction

The intent of this project is to get up and running using Infrastructure as Code principles.  In order to easily create and destroy your Infrastructure, you are going to need a place where you can easily spin up resources, and then destroy them.  While some people might be able to have a lab at home with plenty of compute, network, and storage, most will not.  Thankfully there are a number of inexpensive Cloud Providers that you can use as a lab environment.  We will start with Azure, and eventually (hopefully) use the same principles with some other Cloud Providers.


# Bootstrapping an Infrastructure as Code Environment

## Azure

There is lots of information out there on setting up Azure environments, but most how-to guides are by Microsoft, and assume that you are using Windows.  For this project, we will assume the use of Mac OS X.  Which means we will be using the Windows Azure CLI.  The Windows Azure CLI is written in Node.js, which is a nice way to create cross platform applications.

The following steps could be automated, but for now we will just walk thru them, and automate them at some future time [(backlog item)](https://github.com/dondemsak/towaco/issues/1).

### Installing Node.js
Before you can install the Windows Azure CLI, you will need to have Node.js installed.  Go to the Node.js Download [site](https://nodejs.org/en/download/) and download the Mac OS X installer.  Then install Node.js

To verify that it was installed correctly, open a Terminal Window and type:
```
npm -v
```

If it shows the version of the npm installed, you can go ahead and install Windows Azure CLI.

### Installing Windows Azure CLI
You can use the Node.js package manager to install the Windows Azure CLI package.  The easiest way on a Mac is to use sudo Terminal command, which will prompt you for the password for the administrator account you are currently logged in as.  Open a Terminal Window and type:

```
sudo npm install -g azure-cli
```

You may get a popup window asking to install the xcode build tool.  You can jsut cancel out of that popup.

To test that the Windows Azure CLI has been installed correctly, in the Terminal Window enter the following:
```
Azure help
```

## Connecting to an Azure subscription
To connect to your Azure subscription from the Azure CLI, you there is a deprecated way, and the new way.  The new way uses the Resource Manager model, and requires that you are using Azure Active Directory, which means you can't use a personal Azure account.  Thankfully, there is a way to create an organizational account for your personal account.

### Creating an Azure Organizationl Account

References
+ [Install the Azure CLI](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-install/)
+ [Using the Azure CLI for Mac with Azure Resource Manager]( https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-azure-resource-manager/)
+ [Connect to an Azure subscription from the Azure Command-Line Interface](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-connect/)
+ [Create an organizational account on Azure](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-connect/#create-an-organizational-account)
