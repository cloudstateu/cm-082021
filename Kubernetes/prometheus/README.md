# Prometheus and Grafana

## LAB Overview

#### In this lab you will deploy Prometheus and grafana

## Prerequisite: Install Helm

1. Follow the instructions: https://helm.sh/docs/intro/quickstart/

## Task1: Install Prometheus

1. Add the Helm charts repository
``helm repo add stable https://kubernetes-charts.storage.googleapis.com``

3. Install prometheus:
``helm install prometheus stable/prometheus --version 9.0.0``

#The Prometheus alertmanager can be accessed via port 80 on the following DNS name from within your cluster:
``prometheus-alertmanager.default.svc.cluster.local``

#The Prometheus server can be accessed via port 80 on the following DNS name from within your cluster:
``prometheus-server.default.svc.cluster.local``

4. forward traffic to server URL
``export POD_NAME=$(kubectl get pods --namespace default -l "app=prometheus,component=server" -o jsonpath="{.items[0].metadata.name}")``
``kubectl --namespace default port-forward $POD_NAME 9090``

5. install grafana
``helm install grafana stable/grafana``

6. get the grafana password to login
``kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo``

7. forward the port to grafana
``export POD_NAME=$(kubectl get pods --namespace default -l "app=grafana,release=grafana" -o jsonpath="{.items[0].metadata.name}")``
``kubectl --namespace default port-forward $POD_NAME 3000``

8. login to graphana
``user: admin``
``pass: from previous step``

9. Use this prometheus URL in config:
``http://prometheus-server.default.svc.cluster.local``
