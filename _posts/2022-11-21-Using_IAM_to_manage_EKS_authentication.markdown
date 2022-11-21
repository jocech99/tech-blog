---
layout: post
title: Manage EKS authentication and authorization with IAM (Title)
tags: AWS EKS kubernetes authentication authorization terraform Cloud
date:   2022-11-21 15:47:27 -0500
---
# Using IAM to manage EKS authentication
blahs

## The problem
You have a nice EKS cluster with beautifully crafted networking, managed with you favourite IaC (terraform in this article) and you are wondering how you can use AWS for authentication and authorization in your Kubernetes cluster, instead of manually managing auth with Kubernetes.
If this is a problem you considered, I have found these instructions to be clear and to the point (and similar):
* https://www.eksworkshop.com/beginner/091_iam-groups/intro/
* https://medium.com/swlh/kubernetes-access-control-with-iam-and-rbac-e9c051ee226b

Why bother, would you say?  In this article, I bring this a little further along, using terraform to provision this and add a little functionality.

## Why?


# Basics: Where does it belong?
With Kubernetes mixed up with cloud services, I often find it unclear where should the stuff go.  If you are using a cloud provider, you are probably alread using and IaC for your infrastructure.  Kubernetes is normally configured with a mix of kubernetes, helm, kustomize and other tools. But what about the cluster fundamentals?  I mean either the cluster configuration or these services that are expected to be present when you deploy applications, microservices or whatever you like to your cluster such as authentication and authorization, log collector, service mesh,... Should they be initialized as an init phase in Kubernetes or should this be done as part of the infrastructure provisioning in terraform?  To blurry things further, there are tools, such as crossplane, allowing you to manage cloud resources from the Kubernetes control plane, twisting things outside in (and creating utter confusion for those trying to create a sane architecture).
In this article, I will use the most top down approach (well, still depends what you consider up and down...):  Consider the basic Kubernetes services as infrastructure and configure them with terraform.  Consequently, the cluster A&A shall be configured using terraform with the kubernetes provider.

==Assumptions==
* You are familiar with kubernetes, terraform, AWS IAM, EKS and other services.
* Tools installed and configured: AWS cli, kubectl, terraform
* You have an EKS cluster and the configuration to connect to it using kubectl.

There are tons of resources elsewhere to help you with these and I would like to keep this article focussed.


