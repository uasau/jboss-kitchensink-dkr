# Use rhel 7.2 Image as the base
FROM rhel72:latest

# Maintainer
MAINTAINER "Samu Geevarghese" "samu@uasau.com"

RUN mkdir -p /opt/java /opt/jboss

# JDK 1.7
COPY installs/jdk1.7.0_79.zip /tmp/jdk1.7.0_79.zip
RUN unzip /tmp/jdk1.7.0_79.zip -d /opt/java

# Set the JAVA_HOME  env variable
ENV JAVA_HOME /opt/java/jdk1.7.0_79

# EAP 6.4.0
COPY installs/jboss-eap-6.4.0.zip /tmp/jboss-eap-6.4.0.zip
RUN unzip /tmp/jboss-eap-6.4.0.zip -d /opt/jboss

# Set the JBOSS_HOME env variable
ENV JBOSS_HOME /opt/jboss/jboss-eap-6.4

RUN ls -ltRa /opt

RUN /opt/java/jdk1.7.0_79/bin/java -version

# Create EAP User
RUN $JBOSS_HOME/bin/add-user.sh admin jboss#1234 --silent

# Configure EAP
RUN echo "JAVA_OPTS=\"\$JAVA_OPTS -Djboss.bind.address=0.0.0.0 -Djboss.bind.address.management=0.0.0.0\"" >> $JBOSS_HOME/bin/standalone.conf

# Add WAR file to deployment folder
ADD installs/jboss-kitchensink.war $JBOSS_HOME/standalone/deployments

# Open Ports
EXPOSE 8080 9990 9999

# Start EAP
ENTRYPOINT $JBOSS_HOME/bin/standalone.sh -c standalone-full-ha.xml
