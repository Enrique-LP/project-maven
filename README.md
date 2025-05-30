# JavaFX Game with CodeGym Engine

Este proyecto es un juego JavaFX ejecutable que utiliza el motor gráfico de CodeGym.

## Requisitos Previos

- JDK 18.0.1
- Maven
- IDE compatible con Maven (opcional)

## Configuración del Proyecto

### Dependencias

El proyecto utiliza las siguientes dependencias:

- `org.apache.commons:commons-lang3:3.12.0`
- `org.openjfx:javafx-controls:18.0.1`
- `com.codegym:desktop-game-engine:1.0` (JAR local)
- `org.junit.jupiter:junit-jupiter-engine:5.8.2` (scope: test)

### Plugins de Maven

El proyecto está configurado con varios plugins de Maven:

1. `maven-compiler-plugin`: Configuración por defecto para compilación
2. `maven-dependency-plugin`: Copia todas las dependencias (scope: compile) al directorio de build
3. `maven-jar-plugin`: Crea el JAR ejecutable con las siguientes configuraciones en MANIFEST.MF:
   - `Class-Path`: Incluye todas las dependencias JAR
   - `Main-Class`: `org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader`
   - `Rsrc-Main-Class`: `com.codegym.games.racer.RacerGame`
4. `maven-surefire-plugin`: Configurado para excluir `StrangeTest`
5. `javafx-maven-plugin`: Para ejecutar el juego a través de Maven

## Construir el Proyecto

Para construir el proyecto, ejecute:

```bash
mvn clean install
```

Este comando:
1. Limpia el directorio target
2. Compila el código
3. Ejecuta las pruebas (excluyendo StrangeTest)
4. Crea un fat-JAR con todas las dependencias

## Ejecutar el Juego

Hay dos formas de ejecutar el juego:

1. A través de Maven:
```bash
mvn javafx:run
```

2. Directamente con Java:
```bash
"<ruta-a-java-18>/bin/java.exe" -jar "target/project-maven-1.0.jar"
```

Ejemplo:
```bash
"C:\Users\username\.jdks\openjdk-18.0.1.1\bin\java.exe" -jar "target/project-maven-1.0.jar"
```

## Notas Importantes

- El proyecto requiere específicamente JDK 18.0.1
- No modificar el paquete `org.eclipse.jdt.internal.jarinjarloader`, ya que contiene un cargador personalizado para iniciar la aplicación JavaFX
- El archivo JAR resultante es un fat-JAR que contiene todas las dependencias necesarias
