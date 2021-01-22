---
title: Sample Tutorial
description: This is a sample tutorial to guide user on creating his own tutorial in md.User should follow exact syntax given below to render in user guide
---

### Introduction

What is Ingress?
Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource.
Here is a simple example where an Ingress sends all its traffic to one Service:

An Ingress may be configured to give Services externally-reachable URLs, load balance traffic, terminate SSL / TLS, and offer name-based virtual hosting. An Ingress controller is responsible for fulfilling the Ingress, usually with a load balancer, though it may also configure your edge router or additional frontends to help handle the traffic.
An Ingress does not expose arbitrary ports or protocols. Exposing services other than HTTP and HTTPS to the internet typically uses a service of type Service.Type=NodePort or Service.Type=LoadBalancer.


Prerequisites:

You must have an Ingress controller to satisfy an Ingress. Only creating an Ingress resource has no effect.
You may need to deploy an Ingress controller such as ingress-nginx. You can choose from a number of Ingress controllers.
Ideally, all Ingress controllers should fit the reference specification. In reality, the various Ingress controllers operate slightly differently.


The Ingress resource:

Ingress resource example:

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: minimal-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - http:
      paths:
      - path: /testpath
        pathType: Prefix
        backend:
          service:
            name: test
            port:
              number: 80


As with all other Kubernetes resources, an Ingress needs apiVersion, kind, and metadata fields. The name of an Ingress object must be a valid DNS subdomain name. For general information about working with config files, see deploying applications, configuring containers, managing resources. Ingress frequently uses annotations to configure some options depending on the Ingress controller, an example of which is the rewrite-target annotation. Different Ingress controller support different annotations. Review the documentation for your choice of Ingress controller to learn which annotations are supported.
The Ingress spec has all the information needed to configure a load balancer or proxy server. Most importantly, it contains a list of rules matched against all incoming requests. Ingress resource only supports rules for directing HTTP(S) traffic.

Ingress rules:
 
Each HTTP rule contains the following information:


* An optional host. In this example, no host is specified, so the rule applies to all inbound HTTP traffic through the IP address specified. If a host is provided (for example, foo.bar.com), the rules apply to that host.
* A list of paths (for example, /testpath), each of which has an associated backend defined with a service.name and a service.port.name or service.port.number. Both the host and path must match the content of an incoming request before the load balancer directs traffic to the referenced Service.
* A backend is a combination of Service and port names as described in the Service doc or a custom resource backend by way of a CRD. HTTP (and HTTPS) requests to the Ingress that matches the host and path of the rule are sent to the listed backend.
A defaultBackend is often configured in an Ingress controller to service any requests that do not match a path in the spec.


Ingress class:

Ingresses can be implemented by different controllers, often with different configuration. Each Ingress should specify a class, a reference to an IngressClass resource that contains additional configuration including the name of the controller that should implement the class.

apiVersion: networking.k8s.io/v1
kind: IngressClass
metadata:
  name: external-lb
spec:
  controller: example.com/ingress-controller
  parameters:
    apiGroup: k8s.example.com
    kind: IngressParameters
    name: external-lb

IngressClass resources contain an optional parameters field. This can be used to reference additional configuration for this class.


Default IngressClass:

You can mark a particular IngressClass as default for your cluster. Setting the ingressclass.kubernetes.io/is-default-class annotation to true on an IngressClass resource will ensure that new Ingresses without an ingressClassName field specified will be assigned this default IngressClass.


Note: If you have more than one IngressClass marked as the default for your cluster, the admission controller prevents creating new Ingress objects that don't have an ingressClassName specified. You can resolve this by ensuring that at most 1 IngressClass is marked as default in your cluster.


Updating an Ingress:

To update an existing Ingress to add a new Host, you can update it by editing the resource:


### How to create and manage Ingress Controller 

User can define values as below which needs to be replaced dynamically during run time.

URL :  http://##DNS.IP##:30455

### Accordian 3 - Images

<rect style="color:blue;" rx="0" ry="0" x="-35.84375" y="-22" width="71.6875" height="44" ></rect>

![codestructure](_images/mvc-db-structure.png)

### Accordian 4 - UL - LI

Simple text to demonstrate ul li :
- list text 1.
- list text 2.
- list text 3.

### Accordian 5 - Commands

Open terminal tab from dashboard to execute any commands. 

One can execute them by clicking :

```execute
pwd
```

One can copy them by clicking :

```copy
ls -l
```