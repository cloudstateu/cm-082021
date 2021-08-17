<img src="../../../img/logo.png" alt="Chmurowisko logo" width="200"  align="right">
<br><br>
<br><br>
<br><br>

# Connect Multiple Services

## LAB Overview

In this exercise you'll create an application with 3 services (frontend, backend API and MongoDB). You'll expose application to external world.

## Requirements

1. Github account

## 1. Create new project

1. Go to "Developer" perspective, expand Projects drop-down menu and click on "Create project"
1. Name project `cmstudentXX-ratings` (where `XX` is your student number)

![img](./img/01-create-new-project.png)

## 2. Add template for MongoDB

1. Open [file `./files/mongodb-persistent.json`](./files/mongodb-persistent.json) and copy its content

1. Go to OpenShift and click "+" button pointed on below screen:

   ![](./img/02-add-yaml.png)

1. Paste copied content into the Import YAML editor (it works well with YAML and JSON files)

   ![](./img/03-add-yaml.png)

1. As a result OpenShift should create new template named `mongodb-persistent`:

   ![](./img/04-new-template-success.png)

## 3. Create new MongoDB service

1. Go to "+Add" menu and create new service using "From Catalog"

   ![](./img/05-from-catalog.png)

1. Find service named: MongoDB (you can use search bar)

   ![](./img/06-filter-catalog.png)

1. On side panel choose "Instantiate Template"
1. On the next form provide values as follows:

   | Field                       | Value           |
   | --------------------------- | --------------- |
   | Database Service Name       | mongodb         |
   | MongoDB Connection Username | ratingsuser     |
   | MongoDB Connection Password | ratingspassword |
   | MongoDB Database Name       | ratingsdb       |
   | MongoDB Admin Password      | ratingspassword |

   ![](./img/07-instantiate-mongodb.png)

## 4. Deploy Rating API service

1. Go to [`microsoft/rating-api`](https://github.com/microsoft/rating-api) repository ([link](https://github.com/microsoft/rating-api))
1. Fork the Microsoft repository

   ![](./img/08-fork-ratings-api.png)

1. Go to OpenShift, select "+Add" menu and create service using "From Git".
1. Paste the URL to your forked repository. **Do not click "Create" immediately**.
1. In "Advanced Options" section **un-check** "Create a route to the application".

   ![](./img/09-disable-create-route.png)

1. Expand "Build Configuration" section

   ![](./img/10-build-configuration.png)

1. Create `MONGODB_URI` environment variable with below value. **Remember! Change `<OpenShift_project_name>` to your OpenShift project name**

   | Name        | Value                                                                                                    |
   | ----------- | -------------------------------------------------------------------------------------------------------- |
   | MONGODB_URI | mongodb://ratingsuser:ratingspassword@mongodb.<OpenShift_project_name>.svc.cluster.local:27017/ratingsdb |

1. Click "Create"

   ![](./img/11-ratings-api.png)

## 5. Setup Github Webhook for forked repository (`ratings-api`; rating API repository)

1. Go to Administrator perspective, choose _Build_ > _Build Configs_ and find entry with `rating-api` name. Open it and copy Webhook URL for Github using "Copy URL with Secret".
1. Open forked repository, go to _Settings_ tab, select _Webhooks_ submenu and _Add webhook_
1. Paste copied URL to "Payload URL", change "Content type" to `application/json` and save Webhook using "Add webhook" button.

## 6. Deploy Ratings Web service

1. Go to [`microsoft/rating-web`](https://github.com/microsoft/rating-web) repository ([link](https://github.com/microsoft/rating-web))
1. Fork the Microsoft repository
1. Go to OpenShift, select "+Add" menu and create service using "From Git".
1. Paste the URL to your forked repository. **Do not click "Create" immediately**.
1. Expand "Build Configuration" section
1. Create `API` environment variable with below value.

   | Name | Value                  |
   | ---- | ---------------------- |
   | API  | http://rating-api:8080 |

1. Click "Create"

   ![](./img/11-ratings-api.png)

## 7. Setup Github Webhook for forked repository (`ratings-web`; rating web repository)

1. Go to Administrator perspective, choose _Build_ > _Build Configs_ and find entry with `rating-web` name. Open it and copy Webhook URL for Github using "Copy URL with Secret".
1. Open forked repository, go to _Settings_ tab, select _Webhooks_ submenu and _Add webhook_
1. Paste copied URL to "Payload URL", change "Content type" to `application/json` and save Webhook using "Add webhook" button.

## 8. Add a change to rating web application and observe how applications are rebuild

1. Go to forked `rating-web` repository
1. Display contents of `/src` directory

   ![](./img/12-src-directory.png)

1. Open file `App.vue`
1. Change value of `background-color` (line 22; change `#999` to `#0071c5` or vice versa)

   ![](./img/13-make-a-change.png)

1. Check if background color was changed (you can visit page using Incognito mode):

   ![](./img/14-result-1.png)
   ![](./img/15-result-2.png)

## END LAB

<br><br>

<center><p>&copy; 2021 Chmurowisko Sp. z o.o.<p></center>
