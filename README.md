# Load-Testing-with-APIGW-Lambda-MySQL
Load testing with API Gateway, Lambda and MySQL RDS instance

Here are the steps to create the setup for load testing.

1) Create an RDS instance for MySQL.
2) Get sample employees database from mysql.com or Github. Links are pvovided below. Import this database in the RDS instance database.
https://dev.mysql.com/doc/employee/en/
or
https://github.com/datacharmer/test_db
3) Create an API Gateway
4) Create a Lambda function and configure to use it with API Gateway. Lambda function fetches data from employees database by joining a few tables. You can find the .py file I used to create Lambda function in the this repo.
5) Use Postman to load test the setup by sending multiple requests per minute to API endpoint.
