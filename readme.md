# Running Auth0 Single Page Application SDK with Mock OIDC Provider.

To support use cases like Automated Testing, it may be useful to have a SPA using the Auth0 SDK authenticate with a mock OIDC server rather then an actual Auth0 tenant.

This sample demonstrates how that can be done with [oidc-provider](https://www.npmjs.com/package/oidc-provider). With this approach your application can be configured for testing without requiring any changes to code in the application.

## Pre-requisites

- [Register your SPA](https://auth0.com/docs/get-started/create-apps/single-page-web-apps) in Auth0 and implement login in your application per our [SPA quickstarts](https://auth0.com/docs/quickstart/spa).

- Update your application so that the SDK `useFormData` option is set to true when instantiating the SDK client when using the mock authorization server. By default, the client uses an `application/json` request body when calling the token endpoint. `oidc-provider` requires a request body of `application/x-www-form-urlencoded` while Auth0 supports both. This sample makes using `useFormData` configurable.

## Running this sample.

To run this sample:

- Create a copy of auth_config.sample named auth_config.json. This file is already configured to run against the mock server.
- Install dependencies with `npm install`
- Start sample app and quickstart with `npm start`

The application will run at http://localhost:3000 and the mock auth server at http://localhost:3001.

## Configuring the mock server

Applications, grants, and users can be configured for the mock server in `test\mockProvider.js`. By default, the server shows a consent screen but this can be [suppressed](https://github.com/panva/node-oidc-provider/blob/main/recipes/skip_consent.md).
