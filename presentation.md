## Prequisites

* Laptop
* Docker installed
* Node v8 installed
* Code editor
* Git tools

---

## Workshop Goals

* Build a TODO API
* Working unit tests
* LocalStack based integration tests
* Leave with new skills

vvvvv

## Workshop Schedule

1. Explain a new concept
2. Show-off a partial implementation
3. Assignment to complete the implementation
4. Repeat with a more advanced concept

"Move fast and break people"

vvvvv

## Why Lambda and DynamoDB?

* 😌️ Both are low in complexity
* 💸 Both are nearly free
* 😒 They are both proprietary

vvvvv

## Why LocalStack?

* Testing AWS APIs for free
* Testing AWS APIs without a network

vvvvv
## Details

* One function to list
* One function to add
* One function to delete
* No access control
* No authentication
* No client

---

## Building a Lambda function

vvvvv
## Lambda programming model

* Receive JSON events
* Generate JSON responses
* Don't worry about the OS
* Don't worry about scaling

vvvvv
## Event sources
 
* API Gateway
* Kinesis/SQS records
* DynamoDB updates
* Direct from clients _(that's us)_

vvvvv
## Shortcuts we'll take

* No persistent storage _(for now)_

vvvvv
## A Lambda to add TODOs

```bash
git clone https://github.com/mdlavin/workshop-localstack-node-lambda-dynamodb.git
git checkout implement-add-and-list
npm install
```

vvvvv
## Review add and list impls.

* Event handling in `src/lambda.js`
* "Storage" implemented in `src/database.js`
* Tests in `test/unit/lambda.test.js`

vvvvv
## Assignment

* Add a delete Lambda handler
* Don't forget tests!
* A solution is in the `add-delete-handler` branch
* Timeboxed to 20 min

---

# Integration testing of Lambda functions

vvvvv
## Aren't unit tests enough?

* Mistakes in packaging are easy
* Verify Webpack configuration changes

vvvvv
# How to test Lambda functions

* Deploy it darkly
* Test it pre-deploy

vvvvv
## Why local?

* Faster
* Cheaper
* Simpler


vvvvv
## Limitations

* Not using security groups
* Not using IAM Policies

vvvvv
## Localstack

* https://localstack.cloud/
* Open Source
* A 'mock' implementation of AWS APIs
* Perfect for development time and testing

vvvvv
## Docker-compose

* Multi-container configuration and launching
* Run DynamoDB, Lambdas and tests in separate containers


vvvvv
## Test code

* `git checkout add-integration-tests`
* Show off npm build script
* Explain `docker-compose.yml`

vvvvv
# Testcase walkthrough

* Lambda function creation
* Lambda function invocation
* `npm run-script integration-test`

vvvvv
## Test failures!

An in-memory implementation of TODOs is bogus

vvvvv
## Assignment

* Add a testcase for deleting a non-existent TODO
* Solution in the `add-integration-test-for-delete` branch

---

## Adding DynamoDB to our function

Why do it?

vvvvv
## Intro to DynamoDB model

* Tables
* Items
* Hash keys
* Range keys

vvvvv
## DynamoDB Table defininition

* `git checkout introduce-dynamodb-storage`
* Lambda function assumes tables exist
* Creation is handled at deploy time

vvvvv
## Walkthrough DynamoDB-based impl

Updates to add and list implemenations are in `src/database.js`

vvvvv
## New unit testing approach

* AWS DyanmoDB is now a dependency
* Have to assume that DynamoDB works correctly
* `aws-sdk-mock` to the rescue


vvvvv
## Assignment

* Add a delete implementation based on DynamoDB
* Implement unit tests
* Skip integation tests (for now)
* Cheat by looking at the `deletion-for-dynamodb` branch

---

## Adding DynamoDB integration tests

vvvvv

* `git checkout add-integration-tests-for-dynamodb`

vvvvv
## Fix integration testing

* Now that DynamoDB is used, the Lambda needs to to use LocalStack endpoint
* From `src/database.js`

```
const dynamoDbClient = new AWS.DynamoDB.DocumentClient({
  endpoint: process.env.LOCALSTACK_HOSTNAME
      ? `http://${process.env.LOCALSTACK_HOSTNAME}:4569/`
      : undefined
})
```

vvvvv
## Table creation

* Point to the code

vvvvv
## Assignment

* Add an integation test for delete implementation based on DynamoDB
* You can cheat by looking at the `add-integration-tests-for-dynamodb-delete` branch