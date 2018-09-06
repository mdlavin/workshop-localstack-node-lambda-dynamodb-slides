## Prequisites

* Laptop
* Docker installed
* Code editor

---

## Workshop Goals

* Build a TODO API
* Working unit tests
* Local integration tests
* New skills

vvvvv

## Why Lambda and DynamoDB?

* 😌️ Both are low in complexity
* 💸 Both are nearly free
* 😒 They are both proprietary

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
* git clone https://github.com/mdlavin/workshop-localstack-node-lambda-dynamodb.git
* npm install
* npm test

vvvvv
## Assignment
* Add a delete Lambda handler
* Don't forget tests!
* You can cheat by looking at the `add-delete-handler` branch

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
* Trendy


vvvvv
## Limitations

* Not using security groups
* Not using IAM Policies

vvvvv
## Implemention

* Intro to docker-compose
* Show off npm build script
* Explain docker-compose.yml
* Explain integration testing approach

vvvvv
npm run-script integration-test

vvvvv
## Test failures!

An in-memory implementation of TODOs is bogus

vvvvv
## Assignment

* Implement a testcase for deleting a non-existent TODO
* You can cheat by looking at the `add-integration-test-for-delete` branch

---

## Adding DynamoDB to our function

Why do it?

vvvvv
## Short intro to DynamoDB programming model

vvvvv
## DynamoDB Table defininition

* Lambda function assumes tables exist

vvvvv
## Setup Lambda to store into DynamoDB

vvvvv
## Setup Lambda to fetch from DynamoDB

vvvvv
## Unit testing DynamoDB 

* aws-sdk-mock

---

## Adding DynamoDB integration tests

vvvvv
npm run-script integration-test

vvvvv
Explain LOCALSTACK_HOSTNAME
Explain table createion

vvvvv
Overriding DyanmoDB endpoints for hitting local dynamo