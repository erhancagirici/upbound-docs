---
title: Control Plane Groups
weight: 2
description: An introduction to the Control Plane Groups in Upbound
---

In Upbound, Control Plane Groups (or just, 'groups') are a logical grouping of one or more control planes with shared resources like [secrets]({{<ref "all-spaces/spaces/secrets-management" >}}) or [backups]({{<ref "all-spaces/spaces/backup-and-restore" >}}). It's a mechanism for isolating these groups of resources within a single [Space]({{<ref "all-spaces" >}}). All role-based access control in Upbound happens at the control plane group-level.

## When to use multiple groups

You should use groups in environments where there's a need to have Crossplane manage infrastructure across multiple cloud accounts or projects. For users who only need to deploy and manage resources in a couple cloud accounts, you shouldn't need to think about groups at all.

Groups are a way to divide access in Upbound between multiple teams. Think of a group as being analogous to a Kubernetes _namespace_.

## The 'default' group

Every Cloud Space in Upbound has a group named _default_ available. 

## Working with groups

### View groups

You can list groups in a Space using:

```shell
up group list
```

If you're operating in a single-tenant Space and have access to the underlying cluster, you can list namespaces that have the group label:

```shell
kubectl get namespaces -l spaces.upbound.io/group=true
```

### Set the group for a request

Several commands in _up_ have a group context. To set the group for a request, use the `--group` flag:

```shell
up ctp list --group=team1
```
```shell
up ctp create new-ctp --group=team2
```

### Set the group preference

The _up_ CLI operates upon a single [Upbound context]({{<ref "reference/cli/contexts" >}}). Whatever context gets set is then used as the preference for other commands. An Upbound context is capable of pointing at a variety of altitudes:

1. A Space in Upbound
2. A group within a Space
3. a managed control plane within a group

To set the group preference, use `up ctx` to choose a group as your preferred Upbound context. For example:

```shell
# This sets the context for the up CLI to the default group in an Upbound-managed Cloud Space (gcp-us-west-1) for an organization called 'acmeco'
up ctx acmeco/upbound-gcp-us-west-1/default/
```

### Create a group

To create a group, login to Upbound and set your context to your desired Space:

```shell
up login
up ctx '<your-org>/<your-space>'
# Example: up ctx acmeco/upbound-gcp-us-west-1
```


Create a group:

```shell
up group create my-new-group
```

### Delete a group

To delete a group, login to Upbound and set your context to your desired Space:

```shell
up login
up ctx '<your-org>/<your-space>'
# Example: up ctx acmeco/upbound-gcp-us-west-1
```

Delete a group:

```shell
up group delete my-new-group
```

### Protected groups

Once a managed control plane gets created in a group, Upbound enforces a protection policy on the group. Upbound prevents accidental deletion of the group. To delete a group that has control planes in it, you should first delete all control planes in the group.

## Groups in the context of single-tenant Spaces

Upbound offers a variety of deployment models to use the product. If you deploy your own single-tenant Upbound Space (whether connected or disconnected), you're self-hosting Upbound software in a Kubernetes cluster. In these environments, a control plane group maps to a corresponding namespace in the cluster which hosts the Space.

Most Kubernetes clusters come with some set of predefined namespaces. Because a group maps to a corresponding Kubernetes namespace, whenever a group gets created, there too must be a Kubernetes namespace accordingly. When the Spaces software is newly installed, no groups exist. You _can_ elevate a Kubernetes namespace to become a group by doing the following:

1. Creating a group with the same name as a preexisting Kubernetes namespace
2. Creating a managed control plane in a preexisting Kubernetes namespace
3. Labeling a Kubernetes namespace with the label `spaces.upbound.io/group=true`