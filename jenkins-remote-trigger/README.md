# Triggering Jenkins builds by URL

## Step 1: Setting up a new user
Trigger a build via URL means that the Jenkins endpoint is open to anyone who can hit the server. Naturally, that means you want to ensure you’ve secured this endpoint as much as possible and the first step is to create a user with limited access to Jenkins. To create a new user:

* Click on Manage Jenkins
* Click on Manage Users
* Click on Create User
* Fill in the information for your user (I’ll assume you’ve called this user "remoteuser")
* Click the Sign Up button
This will take you back to the user list.

## Step 2: Enable permission for remoteuser
In order to allow "remoteuser" to trigger the build, the user needs to have the following permissions set:

Overall - Read
Job - Build
Job - Read
Job - Workspace
To configure these permissions:

* Click on Manage Jenkins
* Click on Configure Global Security
Assuming you’re using matrix-based security: add "remoteuser" to the list and check off the boxes for the necessary permissions
* Click Save
If you are not using matrix-based security, then this step is likely not necessary. Just make sure the "remoteuser" user has the correct permissions.

## Step 3: Create User API Token
In order to make an external call using the "remoteuser" user, you’ll need to use an API token. 

* Login using newly created user
* Click on People -> click on "remoteuser" -> next click on Configure -> API Token -> generate Token

11cbad49cd5efa500c663d7e4a934022f7

## Step 4: Enable the URL job trigger
* Login using newly created user

Go to the job that you want to trigger and click Configure to edit the job. Under Build Triggers, check the box next to “Trigger Builds Remotely”. You’ll be asked to provide a secure token for validation. This should not in any way be related to the "remoteuser" user, so don’t reuse the password. You might want to generate a new key using a tool like the Random Key Generator. Click Save to save the job information.

## Step 5: Create the URL

Using Created information, you can now create a URL that looks like this:

```
http://remoteuser:11cbad49cd5efa500c663d7e4a934022f7@52.87.207.81:8080/job/remote-build/build?token=wdvd87687we32y8tyc

```
Note that "remote-build" should be replaced with the job name you’re triggering. 

This URL has three key pieces of information:

The username remoteuser
The API token (after the colon)
The authentication token
All three must be correct, and the permissions for the user must be correct in Jenkins, in order for this URL to trigger the job. In order to trigger the job, you must send a POST request. You can test it out using cURL:

```
curl -X POST http://remoteuser:11cbad49cd5efa500c663d7e4a934022f7@52.87.207.81:8080/job/remote-build/build?token=wdvd87687we32y8tyc
```

Once you send the request, log in to Jenkins and verify that the job is running. You can then use this URL for most webhooks.

