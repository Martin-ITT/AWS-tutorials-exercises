Build the Image
Create the image by executing:

docker build -t spring-hello-world .
Run the Container
Start the container by executing:

docker run -d -p 8080:8080 --name spring-app spring-hello-world
Run curl localhost:8080 to view the output from the webserver. It should look like this:

<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <title>Java Spring Boot Server</title>
</head>
<body>
    Hello from Docker
</body>
</html>

Clean Up
Stop the container:

docker stop spring-app
Remove container:

docker rm spring-app
Remove the images (enter y when prompted):

docker system prune -a