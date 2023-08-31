# Api GatewayV2 websocket with lambda and dynamodb

This is the code for the simple-websocket-chat-app which is oringial from [simple-websockets-chat-app](https://github.com/aws-samples/simple-websockets-chat-app). There are three functions contained within the directories and wires them up to a DynamoDB table and provides the minimal set of permissions needed to run the app:
```
.
├── onconnect                   <-- Source code onconnect
├── ondisconnect                <-- Source code ondisconnect
└── sendmessage                 <-- Source code sendmessage
```
```"resolveJsonModule": true "esModuleInterop": true``` is added to `tsconfig.json` to support import jsonfile as header

## Build

To build this app, you need to be in this example's root folder. Then run the following:

```bash
npm install -g aws-cdk
npm install
npm run build
```

This will install the necessary CDK, then this example's dependencies, and then build your TypeScript files and your CloudFormation template.

## Deploy

Change `account_id` to your own aws account id in `config.json` file.

Run `cdk deploy`. This will deploy / redeploy your Stack to your AWS Account.

After the deployment you will see the API's URL, which represents the url you can then use.

## Synthesize Cloudformation Template

To see the Cloudformation template generated by the CDK, run `cdk synth`, then check the output file in the "cdk.out" directory.

## Testing the chat API

To test the WebSocket API, you can use [wscat](https://github.com/websockets/wscat), an open-source command line tool.

1. [Install NPM](https://www.npmjs.com/get-npm).
2. Install wscat:
``` bash
$ npm install -g wscat
```
3. On the console, connect to your published API endpoint by executing the following command:
``` bash
$ wscat -c wss://{YOUR-API-ID}.execute-api.{YOUR-REGION}.amazonaws.com/{STAGE}
```
4. To test the sendMessage function, send a JSON message like the following example. The Lambda function sends it back using the callback URL:
``` bash
$ wscat -c wss://{YOUR-API-ID}.execute-api.{YOUR-REGION}.amazonaws.com/prod
connected (press CTRL+C to quit)
> {"action":"sendmessage", "data":"hello world"}
< hello world
```