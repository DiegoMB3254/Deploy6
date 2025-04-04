Automatic Deployment Workflow:
This GitHub Actions workflow runs every time a push is made to the main branch. Below are the step-by-step details of the process.

Job: Deploy

Operating System: ubuntu-latest (the latest available version of Ubuntu).

Workflow Steps
Repository Checkout
The actions/checkout@v2 action is used to clone the repository into the execution environment.

SSH Deployment Setup
Environment variables are defined based on the repository's secrets, such as:

SSH keys

Username

Remote host

Project path

Then:

The .ssh directory is created in the execution environment.

The private SSH key is configured for authentication.

Remote host information is added to the known hosts using ssh-keyscan.

SSH Connection and Remote Deployment
An SSH connection is established with the remote server.
If the project directory does not exist, the repository is cloned from GitHub into the specified path.
A git pull is executed to update the repository with the latest changes from the main branch.
