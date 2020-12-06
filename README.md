## Deploy CloudFormation

```
aws cloudformation create-stack --stack-name mac-cft-lambda-cognito --template-body file://cloudformation.yaml

aws cloudformation update-stack --stack-name mac-cft-lambda-cognito --template-body file://cloudformation.yaml
```

*After run CFT, must click save in `User Pool > App clients to avoid` `{"error":"invalid_grant"}` when `call /oauth2/token`* 

## Get token
```
curl -X POST --user {CLIENT_ID}:{CLIENT_SECRET} '{COGNITO_DOMAIN}/oauth2/token?grant_type=client_credentials&scope={SCOPE}' -H 'Content-Type: application/x-www-form-urlencoded'
```

## Call API
```
curl -H "Authorization: {TOKEN}" {API_ENDPOINT}/HelloWorld
```

## Reference 
* https://docs.aws.amazon.com/cognito/latest/developerguide/token-endpoint.html
