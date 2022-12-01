* create/update user with DynamoDBFullPermissions 
* run "aws configure" with user mentioned above
* create sample table
```
aws dynamodb create-table --table-name ProductCatalog --attribute-definitions \
AttributeName=Id,AttributeType=N --key-schema \
AttributeName=Id,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```
* populate table
```
aws dynamodb batch-write-item --request-items file://items.json
```
* Validate items loaded
```
aws dynamodb get-item --table-name ProductCatalog --region us-east-1  --key '{"Id":{"N":"403"}}'
```

