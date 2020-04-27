Openvidu Group Call Video Session
===================================

### Please get permission befor using it.

## @Author: Timothy Lam lamt3@lsbu.ac.uk
===================================

Installation 
===================================
```
sudo echo "deb [arch=amd64] http://ubuntu.openvidu.io/6.13.0 bionic kms6" |   sudo tee /etc/apt/sources.list.d/kurento.list
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5AFA7A83
# sudo apt-get update
# sudo apt-get -y install kurento-media-server
#sudo sed -i "s/DAEMON_USER=\"kurento\"/DAEMON_USER=\"${USER}\"/g" /etc/default/kurento-media-server
```

Install COTURN
===================================
```
#sudo apt-get -y install coturn
```

Install Redis
=====================================
```
sudo apt-get -y install redis-server
```
```
sudo nano /etc/kurento/modules/kurento/WebRtcEndpoint.conf.ini
```
```
externalAddress=YOUR_MACHINE_PUBLIC_IP
networkInterfaces=eth0,enp0s25
```
```
sudo nano  /etc/turnserver.conf
```
```
external-ip=YOUR_MACHINE_PUBLIC_IP
listening-port=3478
fingerprint
lt-cred-mech
max-port=65535
min-port=40000
pidfile="/var/run/turnserver.pid"
realm=openvidu
simple-log
redis-userdb="ip=127.0.0.1 dbname=0 password=turn connect_timeout=30"
verbose
```

```
sudo nano /etc/default/coturn
```

```
TURNSERVER_ENABLED=1
```

```
sudo service redis-server restart
sudo service coturn restart
sudo service kurento-media-server restart
```

### You will need Java 8 to run OpenVidu Server 
```
sudo apt-get install -y openjdk-8-jdk
sudo apt install openjdk-8-jre 
```
```
java -version
```

OpenVidu Server  Download
=======================================
```
wget https://github.com/OpenVidu/openvidu/releases/download/v2.12.0/openvidu-server-2.12.0.jar
```

Init Openvidu Server JAR executable
=======================================
```
java -jar -Dopenvidu.secret=MY_SECRET -Dopenvidu.publicurl=https://YOUR_MACHINE_PUBLIC_IP:4443/   openvidu-server-2.12.0.jar
```
```
https://YOUR_OPENVIDU_SERVER_MACHINE_... 

Username : OPENVIDUAPP 
Password : MY_SECRET 
```
