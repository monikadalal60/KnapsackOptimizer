# KnapsackOptimizer
Service to provide solution for knapsack problem

# Service Endpoints
1. CreateKnapsack can be accessed by https://localhost:*/knapsack
2. GetKnapsack can be accessed by https://localhost:*/knapsack/id

# Architecture
1. ASP.Net Core 3.1 for Web API
2. Layers consists of Controllers, Business, Models
3. NUnit Test project for unit testing.
4. Docker to contain and host KnapsackOptimizer project.

# Testing 
1. Launch the application using Docker listening to an endpoint (Replace * with localhost port).
2. Send request through postman in following order

a. Post Request 
  https://localhost:*/knapsack
  body: {"problem": {"capacity": 60, "weights": [10, 20, 33], "values": [10, 3, 30]}}
  
  This will create a knapsack with randomly generated alphanumeric task. (length 8)
  The generated knapsack will be stored in dictionary created in Knapsack singleton.
  Returns knapsack object with status as "Submitted" and Solution as null.
  
  b. Get Request
  https://localhost:*/knapsack/{{task}}
  
  Send Get request with task that has been returned by the Post request.
  This will update the status of request as "Started" and returns Solution as null.
  
  Send the Get request again with same task.
  Now if the processing has been completed it will return status as "Completed" and returns the Solution to the problem provided.
  
  # Shortcuts 
  1. Dependency injection to map the business layer and provide loosely coupled architecture.
  2. Singleton class having dictionary to store task and knapsack object in absence of database which stores all the knapsacks till the applicaion lifetime.
