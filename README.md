# Ironclad EA ServiceNow Example Code
This repository contains all of the ServiceNow application assets for the EA ServiceNow solution guide.

# Installing the ServiceNow application
## Create Github credential
You will need to create a credential in ServiceNow to hold an SSH key for an Github account that can access this repo. If you are only importing the application into ServiceNow (e.g., for a demo), then you only need read access to the repo. If you are making application changes that you want to save back to the repo, you will need read/write access.
### Create SSH Key
If you do not already have a suitable SSH key registered in your Github account, you will need to create one.  Note that ServiceNow has limitations in terms of what encryption algorithms it will support for SSH credentials (e.g., it does NOT support ED25519 encryption, but it DOES support ECDSA).  

Use whatever SSH key generation tool you have - if you are using ssh-keygen on a Mac or other Unix platform, you would do the following to create a new ECDSA key pair:

```
> cd ~/.ssh
> ssh-keygen -t ecdsa -C "<your Github account email address>"
```
### Register SSH key with your Github account
### Create ServiceNow SSH Credential

## Import ServiceNow Application
- Create an account/login to developer.servicenow.com
- Create a new developer instance if you don’t have one already
- In the developer instance, go to System Applications -> Studio (e.g., search for “Studio” in the main search)
- In the dialog that appears, choose "Import from Source Control"
- In the dialog that appears, choose the "ssh" option, enter the Github URL for the repository with the ServiceNow code (this repository), choose the SSH credential you create above, and specify the branch containing the code version you want.
## Configure Ironclad Webhooks
Once the application is loaded, you need to retrieve the endpoints of the Scripted REST resources defined in the app and register them to receive webhooks from your Ironclad instance.  In Studio, navigate to the Inbound Integrations -> Scripted REST Resources, and for each item in this list, select it and capture the "Resource path" in the details for the REST endpoint. The full endpoint URL will be the domain of your developer instance (see your browser address bar, typically this will be of the form "devXXXX.service-now.com").  