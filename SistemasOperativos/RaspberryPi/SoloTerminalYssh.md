 
# Instalación modo terminal

Instalación para hacer funcionar la raspberry pi sin entorno gráfico, únicamente modo terminal con la intención de hacerlo funcionar como un servidor, con activación de ssh, wifi (opcional), ip fija(opcional).

Toda la explicación de este tutorial es sin llegar a colocar la SD en la raspberry hasta el final del proceso, todo son ediciones de archivos desde un PC que tiene insertada la SD recién grabada.

## Descargar e instalar el sistema operativo en la SD

Ir a la página oficial de [RASPBERRY PI](https://www.raspberrypi.org/downloads/raspberry-pi-os/) y descargar la versión LITE.

Ir a la página del programa para grabar en la SD [ETCHER](https://www.balena.io/etcher/) y descargar el correspondiente a vuestro sistema operativo normal.

Abrir Etcher, elegir la imagen que estará posiblemente en formato zip, elegir la sd y comenzar la grabación.

## Editar archivos para Headless

Una vez grabado, para hacer funcionar la raspberry pi de forma `headless`, es decir, sin pantalla, ni teclado, únicamente una conexión de alimentación y red, se debe activar el `ssh`.

Para ello en la SD grabada, se entra en la partición pequeña llamada `boot`, y se crea un archivo sin extensión que se llame ssh, sin contenido. Al existir ese archivo, en el primer arranque la raspberry lo detectará y activará el ssh.

## Asignar ip fija (opcional)

Opcionalmente se puede asignar una ip fija (no recomendado, hay otras soluciones) para saber siempre qué dirección tiene la raspberry. Para ello en la partición `rootfs` en la carpeta `etc` se modifica un archivo llamado `dhcpcd.conf`, en el que al final del archivo, sin borrar lo que ya está, se añade lo siguiente.

Para conexión por cable se deja tal cual, y para wifi se sustituye `eth0` por `wlan0`.
```
interface eth0
static ip_address=192.168.1.210
static routers=192.168.1.1
static domain_name_servers=8.8.8.8 8.8.4.4
```
`ip_address` corresponde con la ip que se quiere asignar a la raspberry. Recomendado fuera del rango de dhcp (ip automáticas) del router.  
`routers` corresponde con el router que hace de gateway.  
`domain_name_servers` corresponde con las ip de los servidores de dns que se utilice.

## Configurar wifi
Para decirle a la raspberry que desde el primer inicio se conecte a una red wifi disponible, se debe entrar en la partición `boot` y crear un archivo llamado `wpa_supplicant.conf`. Esto en el primer inicio la raspberry lo detectará y sobreescribirá el original ubicado en `/etc/wpa_supplicant/wpa_supplicant.conf` con este nuevo. Debe contener la zona del pais, el nombre de la wifi, y su contraseña, a parte de un encabezado fijo. No quitar las comillas.

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=ES

network={
    ssid="nombreWifi"
    psk="passwordWifi"
}
```
## Encender Raspberry

Una vez hecho todo lo anterior, ya podremos conectarnos a la raspberry por cable o wifi, con ip dinámica o fija. Si se usa dinámica hay que usar algún programa para detectar las ip en la red y ver cual está asignada a la raspberry. O bien usar su nombre de hostname que por defecto es `raspberrypi`.

Se coloca la SD en la raspberry, se conecta el cable de red si fuera necesario, si se ha configurado una wifi, no se conecta cable. Se conecta el cable de alimentación, y a esperar 1-3 minutos a que se haga la primera configuración y se reinicie automáticamente. Entonces se podrá entrar mediante ssh de la siguiente manera con windows y linux, abrir una terminal. Y escribir una de las dos maneras, la ip que se ha utilizado, o hostname.  
`ssh pi@192.168.1.210`  
`ssh pi@raspberrypi`

Saltará un aviso y se escribe `yes`, entonces preguntará por la contraseña del usuario. Por defecto es `raspberry`.

## Seguridad

Una vez podamos manipular la raspberry con terminal, hay dos modificaciones importantes respecto a la seguridad, una es cambiar la contraseña del usuario, a través del comando `sudo raspi-config`. En esa configuración se pueden modificar más cosas si se considera necesario.

La siguiente es quitar la contraseña escrita literalmente en el archivo ahora actualmente en `/etc/wpa_supplicant/wpa_supplicant.conf`, para ello se puede hacer durante las ediciones de archivos si se tiene un sistema operativo linux, o desde la propia raspberry. Se puede hacer durante los pasos previos.

Desde una terminal se ejecuta lo siguiente. `wpa_passphrase nombreWifi` Sin comillas. Al pisar enter preguntará por la contraseña del wifi, se escribe y se pisa enter de nuevo. Ahora nos devuelve algo parecido a lo que ya se tenía, pero el psk es mucho más largo, esto se SUSTITUYE por la contraseña que se tenía antes, quitando las comillas solo en la contraseña. Ejemplo.

Terminal:
```
[xibhu@localhost ~]$ wpa_passphrase nombreWifi
# reading passphrase from stdin
passwordWifi
```
Lo que devuelve y se sustituye en el archivo `/etc/wpa_supplicant/wpa_supplicant.conf`. El viejo psk está comentado con `#` y se debe borrar toda su línea.
```
network={
        ssid="nombreWifi"
        #psk="passwordWifi"        <--BORRAR
        psk=a8be581e761b6c17ad77d41159e11cd2a9e1f58fbccc9c322a30918b4bd5f878
}
```