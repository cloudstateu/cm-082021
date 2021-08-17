<img src="../../../img/logo.png" alt="Chmurowisko logo" width="200"  align="right">
<br><br>
<br><br>
<br><br>

# Deploy an application

## LAB Overview

In this exercise you will fork a repository, create new container image and deploy an application to OpenShift.

## Requirements

1. Github account

## 1. Fork repository

1. [Sign into Github](https://github.com/login)
1. Go to [repository with sample application](https://github.com/macborowy/basic-docker-nodejs) and click on "Fork" button. Follow the Github's instructions.

   ![img](./img/01-fork.png)

1. In a few seconds you should be redirected to your forked repository. Copy the URL.

   ![img](./img/02-forked-repo.png)

## 2. Create new application in OpenShift

1. Log into OpenShift and choose "Developer" perspective
1. Create new project named `cmstudentXX-basic-node` (where `XX` is your student number)

   ![img](./img/03-create-new-project.png)
   ![img](./img/04-create-new-project.png)
   ![img](./img/05-create-new-project.png)
   ![img](./img/06-create-new-project.png)

1. Click "+ Add" menu and choose "From Dockerfile"

   ![img](./img/08-from-dockerfile.png)

1. In "Git Repo URL" field paste your forked repository URL

   ![img](./img/09-naming-app.png)

1. Set up branch name to `main` in Git Reference field

   ![img](./img/10-set-branch-name.png)

1. Give application a name (e.g.: `basic-nodejs-app`)

   ![img](./img/11-naming.png)

1. Check rest of the options that OpenShift has filled
1. Click "Create"

## 3. Observe application deployment and visit the application page

1. Open the Pod details. Observe Pod status and wait for it to be running.

   ![img](./img/12-topography.png)

1. Visit the application and check if it is working.

   ![img](./img/13-working-as-expected.png)
   ![img](./img/14-output.png)

1. Paste the link to your application on a chat.

## END LAB

<br><br>

<center><p>&copy; 2021 Chmurowisko Sp. z o.o.<p></center>
