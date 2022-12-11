Create a New Bridge Network
We are doing to create a bridge network to allow our application and NGINX container to connect to one another.

docker network create my-network
Create an Application Container
We are going to run a simple Python-based HTTP server container that is based on the image bobcrutchley/python-http-server:latest. We're going to give the container the name server and we connect it to our new network with the --network flag.

docker run -d --network my-network --name server bobcrutchley/python-http-server:latest
Create an NGINX Container
Run the following command to create an NGINX container with custom configuration and connect it to our network:

docker run -d --network my-network -p 80:80 --name nginx lukebenson1/docker-networking-nginx:latest
NGINX is a popular web server tool.
It has many uses, but we'll be using it as a reverse proxy.
Below is the configuration used by the NGINX container we just created:

events {}
http {
    server {
        listen 80;
        location / {
            proxy_pass http://server:9000;
        }
    }
}
Without needing to understand NGINX a great deal we can see that proxy_pass is referring to the Python server container by its name server, not an IP address.

The Python server we are using listens for traffic on port 9000, so we also need to include this in the proxy pass.

This name server will be resolved to the current IP address of the server container.

Access the Application
You can now access your application one of two ways.

You can use the command curl localhost on your command line interface. You should see the following output:

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Python: Simple HTTP Server</title>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
  </head>
  <body>
    <h3>Python: Simple HTTP Server</h3>
    <div>
        <div id="info"></div>
    </div>
      <script>
        
        $.getJSON("info.json", function (info) {
            let host_name = `<p>hostname: ${info.host_name}</p>`
            let version = `<p>version: ${info.version}</p>`
            $('#info').html(host_name + version)
        });
        
      </script>
  </body>
</html>

Or you can navigate to your VM's external IP address via your browser. You should see something like this:

Python: Simple HTTP Server
hostname: 4d4d4c931e52
version: 1

When you connect to your application, traffic is going through NGINX first, it is then routed to your deployed
application even though they are in separate containers.
This made possible because both the containers are on the same bridge network.

Clean Up
Stop the containers by executing:
docker rm -f server nginx

Remove images by executing:
docker rmi lukebenson1/docker-networking-nginx:latest bobcrutchley/python-http-server:latest