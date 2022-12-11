Trio Task

This exercise gets you to run a Flask application container, a MySQL container and
an NGINX container in a network.

You should currently be able to:
Containerise the MySQL database and the Flask application in this repository https://gitlab.com/qacdevops/trio-task
You will have to write the Dockerfile to build the images - a Dockerfile template has been provided for both images
Look up the MySQL 5.7 image documentation on Docker Hub to learn how to configure the database
Create a network and connect the Flask application container, database container

You can try to:
Create an NGINX container to and connect it to the network:
You will need to either bind mount the nginx.conf file to /etc/nginx/nginx.conf on the container, or create a custom NGINX image which copys the file there instead.
Navigate to your application either through your browser or on the command line with curl localhost