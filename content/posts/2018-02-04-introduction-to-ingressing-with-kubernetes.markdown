---
author: priyankvex
date: 2018-02-04 14:51:22+00:00
draft: false
title: Introduction to Ingressing With Kubernetes
type: post
url: /2018/02/04/introduction-to-ingressing-with-kubernetes/
tags:
- demo
- deployment
- edx
- ingress
- intro
- kubernetes
- minikube
- routing
- services
---



Single responsibility is a magical notion. Whatever it touches, it makes it more manageable and efficient.

With _Kubernetes, _we have the power to spawn many services. As many of them as we would like. But how inbounds requests are routed among these services?

**_Ingressing _**is a powerful way to decouple routing rules with core application logic.

According to _kubernetes,_


<blockquote>Ingress is a collection of rules that allow inbound connections to reach to reach cluster services.</blockquote>




## Overview


In this post, we'll deploy a couple of services in the kubernetes cluster and then define an ingress to route the requests to one of them according to the rules.

By the end of this post, we'll have a basic understanding of **_ingressing _** and a _**working demo **_to showcase its power.


## More On Ingress


To allow inbound connections to reach cluster services, ingress configures a layer 7 load balancer and provides the following:



	  1. TLS.
	  2. Path-based routing.
	  3. Name-based virtual routing.
	  4. Custom Rules

With ingress, connections can't reach our services directly. Instead, they reach the ingress endpoint and then are routed to a service based on rules.

With this in mind, let's move forward to a working example.


## Step 1: Spawn first service and deployment


We'll be creating two services and deployments, named _**cats **_and _**dogs.**_

In this step, we'll be spawning our first service.

https://gist.github.com/priyankvex/d2b69f0417d7f4321f2d00f34621946b

Above is the ._yaml_ file for our _cats-deployment. _Run the following command to create the _cats-deployment._

    
    
    kubectl create -f cats-deployment.yaml --validate=false


Now, we'll create our _cats-service._

https://gist.github.com/priyankvex/cb1a9328127de44a6de483584643fcf0

Run the following command to create our _cats-service._

    
    kubectl create -f cats-service.yaml --validate=false


As you can see in the deployment file, we are also specifying a volume associated with the container named _**/home/docker/cat_volume.**_

Run the following commands after starting your minikube VM to host a file at that volume's path.

    
    minikube ssh
    mkdir cat_volume
    echo "<h1>cat service content</h1>" > "index.html"


Tada! We have our first service and deployment up and running.




## Step 2: Create the second service and deployment


We are going to name this one _dogs._

Following the steps given, above create the deployment and service for our faithful friends _dogs._

Here are the YAML files.

https://gist.github.com/priyankvex/d49696ba9b349d94bf3638251d8388a7

https://gist.github.com/priyankvex/20b506c3db9d5ae19c4cb5972113d991




## Step 3: Hit the endpoints of our services to see the content we just hosted on them.


Run the following command to get port numbers for the services.

    
    kubectl get services


This will list all the services running the in kubernetes cluster along with their post numbers.

We should see something like this.

![kube_services](https://priyankvex.files.wordpress.com/2018/02/kube_services.png)


Get the port numbers and hit the browser to reach the pages of the two services we just hosted.

Use the following command to get base IP of the minikube VM

    
    minikube ip


Here is how our two services _cats _and _dogs _are looking.



[gallery ids="1043,1044" type="rectangular"]




## Step 4: Create the ingress for our services.


Following is the YAML file that we'll use to create the ingress.

https://gist.github.com/priyankvex/05aa1b9d75436803d9f44ef9643c7dc6

First, we need to start the ingress controller.

    
    minikube addons enable ingress


With the following command, create the ingress.

    
    kubectl create -f pets-ingress.yaml --validate=false


As we can see in the YAML file, we are doing name-based virtual routing between cats.myweb.com and dogs.myweb.com, routing them to our cats and dogs service respectively.

For the sake of our demo to work, we'll have to add these hosts in our /etc/hosts file.

Add the following line in your /etc/hosts file.

    
    192.168.99.100   cats.myweb.com dogs.myweb.com





## Step 5: Hit the paths to see the ingress controller in action!


![dogs_2](https://priyankvex.files.wordpress.com/2018/02/dogs_2.png)
![cats_2](https://priyankvex.files.wordpress.com/2018/02/cats_2.png)


Congrats! Our ingress is working as expected and routing the names to their services like a routing ninja!




## Conclusion


In this post, we got to know basics of ingressing and created a working demo to get the feel of its power.

There is a lot that ingress can do, let's all keep exploring untill we fully learn how to harness its power.



 

# That’s all, folks!
