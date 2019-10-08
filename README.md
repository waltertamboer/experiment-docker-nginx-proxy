# experiment-docker-nginx-proxy

This repository contains an experiment where I set up two sites within Docker containers and 
nginx acts as a proxy.

## The Problem

Consider running multiple webserver containers on the same server. How does the server know 
which container to serve to the user?

## Solution  

This project contains a `docker-compose.yml` file containing three containers. Two websites 
that serve a webpage via Apache httpd: "Site 1" and "Site 2". The third container is an nginx
container acting as a proxy between the two sites.

Within the nginx configuration two sites are defined with two different server names:
- site1.experiment.waltertamboer.nl
- site2.experiment.waltertamboer.nl

Each container runs on a different port (8081 and 8082 in this example). When one of these 
addresses is entered in the browser, the proxy knows to which container the user should be 
redirected.

## Installation

- Clone the repository
- Edit your `/etc/hosts` file and make sure it contains the following lines:
    ```
    127.0.0.1 site1.experiment.waltertamboer.nl
    127.0.0.1 site2.experiment.waltertamboer.nl
    ``` 
- Start up the containers: `docker-compose up -d`

Now you'll be able to visit site 1 and site 2 via the following addresses:
- http://site1.experiment.waltertamboer.nl
- http://site2.experiment.waltertamboer.nl
