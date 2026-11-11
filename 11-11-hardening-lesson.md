## Hardening !!!

### What is hardening? 

Fixing vulnerabilities of your systems and reducing the attack surface of our infra.

### How do you do this?

This is going to depend a lot on OS/What is running on a particular machine.

In general, things like: 
- changing credentials
- removing unnecessary perms
- access
- updating services
- removing scripts

Want to make things as difficult as possible for red team and as simple to defend as we can!

Mentioned during meeting: can we get an offline copy of a database as a backup?
Tentative answer: maybe? Not allowed to "game" the system

### Competition specific notes

We are going to have specific "scored services", we will be scored on uptime for specifically these.
HOWEVER: critical services on which the scored service depends can have their own vulnerabilities!

Pre competition state: red team may or may not have obtained information about the network, services, users

Assume that all initial passwords, tokens, etc. were possibly leaked!!!

Not allowed to just block the whole ass red team ip address range. Unfortunately.

There is also the black team. They need to have access to our machines in order to track uptimes/reset boxes.
Don't screw with the black team user!

Generally, every machine has like ~5 misconfigurations. 

Generally, red team has a map of our infrastructure beforehand.

### Where persistence mechanisms live:

- dummy accounts
- scheduled jobs (systemd timers, chronjobs)
- Startup files (.bashrc, /etc/rc.local)
- SSH authorized keys
- PAM
- libraries / kernel modules
- **Services (intentional/unintentional misconfigurations) BIG ONE!!!**

Note: 
Be on the lookout for planted malicious services that seem legitimate!
Generally, you can just shut off services that aren't doing anything.
Ex. Docker but no container relevant to scored services

### Firewall

Fence of the network. Controls what data can enter + exit the network. Backup the default configuration.

- Default deny inbound
- allow scoring engine to enter network
- segment subnet traffic: SSH, allow only what needs to be allowed
- Filter outbound traffic: helps kill rev shells
- IPv4 and IPv6 are different: a rule for one doesn't cover the other
- Block internal ports from the outside
- Keep logs

EX: Block port 79. The "finger" port: https://en.wikipedia.org/wiki/Finger_(protocol)

### Possible Roles (tentative):

- Captain (also take on one of the following roles)
- Linux lead (critical linux services)
- Windows AD lead (DC admin)
- Firewall Administrator
- Corporate and Wed Lead (web apps and business projects)
- SOC / SIEM (security information and event management)
- Windows specialist (secondary windows admin)
- Linux specialist (secondary linux service)
- IAM admin (ex: manage teleport) (IAM: identity and access management)


### The nmap incident of 2026

Likely caused by not being on the tailnet/misconfigured. 
We made the UMass IT on call team work on the weekend. Oopsies

Moral of the story:
- nmap makes a lot of traffic
- be careful what you're nmapping
- don't nmap stuff you don't own
- lets try our best not to piss off umass IT in the future!





















