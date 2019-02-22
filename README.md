[![Travis](https://img.shields.io/travis/lucasbastianik/clear-lambda-storage-serverless.svg?style=flat-square)](https://travis-ci.org/lucasbastianik/clear-lambda-storage-serverless)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

⚡ Serverless Clear Lambda code storage
=====================

Serverless function that clear Lambda code storage. This project is based on [epsagon/clear-lambda-storage](https://github.com/epsagon/clear-lambda-storage).

Motivation
----------

AWS limits the total code storage for Lambda functions to [75GB](https://docs.aws.amazon.com/lambda/latest/dg/limits.html#limits-list).

The main reason of reaching such size is because for every deployment of existing function, AWS stores the previous version ("qualifier").

Usually, when you reach that point, you want to remove old version.
This tool will help you to!


Setup
-----
```bash
npm i -g serverless
git clone https://github.com/lucasbastianik/clear-lambda-storage-serverless
cd clear-lambda-storage-serverless/
serverless deploy
```

Cron
-----
You can schedule this Lambda code storage clean to run every period you want like code above:

```yaml
functions:
  clear_lambda_storage:
    handler: handler.clear_lambda_storage
    memorySize: 128
    timeout: 120
    events:
      - schedule: cron(0 12 ? * SUN *) # Run every sunday at 12:00pm UTC
```
