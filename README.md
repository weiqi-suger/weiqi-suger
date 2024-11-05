# OKTA SCIM

## Goal / Context:

Our clients want to change the roles of their employees only with Okta, not using Suger-console.

## SCIM implementation

to implement SCIM 2.0, we need to **provide** these APIs to **Okta**

- GET `/Users`                    Retrieve Users
- GET `/Users/{userID}`           Retrieve a specific User
- POST `/Users`                   Create the User
- PUT `/Users/{userID}`           Update the User
- PATCH `/Users/{userID}`         Update the User
- DELETE `/Users/{userID}`        Delete the User

- GET `/Groups`                   Retrieve Groups
- GET `/Groups/{groupID}`         Retrieve specific Groups
- POST `/Groups`                  Create Groups
- PUT `/Groups/{groupID}`         Update a specific Group
- PATCH `/Groups/{groupID}`       Update a specific Group
- DELETE `/Groups/{groupID}`      Delete a specific Group

See this guide: [Build your SCIM API service](https://developer.okta.com/docs/guides/scim-provisioning-integration-prepare/main/)

## Customer installation / configuration 

- We can first build a private SCIM integration for Customers to use.

> See this guide: [Add a private SCIM integration](https://developer.okta.com/docs/guides/scim-provisioning-integration-connect/main/#connect-to-your-scim-service)

> and this guide: [Test your private SCIM integration](https://developer.okta.com/docs/guides/scim-provisioning-integration-test/main/)

- We can also publish SCIM integrations to Okta. This makes it easier for Customers in install our integrations.

> For customers to use our SCIM provisioning integration with Okta, we need to publish it through the [Okta Integration Network](https://www.okta.com/integrations/)

> See this guide: [Publish an OIN integration](https://developer.okta.com/docs/guides/submit-app-overview/)

### Private integration limitation

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

