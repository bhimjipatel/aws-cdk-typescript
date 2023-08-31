# Amplify Console App

This an example of an Amplify Console App, triggering a build and deploy of a static site on every GitHub Repository master push.
This example requires a github repo containing a static website.

## Build

Before building this app, you must first edit `index.ts` with information on your particular repo.

To build this app, you need to be in this example's root folder. Then run the following:

```bash
npm install -g aws-cdk
npm install
npm run build
```

This will install the necessary CDK, then this example's dependencies, and then build your TypeScript files and your CloudFormation template.

## Deploy

Run `cdk deploy`. This will deploy / redeploy your Stack to your AWS Account.

After the deployment you will see the API's URL, which represents the url you can then use.

## The Component Structure

This Stack contains:

- an Amplify Console App resource, representing the Amplify Console App that you wish to build and deploy, you need to specify its name, the URL of the GitHub Repository and the OAuth token from GitHub, which will authorize Amplify Console to access the repository and listen to commits.
- an Amplify Console Branch resource, representing the branch, to which whenever you push code it will trigger a build of your app.
