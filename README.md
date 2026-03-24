# Práctica de Sistemas Distribuidos

Este proyecto implementa un sistema de chat multiusuario en modo texto utilizando Sockets Java (TCP). Sigue un modelo push donde un servidor central retransmite los mensajes a todos los participantes conectados en tiempo real.
Características

    Soporte Multiusuario: Varios clientes pueden conectarse simultáneamente a un único servidor.

    Modelo Push: El servidor mantiene un registro de los clientes y reenvía los mensajes uno a uno.

    Sistema de Bloqueo (Ban/Unban): Los usuarios pueden bloquear localmente los mensajes de apodos (nicknames) específicos.

    Registro de Autoría: Cada mensaje transmitido incluye un prefijo obligatorio de "patrocinio" para asegurar la autoría del alumno.

# Requisitos Previos

    Java Development Kit (JDK) 17 (versión recomendada para evitar advertencias de compilación).

    Apache Maven (para la gestión de dependencias y limpieza del proyecto).

    Apache Ant (para la generación de la documentación Javadoc).

# Estructura del Proyecto

El proyecto sigue el diseño estándar de directorios de Maven:

    src/main/java/es/ubu/lsi/client: Implementación del cliente (ChatClient, ChatClientImpl).

    src/main/java/es/ubu/lsi/server: Implementación del servidor (ChatServer, ChatServerImpl).

    src/main/java/es/ubu/lsi/common: Clases comunes compartidas (ChatMessage, MessageType).

# Configuración y Compilación
### 1. Configurar la versión de Java

Asegúrate de que los archivos pom.xml y build.xml estén configurados para Java 17 para evitar advertencias de opciones obsoletas:

En pom.xml:

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

En build.xml:
Actualiza las tareas javac y javadoc para usar source="17" y target="17".

### 2. Compilar mediante línea de comandos

Ejecuta el siguiente comando desde el directorio raíz para compilar las clases en la carpeta build:

    javac -d build src/main/java/es/ubu/lsi/common/*.java src/main/java/es/ubu/lsi/server/*.java src/main/java/es/ubu/lsi/client/*.java

# Instrucciones de Ejecución
### 1. Iniciar el Servidor

Abre una terminal y ejecuta:

    java -cp build es.ubu.lsi.server.ChatServerImpl

El servidor escucha en el puerto 1500 por defecto.

    Salida esperada: Server waiting for Clients on port 1500.

### 2. Iniciar los Clientes

Abre una nueva terminal para cada cliente que desees conectar:

    java -cp build es.ubu.lsi.client.ChatClientImpl <nickname> 1500 localhost

Sustituye <nickname> por tu apodo deseado.

    El orden de los argumentos es: nickname, puerto, host.

# Comandos del Chat

    ban <nickname>: Bloquea localmente los mensajes del usuario especificado.

    unban <nickname>: Vuelve a aceptar los mensajes del usuario bloqueado.

    logout: Cierra la conexión de forma segura y sale de la aplicación.

# Documentación

Para generar la documentación Javadoc obligatoria en la carpeta /doc, utiliza Ant:

    ant javadoc

# Limpieza del Proyecto

Para eliminar los archivos compilados y artefactos temporales antes de la entrega:

    mvn clean

O bien:

    ant clean

