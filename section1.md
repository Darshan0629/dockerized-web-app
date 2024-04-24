---
layout: section1
title: Section 1 - Setting Up the Database Tier
permalink: /section1/
---

<!-- Content for Docker section 1 -->

# Section 1 - Setting Up the Database Tier with MongoDB

In this section of the tutorial, we will set up the database tier using MongoDB.

## Step 1: Dockerfile for MongoDB

```dockerfile
# Use the official MongoDB image as the base image
FROM mongo:latest

# Set container name with roll number
ENV MONGO_CONTAINER_NAME="mongodb-21bcp140"
```

![Image](/images/mongo-01.png)

## Step 2: building and running the database

```dockerfile
# Build the Docker image for MongoDB
docker build -t mongodb-21bcp140 .

# Run the MongoDB container
docker run -d --name mongodb-21bcp140 -p 27017:27017 mongodb-21bcp140

```
![Image](/images/mongo-02.png)



## Step 3: Connecting MongoDB Container to Network
```dockerfile
# Create a Docker network
docker network create my-network

# Connect MongoDB container to the network
docker network connect my-network mongodb-21bcp140
```

![Image](/images/mongo-03.png)
