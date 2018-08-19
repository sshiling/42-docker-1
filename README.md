# 42-docker-1
## Docker. The bases to understand the idea of containerization of services.

The aim of the Docker-1 project is to make you handle docker and docker-machine, the bases to understand the idea of containerization of services.

## How To Docker
1. Create a virtual machine with docker-machine using the virtualbox driver, and named Char. <br>
2. Get the IP address of the Char virtual machine. <br>
3. Define the variables needed by your virtual machine Char in the general env of your terminal, so that you can run the docker ps command without errors. You have to fix all four environment variables with one command, and you are not allowed to use your shell’s builtin to set these variables by hand. <br>
4. Get the hello-world container from the Docker Hub, where it’s available. <br>
5. Launch the hello-world container, and make sure that it prints its welcome message,
then leaves it. <br>
6. Launch an nginx container, available on Docker Hub, as a background task. It
should be named overlord, be able to restart on its own, and have its 80 port
attached to the 5000 port of Char. You can check that your container functions
properly by visiting
http://<ip-de-char>:5000 on your web browser. <br>
7. Get the internal IP address of the overlord container without starting its shell and
in one command. <br>
8. Launch a shell from an alpine container, and make sure that you can interact
directly with the container via your terminal, and that the container deletes itself
once the shell’s execution is done. <br>
9. From the shell of a debian container, install via the container’s package manager
everything you need to compile C source code and push it onto a git repo (of
course, make sure before that the package manager and the packages already in the
container are updated). For this exercise, you should only specify the commands
to be run directly in the container. <br>
10. Create a volume named hatchery. <br>
11. List all the Docker volumes created on the machine. Remember. VOLUMES. <br>
12. Launch a mysql container as a background task. It should be able to restart on its
own in case of error, and the root password of the database should be Kerrigan.
You will also make sure that the database is stored in the hatchery volume, that
the container directly creates a database named zerglings, and that the container
itself is named spawning-pool. <br>
13. Print the environment variables of the spawning-pool container in one command,
to be sure that you have configured your container properly. <br>
14. Launch a wordpress container as a background task, just for fun. The container
should be named lair, its 80 port should be bound to the 8080 port of the virtual
machine, and it should be able to use the spawning-pool container as a database
service. You can try to access lair on your machine via a web browser, with the
IP address of the virtual machine as a URL. <br>
Congratulations, you just deployed a functional Wordpress website in two commands!
15. Launch a phpmyadmin container as a background task. It should be named roach-warden,
its 80 port should be bound to the 8081 port of the virtual machine and it should
be able to explore the database stored in the spawning-pool container. <br>
16. Look up the spawning-pool container’s logs in real time without running its shell. <br>
17. Display all the currently active containers on the Char virtual machine. <br>
18. Relaunch the overlord container. <br>
19. Launch a container name Abathur. It will be a Python container, 2-slim version,
its /root folder will be bound to a HOME folder on your host, and its 3000 port
will be bound to the 3000 port of your virtual machine.
You will personalize this container so that you can use the Flask micro-framework
in its latest version. You will make sure that an html page displaying "Hello World"
with h1 tags can be served by Flask. You will test that your container is
properly set up by accessing, via curl or a web browser, the IP address of your
virtual machine on the 3000 port.
You will also list all the necessary commands in your repository. <br>
20. Create a local swarm, the Char virtual machine should be its manager. <br>
21. Create another virtual machine with docker-machine using the virtualbox driver,
and name it Aiur. <br>
22. Turn Aiur into a slave of the local swarm in which Char is leader (the command to
take control of Aiur is not requested). <br>
23. Create an overlay-type internal network that you will name overmind. <br>
24. Launch a rabbitmq SERVICE that will be named orbital-command. You should
define a specific user and password for the RabbitMQ service, they can be whatever
you want. This service will be on the overmind network. <br>
25. List all the services of the local swarm. <br>
26. Launch a 42school/engineering-bay service in two replicas and make sure that
the service works properly (see the documentation provided at hub.docker.com).
This service will be named engineering-bay and will be on the overmind network. <br>
27. Get the real-time logs of one the tasks of the engineering-bay service. <br>
28. ... Damn it, a group of zergs is attacking orbital-command, and shutting down
the engineering-bay service won’t help at all... You must send a troup of Marines
to eliminate the intruders. Launch a 42school/marine-squad in two replicas,
and make sure that the service works properly (see the documentation provided
at hub.docker.com). This service will be named... marines and will be on the
overmind network. <br>
29. Display all the tasks of the marines service. <br>
30. Increase the number of copies of the marines service up to twenty, because there’s
never enough Marines to eliminate Zergs. (Remember to take a look at the tasks
and logs of the service, you’ll see, it’s fun.) <br>
31. Force quit and delete all the services on the local swarm, in one command. <br>
32. Force quit and delete all the containers (whatever their status), in one command. <br>
33. Delete all the container images stored on the Char virtual machine, in one command
as well. <br>
34. Delete the Aiur virtual machine without using rm -rf. <br>

## Dockerfiles

1. From an alpine image you’ll add to your container your favorite text editor, vim or
emacs, that will launch along with your container. <br>
2. From a debian image you will add the appropriate sources to create a TeamSpeak
server, that will launch along with your container. It will be deemed valid if at least
one user can connect to it and engage in a normal discussion (no far-fetched setup), so
be sure to create your Dockerfile with the right options. Your program should get the
sources when it builds, they cannot be in your repository. <br>
3. You are going to create your first Dockerfile to containerize Rails applications. That’s
a special configuration: this particular Dockerfile will be generic, and called in another
Dockerfile, that will look something like this: <br>
```
FROM      ft-rails:on-build
EXPOSE    3000
CMD       ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
```
3. Your generic container should install, via a ruby container, all the necessary dependencies
and gems, then copy your rails application in the /opt/app folder of your
container. Docker has to install the approtiate gems when it builds, but also launch
the migrations and the db population for your application. The child Dockerfile should
launch the rails server (see example below). If you don’t know what commands to use,
it’s high time to look at the Ruby on Rails documentation. <br>
4. Docker can be useful to test an application that’s still being developed without polluting
your libraries. You will have to design a Dockerfile that gets the development
version of Gitlab - Community Edition installs it with all the dependencies and the necessary
configurations, and launches the application, all as it builds. The container will be
deemed valid if you can access the web client, create users and interact via GIT with this
container (HTTPS and SSH). Obviously, you are not allowed to use the official container
from Gitlab, it would be a shame... <br>
