# Homework 10 - Docker

### Task 1
1. Install docker
2. Prepare a dockerfile based on Apache or Nginx image
3. Added your own index.html page with your name and surname to the docker image
4. Run the docker container at port 8080
5. Open page in Web Browser
6. Report save in GitHub repository

Steps:

* create Dockerfile:
> ```
> FROM nginx:1.23.3-alpine
> COPY site-nginx /usr/share/nginx/html/
> CMD ["nginx", "-g", "daemon off;"]

* to build docker image with Dockerfile in current directory:

> `docker build -t test2 .`

<img width="1241" alt="Screenshot 2023-01-26 at 21 52 19" src="https://user-images.githubusercontent.com/117667360/214943283-9ddb3414-fa5a-4b93-9859-5c7111d62c67.png">

* to run docker containter with port 8080:

> `docker run -d -p 8080:80 1c2da2338549`

<img width="654" alt="image" src="https://user-images.githubusercontent.com/117667360/214944309-1f0614a8-22d7-4483-84af-e8fbfb4c9618.png">

---------------------------------

### Task 2
1. Prepare private and public network
2. Prepare one dockerfile based on ubuntu with the ping command
3. One container must have access to the private and public networks the second container
must be in the private network
4. A ) Run a container that has access to the public network and ping some resources (
example: google.com )
B ) The second container ping the first container via a private network
5. Report save in GitHub repository

* to create private and public network:
> ``
> `docker network create public`
> `docker network create private --internal`

* Dockerfile:
> ```
> FROM ubuntu:latest
> RUN apt-get update && apt-get install -y iputils-ping 

* to run two containers, one with private and public networks, second only with private network:
> `docker run -d --name priv-app --network private tast2:latest`
> `docker run -d --name pub-app --network public tast2:latest`







