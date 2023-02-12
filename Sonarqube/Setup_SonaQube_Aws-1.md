## Setup sonarqube on aws _ec2

https://github.com/ravdy/DevOps

Source: https://docs.sonarqube.org/latest/requirements/requirements/

1. An EC2 instance with a minimum of 2 GB RAM (t2.small)

2. Java 11 installation
3. SonarQube cannot be run as root on Unix-based systems, so create a dedicated user account for SonarQube if necessary.

### install java
Check what java are avaliavle
```
yum list | grep openjdk
```
For java 11
```
amazon-linux-extras list
```
```
amazon-linux-extras install java-openjdk11 -y
```
### Sonarqube install
###### Download SonarQube latest verions on to EC2 instace
```
cd /opt
```
```
wget https://binaries.sonarsource.com/CommercialDistribution/sonarqube-developer/sonarqube-developer-8.9.9.56886.zip
```
Extract packages
```
unzip sonarqube-developer-8.9.9.56886.zip
```
Make a folder sonarqube
```
mkdir sonarqube
```
Move to sonarqube folder
```
mv sonarqube-8.9.9.56886 sonarqube
```
```
cd /sonarqube
```
```
ls
```


### Sonarqube does not run on root user / MUst create a user 
#### /opt
@opt
```
useradd sonaradmin
```

```
visudo
```
```
scrollING
root ALL=(ALL)     ALL
```
```
sonaradmin ALL=(ALL) NOPASSWD:ALL
```

Check
```
ls -l
```

Giving permission or Ownership of the file
```
cd ..
ls -ltr
```
```
chown -R sonaradmin:sonaradmin /opt/sonarqube-8.9.9.56886
```
```
chmod -R 775 /opt/sonarqube-8.9.9.56886
```

To check
```
ll
```
##### Now switch to root user to sonaradmin user
```
su - sonaradmin
```
```
cd /opt/sonarqube-8.9.9.56886/
```
```
ll
```
```
cd bin
```
```
ls
```
```
cd bin/linux-x86-64/
```
```
./sonar.sh start
```
#### let check the status
```
./sonar.sh status
```
#### To check port
```
netstat -tulpn
```














