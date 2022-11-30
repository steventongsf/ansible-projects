to set up authenticated access to AWS, 
* create an IAM user
* assign permissions
* generate key id and access key
* copy credentials file to ~/.aws/ on the machine you are running ansible on and substitute the placeholders in the file.  See below for template

```
~/.aws/credentials 
[default] 
aws_access_key_id = [your key id] 
aws_secret_access_key = [your access key]
region = [your aws region]
```

