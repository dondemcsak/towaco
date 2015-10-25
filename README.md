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

### Creating an Azure Organizational Account

1. Sign in to the [Azure Portal](https://manage.windowsazure.com/)
2. If no directory exists, select Create your directory and provide the requested information.
3. Select your directory and add a new user and set the role to User. This new user is an organizational account.  During the creation of the user, you will be supplied with both an e-mail address for the user and a temporary password. Save this information as it is needed later.
4. From the Azure portal, select Settings and then select Administrators. Select Add, and add the new user as a co-administrator, using the new user's email address (that you saved from the previous step). This allows the organizational account to manage your Azure subscription.
5. Finally, log out of the Azure portal and then log back in using the organizational account. If this is the first time logging in with this account, you are prompted to change the password.
6. Make sure you see your subscriptions when you log in with the new account.

### Testing Your Organizational Account With Azure CLI

To log in from the Azure CLU using your new organizational account use the following command:
```
azure login -u <username>
```
Enter your password when prompted.

To log out, use the following command:
```
azure logout -u <username>
```

### Storage of CLI Settings
When you log in with an organizational account, your CLI profile and logs are stored in a .azure directory located in your user directory. Your user directory is protected by your operating system; however, it is recommended that you take additional steps to encrypt your user directory. You can do so in the following ways:

On Mac, turn on FileVault for the directory.

## Building Your Environments using Azure CLI

### Setting the Azure Resource Manager Mode

Make sure you are logged in with an admin account before continuing.

Because the Azure Resource Manager mode is not enabled by default, you must use the following command to enable Azure CLI Resource Manager commands.

```
azure config mode arm
```

References
+ [Install the Azure CLI](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-install/)
+ [Using the Azure CLI for Mac with Azure Resource Manager]( https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-azure-resource-manager/)
+ [Connect to an Azure subscription from the Azure Command-Line Interface](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-connect/)
+ [Create an organizational account on Azure](https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-connect/#create-an-organizational-account)
