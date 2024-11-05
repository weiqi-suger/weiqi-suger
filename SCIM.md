# OKTA SCIM

tl;dr: we need to build SCIM + (OIDC and/or SAML)

## Goal / Context:

Our clients want to change the roles of their employees only with Okta, not using Suger-console.

## SCIM implementation

Guide: [Build your SCIM API service](https://developer.okta.com/docs/guides/scim-provisioning-integration-prepare/main/)

to implement SCIM 2.0, we need to **provide** these APIs to **Okta**:

<details>
<summary>
API list
</summary>

- GET `/Users` Retrieve Users
- GET `/Users/{userID}` Retrieve a specific User
- POST `/Users` Create the User
- PUT `/Users/{userID}` Update the User
- PATCH `/Users/{userID}` Update the User
- DELETE `/Users/{userID}` Delete the User

- GET `/Groups` Retrieve Groups
- GET `/Groups/{groupID}` Retrieve specific Groups
- POST `/Groups` Create Groups
- PUT `/Groups/{groupID}` Update a specific Group
- PATCH `/Groups/{groupID}` Update a specific Group
- DELETE `/Groups/{groupID}` Delete a specific Group

</details>

### packages we could use

- https://github.com/elimity-com/scim
- https://github.com/imulab/go-scim

## Customer installation / configuration

- We can first build a private SCIM integration for Customers to use.

  - This is how customers use our SCIM integration: [Add a private SCIM integration](https://developer.okta.com/docs/guides/scim-provisioning-integration-connect/main/#connect-to-your-scim-service)

- We can also publish SCIM integrations to [Okta Integration Network](https://www.okta.com/integrations/). This makes it easier for Customers in install our integrations.

  - See this guide: [Publish an OIN integration](https://developer.okta.com/docs/guides/submit-app-overview/)

<details>

<summary>Private integration limitation</summary>

> A key limitation of a private Okta SCIM integration is that it cannot be readily shared with other Okta customers as it is not listed in the Okta Integration Network (OIN), meaning you cannot benefit from the pre-built integration features and quality assurance checks available for public integrations; you will need to manage all aspects of the integration and its functionality entirely within your own Okta organization.

Other potential limitations of a private SCIM integration with Okta may include:

- Limited feature set:
  Some advanced features or specific attribute mappings might not be available in a private integration compared to a public one.
- Development overhead:
  You need to build and maintain the entire SCIM interface yourself, including error handling and data validation.
- Testing complexity:
  Testing and troubleshooting a private integration can be more challenging as you lack the built-in testing tools available for public integrations.
- No community support:
  If you encounter issues, you may not have access to the same level of community support available for public integrations.

</details>

## SSO

From [overview doc](https://developer.okta.com/docs/guides/scim-provisioning-integration-overview/main/): 
> Your Okta integration should use Single Sign-On (SSO) to initiate end user authentication. Learn how to set up your integration with SSO in our [Build a Single Sign-On (SSO) integration](https://developer.okta.com/docs/guides/build-sso-integration/) guide.

Like SCIM, we can either let customers use a private SSO integration, or pushlish it.

### OIDC or SAML ?

For new app integrations, OIDC is recommended. see [doc](https://developer.okta.com/docs/guides/oin-sso-overview/#choose-your-sso-protocol)

However, if our customers are already using SAML, we'd better provide that too.

- OIDC: https://github.com/coreos/go-oidc
- SAML: https://github.com/crewjam/saml
