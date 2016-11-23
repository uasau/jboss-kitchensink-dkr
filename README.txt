1) CODE
2) DOCKER
3) MAVEN

##############
#    CODE    #
##############

=>  Docker Maven Plugin

IMP:> https://github.com/spotify/docker-maven-plugin

##############
#   DOCKER   #
##############

$ yum -y update

$ yum install docker docker-registry

$ systemctl enable docker.service

$ systemctl start docker.service

$ systemctl status docker.service

$ docker pull jboss/base-jdk:7

##############
#    MAVEN   #
##############

See settings.xml