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
+ JUnit (if you don't have)
+ Git plugin (if you don't have)

## Add Credentials for Containerization
+ Go to Manage Jenkins
+ Go to Credentials in the Security section
  + Click global (Domain column)
  + Click Add Credentials
    + Kind - Secret text
    + Secret - Copy and Paste your Access Token from the Docker Hub account 

## Setting URLs from Jenkins
+ Jenkins Location - Go to Manage Jenkins > System > Jenkins Location section
  + Jenkins URL - your proxy Jenkins VM URL (ex. http://jenkins-practice.westus3.cloudapp.azure.com:8080/jenkins/)
+ SonarQube - Go to Manage Jenkins > System > SonarQube Server section
  + Click Add SonarQube
  + Name - SonarQube
  + Sever URL - your proxy SonarQube VM URL (ex. http://others-practice.eastus.cloudapp.azure.com:9000/sonarqube)
+ Shared Library - Go to Manage Jenkins > System > Retrieval method section
  + Source Code Management - Git
  + Project Repository - your shared library repository (ex. https://gitlab-practice.eastus2.cloudapp.azure.com/prototypes/ci_functions.git)
  + Credentials - Select the Credentials you added, if not Click Add
