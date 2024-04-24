---
layout: section3
title: Section 3 - Setting Up the Frontend Tier
permalink: /section3/
---

<!-- Content for Docker section 3 -->

# Section 3 - Setting Up the Frontend Tier with React

In this section of the tutorial, we will set up the frontend tier using React.

## Step 1: Dockerfile for React Frontend

```dockerfile
# Use the official Node.js image as the base image for building React app
FROM node:latest as build

# Set container name with roll number
ENV REACT_CONTAINER_NAME="react-frontend-21bcp140"

# Create and set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy frontend source code
COPY . .

# Build React app
RUN npm run build

# Use NGINX for serving React app
FROM nginx:alpine

# Copy build files from build stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Command to start NGINX
CMD ["nginx", "-g", "daemon off;"]
```
![Image](/images/frontend-01.png)
## Step 2: Building and Running React Frontend Container
 ``` dockerfile
# Build the Docker image for React frontend
docker build -t react-frontend-21bcp140 .

# Run the React frontend container
docker run -d --name react-frontend-21bcp140 -p 80:80 --network my-network react-frontend-21bcp140
```

![Image](/images/frontend-02.png)


![Image](/images/frontend-03.png)


## Thank you for visiting the documentation