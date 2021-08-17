<img src="../../../img/logo.png" alt="Chmurowisko logo" width="200"  align="right">
<br><br>
<br><br>
<br><br>

# OpenShift Labs

## LAB Overview

In this lab you are going to deploy a test project ["OSToy"](https://github.com/openshift-cs/ostoy) (created by [OpenShift Customer Success](https://github.com/openshift-cs)) and you will see how the OpenShift can scale the applications manually or automatically.
## Prerequisities

1. Lab `02-view-pod-logging` finished

## 1. Scale up manually

1. Go to the OSToy application and display  "Networking" view. Take note how much _Remote Pods_ are displayed in this moment.
2. Go to the Administrator perspective. Display _Deployments_ and choose `ostoy-microservice`.
3. Scale up to 3 replicas.
4. Go to OSToy application and display "Networking". The number of _Remote Pods_ should change.
5. Scale down your deployment to 1 replica.

## 2. Configure Horizontal Pod Autoscaler

> The _Horizontal Pod Autoscaler_ automatically scales the number of pods based on CPU usage

1. Go to the Administrator perspective. Display _"Horizontal Pod Autoscalers"_. Click _"Create Horizontal Pod Autoscaler"_.
2. Modify the YAML in the following way:

   - change (`name`) in section `scaleTargetRef` to `ostoy-microservice`
   - change value `averageUtilization` to `10`

3. Check how the UI of deployment `ostoy-microservice` has changed

## 3. Increase CPU usage

1. Go to the OSToy application. Display "Auto Scaling" view.
1. Read the instructions and increase CPU usage.
1. Display _Deployment_ `ostoy-microservice`.
1. Wait for 1 minute.
1. See how the number of pods has changed automaticaly.

## 4. Observe the _autoscaling_ behavior in case of low cpu usage

1. Display _Deployment_ `ostoy-microservice`. 
2. Wait for 2-3 minutes.
3. See how the number of pods has changed automaticaly.

## 5. Check the IP address of a service by is't DNS name

1. Go to Administrator perspective. Display  _Services_ list. Copy the name of one of the services from this project.
2. Go to the OSToy application and click "Networking".
3. Fill in `Hostname` filed in section _"Hostname Lookup"_ with the name of chosen Service. Click _"DNS Lookup"_.
4. Check if the IP address matches the ClusterIP in _Service_ details.

## END LAB

<br><br>

<center><p>&copy; 2021 Chmurowisko Sp. z o.o.<p></center>
