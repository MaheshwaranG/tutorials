# Nginx

> High Performance Load Balancer, Web server and Reverse Proxy

**Introduction:**

- Nginx is an open source web server and uses non threaded event driven architecture.
- Load Balancer
- Reverse proxy server
- Content cache

# important terms

- Context (scope)
- Directives (single line statement)

Note: We can use some kind of programming language syntax like if statement. Nginx offers so many feature.

**Installation in ubuntu :**

- apt-get install nginx # install nginx on ubuntu
- service nginx start # start nginx server
- service nginx stop # stop nginx server
- service nginx status # check status of nginx server
- service nginx restart # restart runing nginx server
- nginx -t # T stands for test. test nginx configurations

**Docker**

> docker run -d -p 8082:80 --name nginx nginx
> docker exec -it nginx bash

**Architecture**

- Nginx architecture consists of a master and workers process.
- Master process perform privileged operations - such as reading configuration and binding to ports
- one master process can control multiple worker processes
- The worker process handles network connections, read and write content to disk and communicate with other servers
- Each worker process is single threaded
- Worker process waits for events on the listen and connection socket
- Any event on listen socket creats a new connection
- `worker_processes` directive defines the number of worker process should run
- `worker_connections` maximum number of simultaneous connections for each worker process
- Number of request handle per sec is no_of_worker_connection \* no_of_worker ( no_of_worker_connection is equal no of open file limit of the system (ulimit))
- nginx is single threaded, So best practice is total number of worker_process should equivalent to number of core in the system

**Basic Nginx Configuration**

```
server {
    listen 80 default_server;
    server_name client;
    location / {
        root /var/www/html/;
        index index.html;
    }
}
```

**File structure info**

- /etc/nginx/nginx.conf # this is entry point configuration of nginx
  important contet and directives

  - worker_processes
  - events
  - http

**variable**

- Nginx support variables
  - Inbuild variable
  - Custom variables

Syntax:
set \$varibale value;

Note: use it as \$variable

**Location matching types**

> location modifier uri {}

Modifiers :

- exact match (=)
- longest preferential match (^~)
- Regex match (~) case sensitive or (~\*) case insensitive
- prefix match (by default all other are prefix match)
