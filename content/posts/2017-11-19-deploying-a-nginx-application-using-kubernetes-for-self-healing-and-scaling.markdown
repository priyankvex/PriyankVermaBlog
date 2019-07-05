---
author: priyankvex
date: 2017-11-19 15:50:50+00:00
draft: false
title: Deploying a nginx application using Kubernetes for Self-Healing and Scaling
type: post
url: /2017/11/19/deploying-a-nginx-application-using-kubernetes-for-self-healing-and-scaling/
tags:
- alpine
- app
- Application
- coding
- container
- deploy
- DevOps
- docker
- google
- healing
- how
- in
- Internet
- introduction
- k8s
- kubernetes
- minikube
- nginx
- scaling
- self
- technology
- tp
- tutorial
- web
---

Kubernetes is an open source system for automating deployment, scaling and management of containerized applications. A more technical term for it is, _container orchestrator_ which is used to manage large fleets of containers.

_**Minikube**_ is an all-in-one single node installation for trying out kubernetes on local machines. And the following post covers deploying a nginx application container using kubernetes in minikube.

If you don't have, then this link has it all to install minikube and kubectl (command line tool to access minikube) : [Download and install minikube and kubectl](https://kubernetes.io/docs/tasks/tools/install-minikube/)

**Step 1 : Making minikube up and running**

Ensure that minikube is running.

![starting_minikube](https://priyankvex.files.wordpress.com/2017/11/starting_minikube.png)


**Step 2 : Open the minikube dashboard**

Minikube comes with a GUI tool that opens in the web browser. Open the minikube dashboard with following command :

![opening_dashboard](https://priyankvex.files.wordpress.com/2017/11/opening_dashboard.png)


It should open the dashboard in a browser window and it'll look something like this:

![first_look_dashboard](https://priyankvex.files.wordpress.com/2017/11/first_look_dashboard.png)


Looks cool! No?

**Step 3 : Deploy a webserver using the** **nginx:alpine** **image**

Alpine linux is preferred for containers because of its small size. We'll be using the nginx:alpine docker image to deploy a nginx powered webserver.

Now, go the deployments section and click the create button, which will open an interface like below.

![create_app_filled](https://priyankvex.files.wordpress.com/2017/11/create_app_filled.png)


Fill in the details as shown in the image.

We can either provide the application details here, or we can upload a YAML file with our Deployment details.

As shown, we are asking kubernetes to create a deployment with nginx:alpine image as container and that we want 3 pods (or simply instances) of that.

A pod in kubernetes is a scheduling unit, a logical collection of one or more containers that are always scheduled together.

Go on and click that awesome deploy button!

**Step 4 : Analyzing the deployment**

Once we click the deploy button. Kubernetes will trigger the deployment. Deployment will create a ReplicaSet. A ReplicaSet is a replication controller that ensures that specified number of replicas for a pod are running at any given point of time.

Flow is something like this:

Deployment create ReplicaSets, ReplicaSets create Pods. Pods is where the real application resides.

![deployment_overview](https://priyankvex.files.wordpress.com/2017/11/deployment_overview.png)


As expected, we have our deployment, replica set and pods in place.

We can also, check our deployment via command line using kubectl.

![deployment_overview_cli](https://priyankvex.files.wordpress.com/2017/11/deployment_overview_cli.png)


**Step 5 : Create a Service and expose it to the external world with NodePort
**

So far, we have our pods up and running. But how do we access them?

This is where a service comes into play. K8S provides a higher level abstraction called as a service that logically groups pods and policy to access them. This grouping is done via labels and selectors.

Then we expose the service to the world by defining its service type and service redirects our request to one of the pod and load balances them.

Create a **my-nginx-webserver.yaml** file with the following content:

[https://gist.github.com/priyankvex/3b34ec02c82934b84c8dfb68272ed4f1](https://gist.github.com/priyankvex/3b34ec02c82934b84c8dfb68272ed4f1)






    
    apiVersion: v1
    kind: Service
    metadata:
      name: my-nginx-web-service
      labels:
        run: my-nginx-web-service
    spec:
      type: NodePort
      ports:
      - port: 80
        protocol: TCP
      selector:
        app: my-nginx-webserver





Enter the following commands to create a service name my-nginx-web-service

![creating_service_cli](https://priyankvex.files.wordpress.com/2017/11/creating_service_cli.png)


We can now verify that our service is running :

![service_running](https://priyankvex.files.wordpress.com/2017/11/service_running.png)


**Step 6 : Accessing the application**

Our application is running inside the minikube VM. To access the application from our workstation, let's first get the IP address of the minikube VM:

![minikube_ip](https://priyankvex.files.wordpress.com/2017/11/minikube_ip.png)


Now head to the address and port number of the service we got in above step.

![application_running](https://priyankvex.files.wordpress.com/2017/11/application_running.png)


And our app is running! Amazing, give yourself a pat now!

**Taste of self-healing feature of the kubernetes system : **

One of the most powerful feature of kubernetes is self-healing capabilities (just like Piccolo. DBZ, anyone?). While defining our app we created a replica set with 3 pods. Let's go ahead and kill one pod and kubernetes wil create another one to maintain the running pod count 3.

![self-healing.png](https://priyankvex.files.wordpress.com/2017/11/self-healing.png)


As we can see in the image. We deleted the bottom-most pod and K8S created a new one instantly.

Such kubernetes! Much HA (High Availability)!

**Taste of scaling with Kubernetes:**

Now, our app is receiving a crazy amount of traffic and three nginx pods are not enough to handle the load. Kubernetes allows us to scale our deployments with almost zero effort.

Let's go ahead and spin up a new pod.

![scaling_menu_option.png](https://priyankvex.files.wordpress.com/2017/11/scaling_menu_option.png)


![scaling_to_4.png](https://priyankvex.files.wordpress.com/2017/11/scaling_to_4.png)


Click OK. Now let's go and check our pods.

![scaled_deployment.png](https://priyankvex.files.wordpress.com/2017/11/scaled_deployment.png)


As we can see in the image, we have now 4 pods running to handle the increased traffic.

Isn't it amazing? We just horizontally scaled our application with the power of kubernetes.

This was just the tip of the iceberg what Kubernetes can do. I am also exploring the kubernetes and containerized architecture just like you, hopefully we'll be back with another post soon with more kubernetes stuff!


# That’s all, folks!
