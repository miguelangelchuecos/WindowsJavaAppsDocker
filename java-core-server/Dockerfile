# Obtenemos el contenedor limpio y oficial Windows Server Core.
FROM microsoft/windowsservercore
# Variables.
ENV JAVA_URL http://javadl.oracle.com/webapps/download/AutoDL?BundleId=225355_090f390dda5b47b9b721c7dfaa008135
# Descargamos el fichero de instalación de JAVA x64 y lo dejamos en C:\
ADD $JAVA_URL 'C:\jreinstaller.exe'
# Realizamos la instalación de forma silenciosa y al finalizar, eliminamos el fichero de instalación.
RUN powershell Start-Process -filepath C:\jreinstaller.exe -passthru -wait -ArgumentList '/s INSTALLDIR=C:\Java\jre1.8.0_151 /L install64.log'; \ 
    Remove-Item C:\jreinstaller.exe -Force
# Establecemos la variable JAVA_HOME.
ENV JAVA_HOME 'c:\Java\jre1.8.0_151'
# La asignamos a la carpeta bin donde se situan los ejecutables.
RUN setx PATH %PATH%;%JAVA_HOME%\bin
# Mostramos Java.
CMD java.exe