# Towaco Azure Bootstrap Instructions

## Connecting to an Azure subscription
To connect to your Azure subscription from the Azure CLI, you there is a deprecated way, and the new way.  The new way uses the Resource Manager model, and requires that you are using Azure Active Directory, which means you can't use a personal Azure account.  Thankfully, there is a way to create an organizational account for your personal account.

## Creating an Azure Organizational Account

1. Sign in to the [Azure Portal](https://manage.windowsazure.com/)
2. If no directory exists, select Create your directory and provide the requested information.
3. Select your directory and add a new user and set the role to User. This new user is an organizational account.  During the creation of the user, you will be supplied with both an e-mail address for the user and a temporary password. Save this information as it is needed later.
4. From the Azure portal, select Settings and then select Administrators. Select Add, and add the new user as a co-administrator, using the new user's email address (that you saved from the previous step). This allows the organizational account to manage your Azure subscription.
5. Finally, log out of the Azure portal and then log back in using the organizational account. If this is the first time logging in with this account, you are prompted to change the password.
6. Make sure you see your subscriptions when you log in with the new account.

## Testing Your Organizational Account With Azure CLI

To log in from the Azure CLU using your new organizational account use the following command:
```
azure login -u <username>
```
Enter your password when prompted.

To log out, use the following command:
```
azure logout -u <username>
```

## Storage of CLI Settings
When you log in with an organizational account, your CLI profile and logs are stored in a .azure directory located in your user directory. Your user directory is protected by your operating system; however, it is recommended that you take additional steps to encrypt your user directory. You can do so in the following ways:

On Mac, turn on FileVault for the directory.

# Building Your Environments using Azure CLI

## Setting the Azure Resource Manager Mode

Make sure you are logged in with an admin account before continuing.

Because the Azure Resource Manager mode is not enabled by default, you must use the following command to enable Azure CLI Resource Manager commands.

```
azure config mode arm
```
