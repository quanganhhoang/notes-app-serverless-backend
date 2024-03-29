# Serverless Stack Tutorial Notes API

The corresponding Notes App Client is here:
[https://github.com/quanganhhoang/notes-app-frontend](https://github.com/quanganhhoang/notes-app-frontend)

A demo of the completed app can be seen [here](https://dsode8mw8sxg1.cloudfront.net/).

# Checkpoint updates

## [Checkpoint 4](submissions/checkpoint4)

- What was done?
  - Infrastructure as code with AWS CDK and Serverless Stack Toolkit
  - CI/CD with AWS CodePipeline including AWS CodeBuild
  - Monitoring and Debugging - techniques to save logs and alert developers for errors happening in prod such as:
    - Push backend logs to CloudWatch
    - An `ErrorBoundary` React component as a fallback to catch errors as it happens (and not when app crashes when re-rendering) and saves it with another service (e.g. [Sentry](https://sentry.io/welcome/))
  - AWS IAM roles/policies
  - AWS config yaml files for select services
- A screenshot of the terminal output of running `serverless deploy -v` in the "Deploy Your Serverless Infrastructure" section.
- A screenshot of the modified deployed app with the "Login" and "Signup" buttons.
- Link to the final deployed app [here](https://dsode8mw8sxg1.cloudfront.net/)
- Screenshot of AWS billing dashboard displaying costs so far

## [Checkpoint 3](submissions/checkpoint3)

- Progress: I have finished the tutorial up until `Domains and Hosting`. Notes app is deployed on AWS S3 and served with CloudFront.
- Checkpoint 3 progress screenshot(s)
- Checkpoint 3 AWS billing info screenshot
- At least 10 incremental commits in the commit history since checkpoint 2

## [Checkpoint 2](submissions/checkpoint2)

- Progress: same as checkpoint #1 ~ I have finished up until "Adding auth to a React app" of the serverless tutorial.
- Checkpoint 2 app progress screenshot(s)
- Checkpoint 2 AWS billing info screenshot
- Checkpoint 2 question answers
- At least 10 incremental commits in the commit history since checkpoint 1

## [Checkpoint 1](submissions/checkpoint1)

- Progress: I have finished up until "Adding auth to a React app" of the serverless tutorial.
- Screenshot of DynamoDB table
- Screenshot of list notes API endpoint
- Screenshot of AWS billing dashboard
- Working links to API endpoints
    - [GET/POST] https://cllwsrrf55.execute-api.us-west-2.amazonaws.com/prod/notes
    - [GET/PUT/DELETE] https://cllwsrrf55.execute-api.us-west-2.amazonaws.com/prod/notes/{id}

---
# Serverless Node.js Starter

A Serverless starter that adds ES6, TypeScript, serverless-offline, linting, environment variables, and unit test support. Part of the [Serverless Stack](http://serverless-stack.com) guide.

[Serverless Node.js Starter](https://github.com/AnomalyInnovations/serverless-nodejs-starter) uses the [serverless-bundle](https://github.com/AnomalyInnovations/serverless-bundle) plugin and the [serverless-offline](https://github.com/dherault/serverless-offline) plugin. It supports:

- **Generating optimized Lambda packages with Webpack**
- **Using ES6 or TypeScript in your handler functions**
- **Run API Gateway locally**
  - Use `serverless offline start`
- **Support for unit tests**
  - Run `npm test` to run your tests
- **Sourcemaps for proper error messages**
  - Error message show the correct line numbers
  - Works in production with CloudWatch
- **Lint your code with ESLint**
- **Add environment variables for your stages**
- **No need to manage Webpack or Babel configs**

---

### Demo

A demo version of this service is hosted on AWS - [`https://z6pv80ao4l.execute-api.us-east-1.amazonaws.com/dev/hello`](https://z6pv80ao4l.execute-api.us-east-1.amazonaws.com/dev/hello)

And here is the ES6 source behind it

``` javascript
export const hello = async (event, context) => {
  return {
    statusCode: 200,
    body: JSON.stringify({
      message: `Go Serverless v1.0! ${(await message({ time: 1, copy: 'Your function executed successfully!'}))}`,
      input: event,
    }),
  };
};

const message = ({ time, ...rest }) => new Promise((resolve, reject) =>
  setTimeout(() => {
    resolve(`${rest.copy} (with a delay)`);
  }, time * 1000)
);
```

### Upgrading from v1.x

We have detailed instructions on how to upgrade your app to the v2.0 of the starter if you were using v1.x before. [Read about it here](https://github.com/AnomalyInnovations/serverless-nodejs-starter/releases/tag/v2.0).

### Requirements

- [Install the Serverless Framework](https://serverless.com/framework/docs/providers/aws/guide/installation/)
- [Configure your AWS CLI](https://serverless.com/framework/docs/providers/aws/guide/credentials/)

### Installation

To create a new Serverless project.

``` bash
$ serverless install --url https://github.com/AnomalyInnovations/serverless-nodejs-starter --name my-project
```

Enter the new directory

``` bash
$ cd my-project
```

Install the Node.js packages

``` bash
$ npm install
```

### Usage

To run a function on your local

``` bash
$ serverless invoke local --function hello
```

To simulate API Gateway locally using [serverless-offline](https://github.com/dherault/serverless-offline)

``` bash
$ serverless offline start
```

Deploy your project

``` bash
$ serverless deploy
```

Deploy a single function

``` bash
$ serverless deploy function --function hello
```

#### Running Tests

Run your tests using

``` bash
$ npm test
```

We use Jest to run our tests. You can read more about setting up your tests [here](https://facebook.github.io/jest/docs/en/getting-started.html#content).

#### Environment Variables

To add environment variables to your project

1. Rename `env.example` to `.env`.
2. Add environment variables for your local stage to `.env`.
3. Uncomment `environment:` block in the `serverless.yml` and reference the environment variable as `${env:MY_ENV_VAR}`. Where `MY_ENV_VAR` is added to your `.env` file.
4. Make sure to not commit your `.env`.

#### TypeScript

If [serverless-bundle](https://github.com/AnomalyInnovations/serverless-bundle) detects a `tsconfig.json` in your service root, it'll compile it using TypeScript. We have a separate starter for TypeScript here, [**Serverless TypeScript Starter**](https://github.com/AnomalyInnovations/serverless-typescript-starter).

#### Linting

We use [ESLint](https://eslint.org) to lint your code via [serverless-bundle](https://github.com/AnomalyInnovations/serverless-bundle).

You can turn this off by adding the following to your `serverless.yml`.

``` yaml
custom:
  bundle:
    linting: false
```

To [override the default config](https://eslint.org/docs/user-guide/configuring), add a `.eslintrc.json` file. To ignore ESLint for specific files, add it to a `.eslintignore` file.

### Support

- Open a [new issue](https://github.com/AnomalyInnovations/serverless-nodejs-starter/issues/new) if you've found a bug or have some suggestions.
- Or submit a pull request!

---

This repo is maintained by [Anomaly Innovations](https://anoma.ly); makers of [Seed](https://seed.run) and [Serverless Stack](https://serverless-stack.com).
