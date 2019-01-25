This example demonstrates how to use [Express](http://expressjs.com/) 4.x and
[Passport](http://passportjs.org/) to authenticate users using a username and
password with [form-based authentication](https://en.wikipedia.org/wiki/HTTP%2BHTML_form-based_authentication).  Example modified to be deployed to an [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) serverless app and environment on [AWS Cloud](https://aws.amazon.com/) hosting.
Use this example as a starting point for your own web applications.

## Instructions

### Prerequisites:
You must have the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) and the [EB CLI](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html) installed.

To install this example on AWS Elastic Beanstalk, clone the repository to your local environment and install
dependencies.

```bash
$ git clone git@github.com:passport/express-4.x-local-example.git
$ cd express-4.x-local-example
$ npm install
```

### 1. Create an IAM user to handle deployments:
Login to AWS console and open the IAM console. Select the Users option on the left side menu.  Select "Add user" and enter a username to manage your Elastic Beanstalk apps and environments.  Define permissions for the new user. Always restrict as much as possible for the permissions.  This example app only needs EB deploy capabilities.  Create a new Group called eb-full-access and assign that group to the new user.  When creating the Group Filter for "Policy type" then search for AWSElasticBeanstalkFullAccess and assign the AWS IAM Group Full Access permission to Elastic Beanstalk.  Select the rest of the default settings to create the AWS IAM Group.

Using the AWS CLI tool aws configure, configure the new profile with the AWS IAM username.
```bash
$ aws configure --profile name_of_new_user
```

Execute the following command from the project's root directory.
```bash
$ eb init --profile name_of_new_user
```
You will need to enter the "AWS Access Key ID" and "AWS Secrete Key" from the AWS IAM console.

### 2. Create an EB app and environment and deploy the Express Passport.JS Express local example app to Elastic Beanstalk.
```bash
$ eb create
```

### Future modifications can be redeployed with the following EB CLI command.
```bash
$ eb deploy
```

Open a web browser and navigate to your Elastic Beanstalk URL to see the example in action.  Log in using username `jack` and password `secret`.
