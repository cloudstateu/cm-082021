<img src="../../../img/logo.png" alt="Chmurowisko logo" width="200"  align="right">
<br><br>
<br><br>
<br><br>

# Deploy an application

## LAB Overview

In this lab you will add a Build Trigger to the application from [previous lab](../11-deploy-dockerfile-application/README.md). The Build Trigger will start build as soon as code on repository change.

## Requirements

1. Github account
1. Finished [previous lab](../11-deploy-dockerfile-application/README.md)

## 1. Get the webhook URL

1. Open side menu, click on "Builds" and select Build Configuration.

   ![img](./img/01-build.png)

1. On Build Configuration page scroll down and click on "Copy URL with secret" for Github.

   ![img](./img/02-copy-github.png)

## 2. Setup webhook on Github

1. Go to [Github](https://github.com/), find your forked repository and go to its settings.

   ![img](./img/03-settings.png)

1. Find Webhooks and click on "Add webhook"

   ![img](./img/04-webhooks.png)

1. Paste the copied URL into the "Payload URL" field, change "Content type" to `application/json`, leave "Secret" empty.

   ![img](./img/05-webhooks-settings.png)

1. Click "Add webhook"
1. Wait few seconds and check if your webhook has green check mark. If it still grey - refresh the page.

   ![img](./img/06-succes.png)

## 3. Update the code

1. Go to the "Code" tab, click on `server.js` file and edit it.

   ![img](./img/07-code.png)
   ![img](./img/08-edit.png)

1. Increment the `VERSION` variable and commit

   ![img](./img/09-change-version.png)

## 4. Check build status in OpenShift

1. If you setup webhooks correctly you should see that the new build has started (or it is finished already a few seconds ago)

   ![img](./img/10-check-build.png)

1. Visit the application page and check if the version has changed. Try refreshing page using `Ctrl + F5`, if the version doesn't change.

   ![img](./img/11-new-version.png)

## END LAB

<br><br>

<center><p>&copy; 2021 Chmurowisko Sp. z o.o.<p></center>
