# le-serverpilot
SH script to install / manage Lets Encrypt for Server Pilot free users

#** PLEASE USE AT YOUR OWN RISK **

##Requirements

 * Ubuntu 14.04 
 * Server running with Serverpilot
 * Root / SUDO User Access
 * Install in a non user home directory (so /etc/ will work fine)

---
##How to Install

```
cd /etc/
git clone https://github.com/dfinnema/le-serverpilot.git
cd le-serverpilot
chmod +x df.sh
```
##For development branch:
```
cd /etc/
git clone -b development https://github.com/dfinnema/le-serverpilot.git
cd le-serverpilot
chmod +x df.sh
```
---
##How to Use

```
cd /etc/le-serverpilot
./df.sh
```
---
## Config File

you can edit the config file to change the testing mode to 0 to not use the staging server at Lets Encrypt
As well as setup Mailgun to email you the result of each CRON job 

---
## Misc

Please note this is just a simple set of scripts quickly written. Feel free to fork it.

It uses the Shell script from (https://github.com/lukas2511/letsencrypt.sh) to do all the Lets Encrypt stuff. 

---
## Email result of CRON Jobs

By default it does not email anybody unless you edit the config file (copy a sample from config.sample) 
It uses mailgun to send it as not all servers have the mail module installed by default. 

---
### FAQ

Q: Does this need to be run as ROOT / SUDO (it will automaticly attempt to run itself with SUDO)

A: Yes at this time it requires ROOT or SUDO access as it needs to edit APACHE and NGINX configurations as well as for CRON jobs

Q: Where does it store the SSL files 

A: in a sub directory called 'certs' (eg; le-serverpilot/certs/)

Q: Where does it store my Lets Encrypt account 

A: in a sub directory called 'accounts' (eg; le-serverpilot/accounts)

Q: Does this support SNI (Server Name Indication)?

A: Yes it does but it needs to be able to verify all the domains from this server

Q: Does this use the official Lets Encrypt client

A: No it uses a very usefull script from (https://github.com/lukas2511/letsencrypt.sh) to do the heavy lifting

Q: How often will it renew the cert?

A: If the Certificate is older than 29 days it will renew the cert if run manually or through a CRON job
