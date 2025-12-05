
# Restricted-user-logging

Create a restricted Bash user with with activity logging on linux system
This project demonstrates how to create a limited Bash shell user (`rbash`) in Linux, log their commands to `/var/log`, and ensure security by restricting shell access.

Features:

  -Restricted shell ("rbash")
  - Command logging using("script")
  - Secure logging storage in "/var/log"
  - Easy setup

 Setup

## step 1. Create the user

```bash
sudo useradd -m -s /usr/bin/rbash desmondkrus # replace with your own name
```

## step 2. Create log file
```bash
sudo touch /var/log/desmondkrus_session.log
sudo chown desmondkrus:desmondkrus /var/log/desmondkrus_session.log
sudo chmod 600 /var/log/desmondkrus_session.log
```

## step 3. Setup the restricted shell with logging

```bash
sudo bash -c 'cat <<EOF > /usr/local/bin/logrbash
#!/bin/bash
LOGFILE="/var/log/desmondkrus_session.log"
exec /usr/bin/script -q -f -c "/bin/rbash" "$LOGFLE"
EOF'
```

After that run these commands

```bash
sudo chmod +x /var/log/bin/logrbash
sudo usermod -s /usr/local/bin/logrbash desmond
krus
```

## step 4. Usage

Login as the restricted User:

```bash
su - desmondkrus
pwd
whoami
exit
```

Verify the logged activity

```bash
sudo cat /var/log/desmondkrus_session.log
```

License
This project is license under the MIT license

Author
Harison Kimutai Chirchir
harisonchirchir25@gmail.com








  
