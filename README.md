# lambda-go
Simple lambda function using go


## TO RUN/BUILD APP

 ```sh
 To Build the app:  go build
 To run the application : need to setup aws and run the commands below
 ```
 ## Technical Dependencies:

* Requries an AWS account and aws-cli to be installed
* build the code and zip the file
* After logged into aws console. We need to carete a role for lambda : aws iam create-role --role-name lambda-ex --assume-role-policy-document file://iam_role_create_policy.json
* Attach a service role to the created role : aws iam attach-role-policy --role-name lambda-ex --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole
* Push and create the go function to lambda of aws user accountID : aws lambda create-function --function-name lambda-go --zip-file fileb://function.zip --handler main --runtime go1.x --role arn:aws:iam::{accountID}role/lambda-ex
* To invoke the lambda function : aws lambda invoke --function-name lambda-go --cli-binary-format raw-in-base64-out --payload file://input.json output.txt
