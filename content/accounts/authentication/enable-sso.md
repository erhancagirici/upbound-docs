---
title: "Single Sign On in Upbound"
description: "Configure single sign-on in your Upbound organization to manage user access"
---

<!-- vale off -->
Upbound allows organizations to configure single sign-on (SSO) to manage user access. Administrators can secure access to organizational resources and manage permissions with SSO and Directory Sync. Upbound supports integration with your existing Identity Providers (IdPs) for a seamless login experience and Directory Sync for streamlined user management.
<!-- vale on -->

## Introduction

Upbound offers SSO and Directory Sync in a customized wizard setup. You can configure SSO only or add Directory Sync after you enable SSO.

<!-- vale off -->
### Single sign-on
<!-- vale on -->

SSO increases security and decreases common password or authentication problems. When a user attempts to log in to an application, the SSO workflow transparently redirects the authentication request to an already trusted identity provider. The Upbound implementation of SSO supports Security Assertion Markup Language (SAML) and OpenID Connect (OIDC) protocols to communicate between your IdP and Upbound.

<!-- vale off -->
If your organization requires SSO due to compliance or security restrictions, each time you integrate a new third party application, you must configure SSO in the new application.
<!-- vale on -->

### Directory sync

<!-- vale off -->
Directory sync adds the benefit of automatically updating users in third-party applications when your internal directory changes. For example, when you add the user to a directory like Microsoft AD, you can user Directory Sync to create a new user in your Upbound account. Another benefit of Directory Sync is offboarding. Directory Sync allows you to mitigate security risks by automatically deleting users from your Upbound account as soon as you deactivate or remove them from your directory. Directory Sync provides increased security and automatic user management from a centralized location.

If your organization wants to manage access through your Microsoft AD, Google Workspace, Okta, or other directory, you can configure Upbound to automatically sync user accounts.
<!-- vale on -->

## Prerequisites

Before you begin, reach out to [the Upbound support team](https://www.upbound.io/contact) to enable SSO in your organization.

To enable SSO, you need:

- An Upbound account with administrative permissions to the organization
- An existing Identity Provider (IdP) with administrative permissions to create the configuration

<!-- vale off -->
## Configure your identity provider for single sign-on
<!-- vale on -->

After contacting the support team for SSO access, Upbound sends link to configure your IdP with Upbound. You can use the predefined workflows for your specific IdP or create a custom SAML or OIDC connection.

<!-- vale off -->
### Enable single sign-on
<!-- vale on -->


Walk through the workflow in your provided link to enable SSO. The requirements differ for each IdP, but you may need:

- An IdP metadata XML file
- An IdP SSO link
- A signing certificate (X.509)

### Enable directory sync

After you enable SSO, walk through the workflow in your provided link to enable Directory Sync. You can choose from the predefined workflows for your directory or create a or SCIM connection. The requirements differ for each directory, but you may need:

- An API bearer token from your IdP

<!-- vale off -->
### Finalize your changes

After you enable SSO to your IdP and test the connection, contact Upbound support or your account representative to finalize the configuration. SSO will not be enabled until you contact Upbound to confirm the change.
<!-- vale on -->


## Considerations

When you enable SSO with Upbound, remember these important considerations:

<!-- vale off -->
- SSO can only be configured in a single Upbound organzation per domain
- Users in an SSO enabled organization must use SSO to log in
<- When you enable SSO, all outstanding invites will be destroyed
- When you enable SSO, all currently logged in users will be logged out to reauthenticate
<!-- vale on -->

## Next steps

SSO and Directory Sync in Upbound are effective ways to manage your user access.

For more information, contact the Upbound support team.