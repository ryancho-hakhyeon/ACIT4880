# Jenkins
Install docker in your jenkins server and follow the instructor below the link that is explained how you do initial set up.

+ Link: https://linuxhint.com/install_jenkins_docker_ubuntu/


## Setting Jekins in Doker
+ Stop
  + sudo docker stop jenkins-master
  + sudo docker rm jenkins-master

+ Building the image
  + sudo docker build -t myjenkins .

+ Start
  + sudo docker run -p 8080:8080 -p 50000:50000 --restart always --name=jenkins-master --mount source=jenkins-log,target=/var/log/jenkins --mount source=jenkins-data,target=/var/jenkins_home -d myjenkins

