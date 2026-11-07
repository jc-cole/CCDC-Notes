## Remote accessing a windows server

You need to use RDP protocol for windows. 
You can use sometimes ssh but you do not get the full level of control as you would with RDP, default to RDP.

On windows: use Windows Remote Desktop
On linux: use rdp client like remmina





|From slides on Enumerating Windows|
|---|
|
- Username and hostname
- `whoami`
- Group memberships of users
- `whoami /groups`
- `Get-LocalUser`
- `Get-LocalGroup`
- `Get-LocalGroupMember <group>`
- Operating system, version, architecture
- `systeminfo`
- Services, network
- `ipconfig /all`
- `route print`
- `netstat -ano` # all active/listening tcp/udp connections
- Service Binary Hijacking
- Installed 32x/64x applications
- Group Policies, Relationships, Password lockouts?!
- AD???|



Wordpress: common theme in competitions
- look for outdated php backends, check version, update to patched version

Semaphore: 
- used for ansible, playbook to help with setting up infrastructure
- can manage ansible secrets 

Grafana:
- can be used to monitor services 
- often used with prometheus to capture info about a machine
- Prometheus, Grafana Loki, Grafana stack commonly used for monitoring

Build ELK Stack:
- Elasticsearch, Logstash, Kibana

Falco:
- often used in pair with Kubernetes
- used for integrations, often to push events to Discord

Tammy Homework:
- connect to falco server as root in our Teleport and enumerate it
- also ssh in to the other servers, enumerate it, jot down something you can observe about the server

`ss -lntp`
    -l: Display only listening sockets
    -n: Do not try to resolve service names, show exact bandwidth values
    -t: Display tcp sockets
    -p: Show processes using sockets

Linux File Permissions:
- Each file has an owner and belongs to a group
- Three categories of permissions are User (Owner), Group, Others
- Within each category, you can set r (read), w (write), x (execute)
- Symbolic notation looks like rw-r--r--
- Octal notation looks like 644
- look at the three bits in each octal num to figure out which permissions it means
- ex: 644 means permission bits |110|100|100|, user has read + write, Group has read, others have read
- `ls -l` tells you permissions on the listed files
- Use `chmod` to change permissions for a file

`man`
- put man in front of a linux command to see its manual or "man" page
- Tells you basically everything you need to know about a partiular command
- Usage, arguments, flags




