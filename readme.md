## Linux Server Configuration Project

The working app is available [here](http://ec2-52-42-94-94.us-west-2.compute.amazonaws.com), ip: 52.42.94.94

### Steps that were made while configuring server

Created a new user named grader, sudo permissions granted this user.

```
adduser grader
sudo adduser grader sudo
```

All currently installed packages updated

```
sudo apt-get update
sudo apt-get upgrade
```

The local timezone configured to UTC

```
sudo dpkg-reconfigure tzdata
```

The SSH port changed from 22 to 2200
Uncomplicated Firewall (UFW) configured

```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow ntp
sudo ufw enable
```

Installed Apache, created wsgi-application:

```
import sys
import os.path
sys.path.insert(0, "/var/www/html")
from webserver import app as application
application.secret_key = 'secret-string'
```

Indtalled PostgreSQL, created new user with all privileges on database.
Changed *create_engine* call that is now accessing postgre database (instead of sqlite).

Also installed git and some additional dependencies required by the application.
