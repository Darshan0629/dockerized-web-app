---
layout: section2
title: Section 2 - Setting Up the Backend Tier
permalink: /section2/
---

<!-- Content for Docker section 2 -->

# Section 2 - Setting Up the Backend Tier with Node.js

In this section of the tutorial, we will set up the backend tier using Node.js.

## Step 1: Dockerfile for Node.js Backend

```dockerfile
# Use the official Node.js image as the base image
FROM node:latest

# Set container name with roll number
ENV NODE_CONTAINER_NAME="nodejs-backend-21bcp140"

# Create and set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy backend source code
COPY . .

# Expose port 5000
EXPOSE 5000

# Command to run the backend server
CMD ["node", "server.js"]
```

![Image](/images/backend-01.png)


## Step 2: Building and Running Node.js Backend Container

``` dockerfile
# Build the Docker image for Node.js backend
docker build -t nodejs-backend-21bcp140 .

# Run the Node.js backend container
docker run -d --name nodejs-backend-21bcp140 -p 5000:5000 --network my-network nodejs-backend-21bcp140
```
![Image](/images/backend-02.png)