 
Fallo del programa LogoComfortV8 en linux, al intentar cambiar de versión de logo o intentar subir el programa al dispositivo, el programa da un error 

"An unexpected error occurred. Your data may be inconsistent and subsequent errors may occur.
java.lang.UnsupportedOperationException: cfg script file format is not supported."

O bien.

"An unexpected error occured. Your data may be inconsistent and subsequent error may occur.
java.lang.UnsupportedOperationExeption: adapter type is not support."

Para solucionar esto hay que crear una carpeta y dos archivos con el nombre de los dispositivos de red del pc, vacios.

`sudo mkdir -p /etc/sysconfig/network`

`sudo touch/etc/sysconfig/network/ifcfg-eth0`

`sudo touch /etc/sysconfig/network/ifcfg-wlan0`

Hay que sustituir "eth0" y "wlan0" por los nombres de las redes que aparezcan con el comando `ip addr` en mi caso son `enp7s0f1` y `wlp0s20f3`