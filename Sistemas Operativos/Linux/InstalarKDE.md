 
A continuación mi manera de instalar debian en este portátil:

Tras elegir el modo normal, realizo los mismos pasos, pero sin instalar la interfaz gráfica (dejando sin tick ningún elemento de interfaces durante el instalador), de esta manera puedo instalarla más adelante con los programas que yo necesito, ya que por defecto las interfaces gráficas de serie vienen con una variedad de software que no utilizo. Además de realizar algunas configuraciones para que todo funcione bien.

Una vez instalado sin interfaz, se arranca debian en modo terminal automáticamente, inicio sesión con mi usuario y contraseña. 

## Opcional

En primer lugar coloco los repositorios hacia testing, y añadiendo los paquetes contrib y non-free.

Para ello utilizamos el siguiente comando.

`sudo nano /etc/apt/sources.list`

Y en las líneas que se tenga (pueden ser más o menos), lo coloco de la siguiente manera.

```
deb http://deb.debian.org/debian/ testing main contrib non-free
deb-src http://deb.debian.org/debian/ testing main contrib non-free

deb http://security.debian.org/debian-security testing/updates main contrib non-free
deb-src http://security.debian.org/debian-security testing/updates main contrib non-free
```

Tras guardar se actualiza.

`sudo apt update`

`sudo apt upgrade`

`sudo apt dist-upgrade`

## Instalar interfaz gráfica

Se instala la interfaz, el administrador de redes, el wifi y el bluetooth. Esos firmware son los drivers para MI hardware, ustedes utilizariais el correspondiente, o ninguno, teneis que vervuestro hardware y si es necesario instalar algo extra que no haga debian por defecto.

`sudo apt install kde-plasma-desktop plasma-nm firmware-iwlwifi firmware-realtek`

## Redes

Ahora reiniciamos, debería entrar directamente en la interfaz gráfica, iniciamos sesión, y sorpresa, la red cableada no funciona. En mi caso tengo que ir al siguiente archivo:

`sudo nano /etc/network/interfaces`

Y borrar las siguientes líneas que son las dos últimas:

>allow-hotplug enp7s0f1  
iface enp7s0f1 inet dhcp

## Gráfica nvidia

Y para poder utilizar la gráfica con ahorro de energía y para juegos utilizo bumblebee con el siguiente comando que nos dan en la página oficial de debian, si solo vais a trabajar estilo oficina, con los nouveau es suficiente.

`sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install bumblebee-nvidia primus libgl1-nvidia-glx primus-libs:i386 libgl1-nvidia-glx:i386`

Tras esto reiniciar el ordenador.

Después se puede hacer unas configuraciones OPCIONALES, como instalar mesa-utils para tener glxgears y probar el optirun que es el comando necesario para utilizar la gráfica dedicada.

`sudo apt install mesa-utils`

Comprobar que funciona el driver.

`optirun glxgears`

Y añadir una línea en un archivo de texto, que no sé para qué se utiliza, pero estaba en un tutorial. También opcional.

`sudo nano /etc/enviroment`

Añadir linea:

`__GLVND_DISALLOW_PATCHING=1`

[Mi manera de instalar los programas](InstalarProgramas.md)

