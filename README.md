# lambda-kms-encryption-decryption
encryption and decryption of environment variables with aws kms in lambda 

#In this function we are using serverless framework in aws lambda functions
https://serverless.com/framework/docs/providers/aws/cli-reference/create/

serverless create --template aws-nodejs 

#above command will create a nodejs lambda function 
#for encrypting keys we require a key in aws kms service with IAM role
#make sure to use same IAM role secret key and access key for lambda function to encrypt and decrypt
![image](https://user-images.githubusercontent.com/26525621/66699242-9d857f00-ed02-11e9-8d7c-c95aeb69544b.png)

#We have to use that key for encrypting of our environment variables in lambda functions

serverless encrypt -n MY_SECRETS1:database -v teststring -k <paste your key here>

#Above command will generate an yaml file with secret key
#We can update the key by using same command 
#second time we don't require key as a custom yaml file will be generated in your code


![image](https://user-images.githubusercontent.com/26525621/66699333-94e17880-ed03-11e9-8cfd-bbc986fe8805.png)

serverless encrypt -n MY_SECRETS1:database -v test 

#We can decrypt the key using 
serverless decrypt

![image](https://user-images.githubusercontent.com/26525621/66699354-c3f7ea00-ed03-11e9-8b27-70018bb17eaf.png)

#deploy the function with serverless command
serverless deploy
#Then we can test the app locally 
serverless invoke --function kmsEncryptionDecrytion


![image](https://user-images.githubusercontent.com/26525621/66699383-11745700-ed04-11e9-8ec0-84614af10ebe.png)

#Then we can remove the lambda using below command
serverless remove
