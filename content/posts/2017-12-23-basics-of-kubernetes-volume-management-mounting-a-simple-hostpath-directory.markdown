---
author: priyankvex
date: 2017-12-23 20:02:04+00:00
draft: false
title: 'Basics Of Kubernetes Volume Management :  Mounting a simple hostPath directory'
type: post
url: /2017/12/24/basics-of-kubernetes-volume-management-mounting-a-simple-hostpath-directory/
---

![kubernetes](https://priyankvex.files.wordpress.com/2017/11/kubernetes.jpg)


Kubernetes is a system for automating deployment, scaling, and management for containerized applications.

As we know, containers, which create the Pods, are ephemeral in nature. All data stored inside a container is deleted if the container crashes. However, **kubelet** will restart it with a clean state, which means that it will not have any of the old data.

To overcome this problem, Kubernetes uses [Volumes](https://kubernetes.io/docs/concepts/storage/volumes/). A Volume is essentially a directory backed by a storage medium.

**Volume Type :**

A volume that is mounted to a pod can be seen as a directory. Each directory is backed by a directory type.

Kubernetes provides many directory types like emptyDir, hostPath, secret, nfs etc.

You can read more about kubernetes volume  [here](https://kubernetes.io/docs/concepts/storage/volumes/).

In this blog we are going to use the volume type hostPath.

**hostPath Volume Type**

With hostPath volume type, we can share a directory from the host to a pod. So, even if the pod dies, the data is persisted as the directory is present at the host machine.

**Demo Time : **

Fun time! The best way to get our head around volumes is to quickly try an working example.

**Step 1 : Make sure the minikube VM is running with the kubernetes cluster**

As we are using minikube to run our kubernetes cluster, let's first ensure that our minikube VM is up and running.

![minikube_starting](https://priyankvex.files.wordpress.com/2017/12/minikube_starting.png)


**Step 2 : Create the directory we want to mount in the host**

In this case, out minikube is the VM which is acting as host for our kubernetes cluster.

Let's SSH into the minikube and create the directory and file that we need.

![minikube_ssh_creating_index_page](https://priyankvex.files.wordpress.com/2017/12/minikube_ssh_creating_index_page.png)


As we can see, we did following things in this step :



	  1. We ssh'ed in the minikube VM.
	  2. Create the my_vol directory that we'll need to share with pod.
	  3. Create the file index.html in the my-vol directory.
	  4. Got the path of the directory.

**Step 3: Create the deployment specifying the volume that we want to mount**

** ![deployment_yaml](https://priyankvex.files.wordpress.com/2017/12/deployment_yaml.png)
**

Given above is the what our deployment file looks like.

Let's type that content by hand so that we pay heed to each and every property of the file.

Note that the path that mount path in the container is the place where nginx looks for the html page by default.

So, basically what's happening is, we are telling the container that your "/use/share/nginx/html" path is mapped to the "/home/docker/my-vol" path in the host machine,

Once that file has been saved, use the following command to create the deployment.

![deployment_created](https://priyankvex.files.wordpress.com/2017/12/deployment_created.png)


**Step 4: Create the service yaml file and start the service:**

Once our deployment is up, we need a service to tie it all together.

![service_yaml](https://priyankvex.files.wordpress.com/2017/12/service_yaml.png)


Once the service file is created. Create the service by the command given below.

![start_service](https://priyankvex.files.wordpress.com/2017/12/start_service.png)


**Step 5: Head over to the IP of the minikube and post number of the service to view the web page**

We can use the command

`kubectl get my-nginx-web-service`

to get the post number

![web_page](https://priyankvex.files.wordpress.com/2017/12/web_page.png)


And there we go! We can see our own page read from our mounted volume, running inside a container in a kubernetes cluster!
