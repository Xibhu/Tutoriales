 
# Configuración eclipse JavaFX

Para hacer funcionar eclipse con OpenJDK11 y Openjfx hay que realizar varios pasos. Esta es la manera en la que a mi me ha funcionado utilizando debian testing.

## Instalar OpenJDK11

Por defecto viene instalado en linux (en mi caso uso debian testing bullseye).  
En caso de no tenerlo, se realiza con el siguiente comando, o el que sea de tu distribución.

`sudo apt install openjdk-11-jdk`

En windows descargar [adoptOpenJDK](https://adoptopenjdk.net/?variant=openjdk11&jvmVariant=hotspot) o oracle java.

## Instalar Openjfx

Este paquete no viene instalado y es la base del javafx11.

`sudo apt install openjfx`

En windows o linux (si no se quiere del repositorio) descargar [openjfx](https://openjfx.io/) de la página oficial.

## Instalar Eclipse

Vamos a la página oficial https://www.eclipse.org/downloads/. Se descarga y se instala donde queramos.

## Configurar javafx en eclipse.

En primer lugar tras ejecutar eclipse por primera vez y tener ya hecho el workspace. Vamos a la siguiente opción.

Window -> Preferences -> Java -> Build Path -> User Libraries

Entonces le damos a 'New' con nombre JavaFX11 (o similar) y aceptar. Y cuando aparezca la libreria, pisamos 'Add External JARs...' y se seleccionan todas las librerias de javafx.

En caso de instalar openjfx desde repositorio en linux, hay que ir a la ruta `/usr/share/openjfx/lib` y seleccionar todos los jar, en mi caso son 7 distintos. Base, Controls, Fxml, Graphics, Media, Swing, Web.

En caso de hacerlo desde la descarga de la página oficial, se selecciona dentro del zip la única libreria que hay.

## Configurar proyecto en eclipse

Ahora tras tener esa configuración, ahora en cada proyecto hay que realizar una modificación. Ya sea con un proyecto normal, o con proyecto javafx si se tiene instalado el plugin e(fx)clipse (versión 3.5.0) hay que añadir la librería a mano y el archivo modules-info.java.

En primer lugar al crear un proyecto nuevo, ya sea Java Proyect o JavaFX proyect, tras la primera ventana en la que se pone el nombre del proyecto, y se selecciona la versión de java, en este caso la 11, se le da a Next.

Entonces en las pestañas se selecciona Libraries y se selecciona Modulepath, entonces se pisa Add Library, y en la nueva ventana se selecciona User Library, tras esto se selecciona la librería JavaFX11 o con el nombre que se le haya puesto y se pisa Finish.

Con esto el proyecto ya tiene incluido los paquetes, pero no es suficiente, ahora en la carpeta src de nuestro proyecto debemos tener un archivo `module-info.java` si es proyecto normal de java, en caso de javafx no estará, por lo tanto se crea a mano.

En el interior vamos a poner las siguientes líneas.

```java
module fx {
	requires javafx.graphics;
	requires javafx.controls;
	requires javafx.base;
	requires javafx.fxml;
	requires javafx.web;
	requires javafx.media;
	requires javafx.swing;
	exports paquete;
	opens paquete to javafx.graphics;
}
```
Donde `paquete` es el nombre del paquete donde está el archivo Main.java en nuestro proyecto. Con esto realizado y el siguiente código de prueba, debería aparecer una ventana en blanco al ejecutar el Main.

```java
package pru;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;


public class Main extends Application {

    @Override
    public void start(Stage stage) {
        Scene scene = new Scene (new StackPane(), 300, 200);
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }

}

```
En mi caso el paquete que pongo en el archivo module-info es `pru`.

Si da algún error, no sé como se soluciona.