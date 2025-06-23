# Trilium – Single-User Note-Taking Software

## Installing Trilium

With the structured note-taking app Trilium, you can organize your content in a tree-like hierarchy.
You can store text, images, code, to-do lists, and more – either locally or in the browser.
Trilium supports encryption, tags, links, versioning, and even scripting to make your content dynamic.

To install Trilium, we use a Git clone without dependencies. After downloading Trilium, we use the `cd` command to switch to the Trilium directory.

* git clone https://github.com/zadam/trilium.git     (Download Trilium)
* cd trilium                                         (Change into the directory)

## Installing Docker

Docker is a virtual machine that doesn't virtualize entire operating systems, but containers instead.
Containers are like boxes that hold the application, its configuration, and all dependencies.
That’s why we install Trilium without dependencies and use Docker to run it in a container.
We also enable Docker to start automatically:

* sudo apt install docker.io
* sudo systemctl start docker
* sudo systemctl enable docker

Then we create and start the Trilium container using docker run:

* sudo docker run -d -p 8080:8080 --name trilium zadam/trilium

You can change the **left** port if needed, e.g., from 8080:8080 to 8020:8080, in case you want to run multiple Trilium instances in parallel.

## If Trilium is not reachable:

* sudo docker start trilium          (Starts the Trilium container. Must be done after every VM reboot)
* sudo docker logs trilium           (Check who logged in)
* curl http://localhost:<port>       (Local test to see if the server is reachable – use the configured port)

## Accessing Trilium in the browser

http\://<your-VM-IP>:<configured-port>/setup

(You might need to add `/setup` manually if you’re not redirected automatically.)

## Note:
* `localhost` won’t work if Trilium is running inside a virtual machine accessed via SSH. In that case, “localhost” refers to the VM itself, not your PC.
* Access via HTTP does not constitute an encrypted connection. If you are using Trilium productively or on a network, you may need to set up a reverse proxy with HTTPS.
