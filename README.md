# Load Testing RDS Database with API Gateway, Lambda and Postman
If you have scalable compute on AWS, its important to know how many requests your RDS database can handle as it can't scale automatically. These steps will help you  load test your RDS instance with API Gateway, Lambda and Postman.

Here are the steps to create the setup for load testing.

1) Create an RDS instance for MySQL.
   
2) Get sample employees database from mysql.com or Github. Links are pvovided below. Import this database in the RDS instance database.
https://dev.mysql.com/doc/employee/en/
or
https://github.com/datacharmer/test_db
3) Create an API Gateway API with Lambda function integration. Below is a screenshot of how it looks like.
   <img width="1117" height="467" alt="APIGW-Lambda-Integration" src="https://github.com/user-attachments/assets/fa2e9798-fe5d-43ad-bb25-755747794b34" />

4) Create a Lambda function and configure to use it with API Gateway. Lambda function fetches data from employees database by joining a few tables. You can find the .py file I used to create Lambda function in the this repo.
   
5) Use Postman to load test the setup by sending multiple requests per minute to API endpoint. Below screenshot shows load test report with ramp up from 3 users to 15 users in 5 minutes.
   <img width="1920" height="1080" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/814642d9-4c4e-4e5d-a307-deda3e3eade0" />

   Following screenshot shows CPU utilization of RDS going up when we did the load test.
   <img width="1763" height="836" alt="Screenshot 2025-07-19 125814" src="https://github.com/user-attachments/assets/b266c391-33b9-4c6e-a654-b76c4e1d3405" />

This way, you will know how many requests your RDS instance can handle. You can tweak your RDS instance size according to traffic you expect. 

There are other ways you can handle more requests without increasing the RDS instance size. You can also optimize database queries so that they consume less resouces and time to get output. You can use in-memory cashing to cache less frequently updated data. You can get this data directly from cache and hence reducing requests to database. 

