# FAQ

### How to pre-config Seafile directory and server address in Windows


### How to use run Seafile client as a service in Windows

Seafile client can be configured to run as a daemon using tools like Firedaemon.

First configure Seafile as the user it should run - in this example "Administator"

Parameters for ccnet: -c C:/Users/Administrator/ccnet
Parameters for seaf-daemon: -c C:/Users/Administrator/ccnet -d S:/seafile-data -w S:/Seafile
