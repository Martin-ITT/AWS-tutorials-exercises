Build the image

Now we're ready to build the image

docker build -t my-image:latest .
You should see a similar output, which shows the contents of context directory within the image:

drwxr-xr-x    2 root     root          4096 Sep  7 00:59 .
drwxr-xr-x    1 root     root          4096 Sep  7 00:59 ..
-rwxr-xr-x    1 root     root           138 Sep  7 00:58 .dockerignore
-rwxr-xr-x    1 root     root           265 Sep  7 00:58 Dockerfile
-rwxr-xr-x    1 root     root             0 Sep  7 00:57 README.md
-rwxr-xr-x    1 root     root             0 Sep  7 00:57 app.py
Removing intermediate container 11efe999df76
 ---> c324763036ad
Successfully built c324763036ad
Successfully tagged my-image:latest


Remove the image:
docker rmi my-image alpine