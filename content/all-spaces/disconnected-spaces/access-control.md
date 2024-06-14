---
title: Enable and configure access control
weight: 9
description: A tutorial for creating role-based access control in Upbound
---

{{< hint "important" >}}
For more information about Upbound's Space offerings, review [What is Upbound]({{<ref "what-is-upbound.md" >}}).
{{< /hint >}}


This guide introduces role-based access control (RBAC) in Upbound. RBAC allows
you to control access to your Upbound resources and control planes based on the
roles of individual users within your organization.

<!-- vale gitlab.SentenceLength = NO -->
Depending on your operational model, you can use [Upbound RBAC]({{<ref "all-spaces/spaces/access-control.md" >}}) (with Connected or Cloud Spaces) or Kubernetes Hub Authorization (Single-Tenant Connected or Disconnected Spaces) to manage your users access within Upbound or the underlying resources.
<!-- vale gitlab.SentenceLength = YES -->


## Identity types

Upbound supports the following identity types:

- [Users]({{<ref "accounts/users.md" >}}) - Accounts representing a single user.
- [Organizations]({{<ref "accounts/organizations.md" >}}) - A top-level collection of
  users and teams.
- [Teams]({{<ref "accounts/teams.md" >}}) - A sub-group within an organization.
- [Robots]({{<ref "accounts/robots.md" >}}) - Non-user accounts designed for
  automation.

Upbound constructs unique identities with `upbound:(user|robot|team):<name>`.

## Authentication

Upbound issues JSON Web Tokens (JWT) with identity information to
authenticate to your platform APIs.

The token includes:

- a subject (`upbound:user/team:<name>`)
- the users team memberships(`upbound:team:<UUID>`)
- the organization context(`upbound:org-role:(admin|member)`)

## Authorization

<!-- vale off -->
Upbound uses identities to check for authentication across the platform. In
the Cloud environment, Upbound grants identities organization roles to
control access to features and resources with IAM policies.
<!-- vale on -->


In Connected Spaces, you can bind identities to Kubernetes RBAC or
Upbound RBAC to control access to resources.

The subject and group claims in the JWT token determine the user's effective permissions for an API request.


## Enable Kubernetes hub authorization

To enable Kubernetes Hub Authentication in your Space, you need:

- a Kubernetes cluster with RBAC enabled
- to attach your cluster to Upbound

Users can authenticate to the single-tenant Connected Space with their Kubernetes
credentials with this method.

<!-- vale Microsoft.HeadingAcronyms = NO -->
### Configure Kubernetes RBAC
<!-- vale Microsoft.HeadingAcronyms = YES -->


To configure Kubernetes RBAC in your Disconnected Space, you need to create
`ClusterRoles` and `Roles` for defining access to your resources.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: upbound-user
rules:
- apiGroups: ["spaces.upbound.io"]
  resources: ["controlplanes"]
  verbs: ["get", "list", "watch"]

```

Next, create `ClusterRoleBindings` and `RoleBindings` to assign
roles to subjects like users, groups, or service accounts.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: controlplane-getters
subjects:
- kind: Group
  name: upbound:(user|robot):<username>
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: controlplane-getter
  apiGroup: rbac.authorization.k8s.io
```

The `subject` in this example can contain teams (`upbound:team:<uuid>`) or org roles (`upbound:org-role:admin|member`) depending on your role need.

This example creates an `controlplane-getter` with read permissions on
`controlplanes` and binds the users to the `upbound:users` group.
