# MATF-RVTECH-AWSCLOUD-2025

# Pokretanje (LocalStack)
```bash

cd final
docker-compose down -v
docker-compose up -d
sleep 5

npm install
npx serverless@3 deploy

API_ID=$(awslocal apigateway get-rest-apis --query 'items[0].id' --output text)
echo $API_ID

# Upisi API_ID u final/web/index.html:
# const API_ID = 'OVDE_NALEPI';

awslocal s3 sync ./web s3://punjaci-website

http://punjaci-website.s3-website.localhost.localstack.cloud:4566/