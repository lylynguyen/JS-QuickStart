# Set Up Docker

| Tech        | Info           |
|:------------- |:-------------|
| <img src="http://imgur.com/ezUeJxf.png"> | Docker is an open source tool to automate application deployment using 'containers' <br> * <em>Docker Containers wrap up a piece of software in a complete filesystem that contains everything it needs to run: code, runtime, system tools, system libraries – anything you can install on a server. This guarantees that it will always run the same, regardless of the environment it is running in.</em> |

> Set yourself up to use Docker from your local machine!

### Step 1

Download the [Docker Toolbox (48KB)](https://www.docker.com/products/docker-toolbox)
You’ll see several download options. Select the .pkg option for the install wizard.
To create a docker machine virtual machine:

`docker-machine create --driver virtualbox <name of vm, mine was 'temp', default is 'default'>`

(virtualbox is _probably_ already installed on your machine)

The provisioning of the new vm will take several seconds.

To start that machine (let’s assume it’s called ‘default’): `docker-machine  start default`

to manage that machine: `eval $(docker-machine env default)` (edited)
(note: ^ this is necessary for each new terminal tab/window)

to check what (top-level) images are available on docker (once the machine is running): `docker images`

to check _all_ images: `docker images -a` (edited)

to output only the shortened image hash: `docker images -q` (edited)

to check what containers are running on docker (once the machine is running): `docker ps`

to check _all_ containers (even stopped ones): `docker ps -a`

to output only the shortened container hash: `docker ps -q`

building an image (from _this_ directory, `.`): `docker build -t <some useful image name, or the repo/tag to which you will push> .`

to run that image (let’s call it `image1`), say with container port 80 attached to host's (your *docker*-machine’s) port 8081, with the name `container1`: `docker run -p 8081:80 --name container1 image1`

sorry, I made a mistake above;
since we’re running it on a vm, to actually access this, assuming container1 is running a webserver, we need to know the ip address of the vm; we can do this with either of the following commands):
`docker-machine ls` (will include the ip address)
`docker-machine ip default` (will only output the ip for the machine named `default`)

(e.g.:
```AMAC02QVD1EFVH5:hellowworld robert.glenn$ docker-machine ip temp
192.168.99.100
AMAC02QVD1EFVH5:hellowworld robert.glenn$ docker run -p 8081:80 hello-web
npm info it worked if it ends with ok
npm info using npm@3.10.8
npm info using node@v6.8.0
npm info lifecycle hellowworld@1.0.0~prestart: hellowworld@1.0.0
npm info lifecycle hellowworld@1.0.0~start: hellowworld@1.0.0

> hellowworld@1.0.0 start /code
> node server.js

Hello Liquid Studio app listening on 80```
so I would access this at http://192.168.99.100:8081)
