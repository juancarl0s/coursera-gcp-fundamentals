# Introduction

- Cloud Computing
  - First, you get computing resources on-demand and self-service,with no need for human intervention.
  - You access these resources over the net from anywhere you want.
  - The provider of those resources has a big pool of them and allocates them to customers out of that pool.
  - Resources are elastic. If you need more resources you can get more. If you need less, you can scale back.
  - Customers pay only for what they use or reserve as they go.

- Virtualization lets us all use resources more efficiently and be more flexible

- **IaaS** offerings provide raw compute, storage, and network organized in ways that are familiar from data centers.
- **PaaS** offerings, bind application code you write to libraries that give access to the infrastructure your application needs

- GCP Zones: think of a zone as a single failure domain within a region (independent geographic areas). As part of
building a fault tolerant application, you can spread their resources across multiple zones in a region.
  - Several zones withing a region -> Beter fault tolerance
  - Several regios -> be closer to users around world, improved fault tolerance

- Fine-grain billing (per second): big cost savings for workloads that are bursty
- Compute Engine offers automatically applied sustained use discounts which are automatic discounts that you get for running
a virtual machine instance for a significant portion of the billing month.

- GPC uses open APIs, open-source APIs to avoid vendor locking (into GCP)

- Multi-layered security approach:
  - Server boards and the networking equipment in Google data centers are custom designed by Google. 
  Google also designs custom chips, including a hardware security chip called Titan that's currently
  being deployed on both servers and peripherals.
  - Google server machines use cryptographic signatures to make sure they are booting the correct software.
  - Google designs and builds its own data centers which incorporate multiple layers of physical security protections.
  - Access to these data centers is limited to only a very small fraction of Google employees, not including me.
Google's infrastructure provides cryptographic privacy and
integrity for remote procedure called data-on-the-network,
which is how Google services communicate with each other.
The infrastructure automatically encrypts our PC traffic in transit between data centers.
Google Central Identity Service, which usually manifests to end users as
the Google log-in page, goes beyond asking for a simple username and password.
It also intelligently challenges users for additional information based on
risk factors such as whether they have logged in
from the same device or a similar location in the past.
Users can also use second factors when signing in,
including devices based on the universal second factor U2F open standard

- GCP has budgets and alerts;  billing, export, reports and quotas (rate and allocation).

- Projects are the main way you organize the resources you use in GCP
 - Projects can have folders in them, which can contain other folders

- You use Google Cloud Identity, and Access Management, also called IM, or IAM to control who can do what.
  - Principle of least privilege: each user should have only those privileges needed to do their jobs.
  In a least-privilege environment, people are protected from an entire class of errors.


# Resource hirearchy
- Resources are organized within projecs
- Projects, folders and organization nodes are all places where the policies can be defined
- Some GCP resources let you put policies on individual resources too
- Policies are inherited downwards in its hirearchy

## Projects
- Has a permanent project ID and number, can also add a name
- Projects can be organized into folders
  - Folders can contain other folders
  - Folders let teams have the ability to delegate administrative rights,
so they can work independently
  - Resources in a folder inherit IAM policies from the folder

## Organization node
- All projects and folders by an organization can be brought together under an organization node
- Centralized visibility on how resources are being used and to apply policy centrally
  - IE: you can assign a project creator role, which is a great way to control who can spend money
- If you have a G Suite domain, GCP projects will automatically belong to your organization node.
Otherwise, you can use Google Cloud Identity to create one

Note: Resources inherit the policies of their parent resource. For instance, if you set a policy at the organization level,
it is automatically inherited by all its children projects. And this inheritance is transitive, which means
that all the resources in those projects inherit the policy too. There's one important rule to keep in mind.
The policies implemented at a higher level in this hierarchy can't take away access that's granted at a lower level


# Identity and Access Management (IAM)

![](images/iam.png?raw=true)

## Who part
Defined either by a Google account, Google group, Service account, an entire G Suite, or a Cloud Identity domain.
## Can do what part
Defined by an IAM role, an IAM role is a collection of permissions

## Kinds of roles in Cloud IAM
 - **Primitive roles** are broad. You apply them to a GCP project and they affect all resources in that project.
    - Viewer: can examine resource but not change its state
    - Editor: everything a viewer can do, plus change its state
    - Owner: everything an editor can do, manage roles and permissions on the resource, set up billing 
- **Predefined roles** set of offered roles can be applies to resources in a given project, a given folder,
or in an entire organization
- **InstanceAdmin** Role allows to perform a certain set of actions on virtual machines (listing them,
reading and changing their configurations, and starting and stopping them)
- **Custom roles**
  - You'll need to manage their permissions
  - Custom roles can only be used at the project or organization levels. They can't be used at the folder level
- **Service accounts** are named with an email address. But instead of passwords, they use cryptographic keys to access resources
  - Service account has been granted Compute Engine's InstanceAdmin Role
  - Service accounts need to be managed, too
  - In addition to being an identity, a service account is also a resource. So it can have IAM policies on its own attached to it
    - For instance, Alice can have an editor role in a service account and Bob can have the viewer role (just like granting roles for any other GCP resource)


# Interacting with Google Cloud Platform
Console, SDK, Cloud Shell, Mobile App, APIs

## Console
Web-based interface to view and manage all your projects and all resources used.
- Lets you enable, disable and explore APIs of GCP services.
- Gives you access to Cloud Shell.
That's a command-line interface to GCP that's .
From Cloud Shell, you can use the tools provided by
the Google Cloud Software Development kit
SDK, without having to first install them somewhere

## SDK
Set of tools to manage resources and applications, allows access to `gcloud` and `gsutil`

## Cloud Shell
CLI to use the SDK without having to first install them somewhere


# Cloud Marketplace (formerly Cloud Launcher)
Tool for quickly deploying software packages (no need to manually configure the software,
virtual machine instances, storage or network settings). Some Cloud Launcher images charge users fees,
particularly those published by third parties with commercially licensed software. GCP updates the base images for
these software packages to fix critical issues and vulnerabilities. But it doesn't update the software after
it's been deployed; you'll have to do that manually