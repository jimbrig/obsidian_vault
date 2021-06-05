%%
ID: 5972284
Updated: 2020-10-24
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[Kubernetes Explained to Product Managers]]
Author: [[dev.to]]
Category: #articles
Number of Highlights: ==23==
Last Highlighted: *2020-10-22*
Readwise URL: https://readwise.io/bookreview/5972284
Source URL: https://dev.to/strio/kubernetes-explained-to-product-managers-4b1a


# Highlights 
containers, Docker, Kubernetes or clusters  ^103016501

---

some basic knowledge should allow you to collaborate more fluidly with your team, while being able to get an idea of the stakes, either because your company is considering migrating to Kubernetes, or because they already use this technology on a daily basis.  ^103016502

---

Why is everyone talking about Kubernetes?  ^103016503

---

Kubernetes is an open-source project initiated by Google, and launched in 2014. Google being praised for its high performing infrastructure and applications, an open-source project originating from the company is kind of a guarantee that it might be helpful to other organizations. Google has a tradition of open-source, with more than 2,000 projects launched to date. Some of them are particularly famous, like the Go language or Spinnaker (although launched by Netflix, it's been considerably extended by Google).  ^103016504

---

Today, Kubernetes is no longer managed by Google, as the company passed the project to the Cloud Native Computing Foundation, or CNCF, a non-profit organization hosting critical infrastructure projects.

Although launched only 6 years ago, Kubernetes is becoming a standard used by an increasing number of companies. 78% of companies using container orchestration have chosen Kubernetes, from tech companies, to large enterprises or rising startups. Think Google, Slack, The New York Times, BlaBlaCar or Huawei.  ^103016505

---

So what exactly is Kubernetes?  ^103016506

---

The name Kubernetes originates from Greek, meaning helmsman or pilot.  ^103016507

**Note: Kubernetes=“Helmsman or Pilot” in Greek. Look towards Latin, Greek, or other ancient languages for cool names!**

---

Kubernetes defines itself as "an open-source system for automating deployment, scaling, and management of containerized applications."  ^103016508

---

Since Kubernetes orchestrates containers, let's start by examining what containers actually are.

Containers have been made popular by an open-source project called Docker, created in 2013  ^103016509

---

Think of the container as a standardized unit of software. It is a way to package software into standardized units for Development, Shipment and Deployment.

You can imagine containers as same-sized boxes built around your code, which allow you to manipulate them much more easily than if the code was on its own, without any standard.

Thanks to this standardization, containers allow complex architecture to be managed much more easily.  ^103016510

---

A container is composed of several elements. To be precise, each container has its own filesystem, CPU, memory or process space. They are fully decoupled from the architecture, which allows them to be portable.  ^103016511

---

Containers are great but they must be managed and orchestrated. For example, if a container goes down, another container needs to start instead to avoid downtime on the app.

Instead of moving containers one by one, that's where orchestration tools such as Kubernetes comes in. Kubernetes is an orchestration tool, that takes care of the orchestration and scaling of containers. Without Kubernetes, containers would be handled by hand. As you can imagine, the more the containers the more the hand work, which is not compatible with the growth of an application.

Kubernetes runs these containers for you and therefore is your best ally when your application is scaling.  ^103016512

---

What makes K8S special?  ^103016513

---

Kubernetes runs containers at scale and have the following features:

Declarative: Declarative refers to a model where you don't have to specify and plan exactly how things will happen. Instead, you just state what your desired outcome is, without thinking at the way it is achieved. This allows Kubernetes users to forget about the complex details, to focus only on the outcome.
Automation: Thanks to this declarative mode, Kubernetes achieves automation. Rather than spending countless hours working on the details of containers orchestration, Kubernetes abstracts it for you.
Portable: Kubernetes can be used whatever the cloud provider or the kind of infrastructure used, which means it is portable.  ^103016514

---

Kubernetes can run anywhere. It is cloud agnostic and can run on virtual machines, which means there is no vendor lock-in  ^103016515

---

Kubernetes accompanies the scaling of applications and helps manage complex architectures and infrastructures  ^103016516

---

Kubernetes allows developers to be more productive  ^103016517

---

Kubernetes vocabulary  ^103016518

---

Basically, Kubernetes is made of clusters, nodes and pods.

When you deploy Kubernetes, you get a cluster.

Inside this cluster, you can find nodes.

You deploy pods on these nodes.  ^103016519

---

Cluster: It is a collection of hosts (servers) that helps you to aggregate their available resources. That includes ram, CPU, ram, disk, and their devices into a usable pool.  ^103016520

---

Nodes: Nodes are controlled by the control plane. Nodes are a virtual or physical machine. Nodes are the machinery needed to deploy pods.  ^103016521

---

Pods: Pods are the smallest units in Kubernetes. A pod is a group of one or more containers, with shared storage/network resources, and a specification for how to run the containers.  ^103016522

---

Want to go further? Here is a set of beginners resources about Kubernetes.

Kubernetes documentation
Why and when you should use Kubernetes
More about Kubernetes components
A Youtube Kubernetes tutorial for beginners
The illustrated children's guide to Kubernetes  ^103016523

