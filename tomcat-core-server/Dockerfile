# Obtenemos el contenedor Windows Server Core que incluye Java.
FROM java-server-core:latest
# Variables.
ARG TOMCAT_VERSION
ENV TOMCAT_URL https://archive.apache.org/dist/tomcat/tomcat-8/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION-windows-x64.zip
# Descargamos Tomcat x64 y lo dejamos el paquete comprimido en C:\
RUN mkdir \Tomcat  
ADD $TOMCAT_URL 'C:\tomcat.zip'
# Descomprimimos el fichero descargado.
RUN powershell Expand-Archive -Path C:\tomcat.zip -DestinationPath 'C:\\' -Force; \
    Remove-Item 'C:\tomcat.zip' -Force; \
    Move-Item C:\apache-tomcat-%TOMCAT_VERSION%\* C:\Tomcat; \
    Remove-Item C:\apache-tomcat-%TOMCAT_VERSION% -Force
# Definimos puertos.
EXPOSE 8080
# Establecemos la variable CATALINA_HOME.
ENV CATALINA_HOME 'C:\Tomcat'
RUN setx PATH %PATH%;%CATALINA_HOME%\bin
# Iniciamos Jenkins.
CMD C:\Tomcat\bin\catalina.bat run