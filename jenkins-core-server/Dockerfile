# Obtenemos el contenedor Windows Server Core que incluye Java.
FROM java-server-core:latest
# Variables.
ARG JENKINS_VERSION
ENV JENKINS_URL http://mirrors.jenkins-ci.org/war/$JENKINS_VERSION/jenkins.war
# Descargamos el fichero de instalación de JAVA x64 y lo dejamos en C:\
RUN mkdir \Jenkins  
ADD $JENKINS_URL 'C:\Jenkins\jenkins.war'
# Establecemos la variable de Jenkins.
ENV HOME /jenkins
# Definimos puertos.
EXPOSE 8080
EXPOSE 50000
# Iniciamos Jenkins.
CMD java -jar "C:\Jenkins\jenkins.war"