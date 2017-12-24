# Obtenemos el contenedor Windows Server Core que incluye Java.
FROM java-server-core:latest
# Variables.
ARG NEXUS_VERSION 
ENV NEXUS_FOLDER_NAME nexus-$NEXUS_VERSION
# 3.6.2-01
ENV NEXUS_URL http://download.sonatype.com/nexus/3/nexus-$NEXUS_VERSION-win64.zip
# Descargamos y descomprimimos el zip y lo dejamos en C:\Nexus.
RUN mkdir \Nexus  
ADD $NEXUS_URL 'C:\nexus.zip'
RUN powershell Expand-Archive -Path C:\nexus.zip -DestinationPath 'C:\Nexus' -Force; \
    Remove-Item 'C:\nexus.zip' -Force
# Definimos puertos.
EXPOSE 8081
# Iniciamos Nexus.
CMD Nexus\%NEXUS_FOLDER_NAME%\bin\nexus.exe /run