Duo Task

This exercise gets you to containerise a basic Flask application and use NGINX as a reverse proxy.

You should currently be able to:
Containerise the Flask application in this repository https://gitlab.com/qacdevops/duo-task
You will have to write a Dockerfile to build the image - a Dockerfile template has been provided for you
Create a network and connect the Flask app container to it.

You can try to:
Create an NGINX container to and connect it to the network:
You will need to either bind mount the nginx.conf file to /etc/nginx/nginx.conf on the container,
or create a custom NGINX image which copies the file there instead.
Navigate to your application either through your browser or on the command line with curl localhost