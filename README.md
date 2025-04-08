# whackascan
## The idea of this project is basically to automate nmap scans using docker containers
## I have no clue if this has been done before but I see it as an interesting project.
## Technologies 

* Python
* Docker
* Nmap

## Theoretical functioning (big words)

The idea is to be able to parallelize the scan of a whole network using docker containers.

The docker containers would retrieve an ip and mac address (macvlan) on the same network as the host and they will be able to launch nmap scans.

The controller will be able to create/recreate docker containers and it will parse the nmap outputs.

For example, if you want to launch a full network scan, the controller will launch a docker container that retrieves all machines on the network.

Then, the controller will instruct docker containers to run an aggressive (or other flag) scan onto each retrieved machine.

In case a docker container gets blocked by a machine, ids or simply stops responding, the container will be recreated with a different IP and mac address.

The retrieved info from the docker containers (after the scan is complete) can then be sent to the controller for parsing or further adjustments.

## Why

Usually when you want to ennumerate a network using nmap, you could use the -sn flag to list all available devices on the network. Then (as far as I know) you need to individually scan them.

That said, there is a risk of your device being blocked when doing those scans and it takes a lot of time.

