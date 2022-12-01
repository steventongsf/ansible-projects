# Prerequisites
* Create or update IAM user to allow kms:Encrypt and kms:Decrypt
* Create a key in KMS. 
    * Key Type: SYNMMETRIC_DEFAULT
    * Assign key administrator
    * Assign key user

# Sample Commands
* _YOURKEYIDHERE_ is your customer managed key that you create or can access
* Enter the following with the user in created or mentioned in the prerequisites with the:
    * ACCESSKEYID
    * ACCESSKEY
    * REGION
```
aws configure
```

```
# encrypt secret.txt
aws kms encrypt --key-id YOURKEYIDHERE --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
```
```
# decrypt sencryptedsecret.txt
aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt
```
```
# re-encrypt encryptedsecret.txt
aws kms re-encrypt --destination-key-id YOURKEYIDHERE --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt 

```
```
# rotate key
aws kms enable-key-rotation --key-id YOURKEYIDHERE
```
```

aws kms get-key-rotation-status --key-id YOURKEYIDHERE
```
```
aws kms generate-data-key --key-id YOURKEYIDHERE --key-spec AES_256
```

