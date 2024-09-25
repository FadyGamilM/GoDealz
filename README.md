# GoPay
GoPay is a C2C platform that provides a seamless experience to buyers and sellers.

# Functional Requierments : 
- User can be a seller or a buyer 
- Seller can advertise producets and sale them 
- Buyer can purchase products
- we should have a transaction between c2c
- A specific percentage of the transaction will be hold for the application 
- We should have a notification system (email, sms)
- We should have an open channel (chatting or something) between the buyer and the seller 

# Backend Technologies
## Databases : 
I actually still didn't decide yet what should i use, I want to explore dynamodb and also i know that it will not scale with the different relationships and access patterns i will need in the future, so what i've decided is to start with postgres, and when i finish the entire microservices i will document the access-patterns i needed and will start migrate to mongo (just for the sake of exploration and having fun with different technology) 
- DynamoDB
    - So far we don't know exaclty the schema of the data models.
    - I need strong consistency and Dynamodb has 2 types of consistency : 
        - `Eventually Consistent (The Default)` and it gives us the latest written data after max 1-sec, but we might read some stale data if we read from the secondary-partition that replicates the data asynchronously.
        - `Strong Consistency` where we will always get the latest data when we read after write
        ![alt text](dynamo-replication-model.png)
    - It works very well with Lambda and almost all endpoints will be lambda functions because the entire backend will be serverless on AWS.

- Postgres 
    - Simple, powerfull relational database
    - scales very well
    - fits any future access pattern 
    - familiar with how i can use it as a database-per-service database 

