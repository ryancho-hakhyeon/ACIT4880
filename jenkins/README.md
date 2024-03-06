# Jenkins
Install docker in your Jenkins server and follow the instructor below the link (my Blog) that explains how you do the initial setup.

+ Link: https://ryanchohakhyeon.wordpress.com/2023/12/26/azure-ci-cd-pipeline-jenkins/


## Setting Jekins in Doker
+ Stop
  + sudo docker stop jenkins-master
  + sudo docker rm jenkins-master

+ Building the image
  + sudo docker build -t myjenkins .

+ Start
  + sudo docker run -p 8080:8080 -p 50000:50000 –restart always –name=jenkins-master –mount source=jenkins-log,target=/var/log/jenkins –mount source=jenkinsdata,target=/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -d myjenkins

## Build Jenkins Pipeline
+ New Item > (Enter an Item Name) Pipeline and OK
+ In the Pipeline section
  + Definition - Select Pipeline script from SCM
  + SCM - Select Git
  + Repository URL - Your GitLab Repository URL (ex. 'point' GitLab repository, 'carlot' GitLab repository)
  + Credentials - Select the Credentials you added, if not Click Add
    + Select Jenkins
    + Write Username - Any name you can recognize easily - and Password - It's from your GitLab you created
    + Click Add
  + Branch Specifier - Rewrite to */main
  + Script Path - Rewrite to ci/Jenkinsfile   

## Jenkins Plugin
+ SonarQube Scanner

