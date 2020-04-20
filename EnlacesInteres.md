base de datos: wordpress
usuario: wpuser
password: 
prefijo: wp_dev_

Titulo del sitio: 
Nombre usuario: admin
Password: 
----
Cambiar el límite de subida de archivos. (cambiar por tamaños adecuados)
nginx: nginx.conf

Añadir en http, o server, o location, esta línea:
# set client body size to 2M #
client_max_body_size 2M;

php: php.ini
;This sets the maximum amount of memory in bytes that a script is allowed to allocate
memory_limit = 32M

;The maximum size of an uploaded file.
upload_max_filesize = 2M

;Sets max size of post data allowed. This setting also affects file upload. To upload large files, this value must be larger than upload_max_filesize
post_max_size = 3M
------
Para entrar en modo administrador:
localhost:xxxx/wordpress/wp-admin
------
https://docs.oracle.com/javase/tutorial/i18n/intro/steps.html
------
https://neliosoftware.com/es/blog/wordpress-multiidioma/
------
https://www.webempresa.com/hosting-wordpress-ciudadano2.html?utm_medium=affiliate&utm_source=1295&utm_campaign=Afiliados
------
https://forums.virtualbox.org/viewtopic.php?t=52826
------
http://blog.techprognosis.com/how-to-enable-dhcp-in-virtualbox-4/
------ fuentes
https://www.myfonts.com/WhatTheFont/
https://www.whatfontis.com/
------
http://lemoncode.net/lemoncode-blog/2017/12/12/git-y-visual-studio-code
------
http://javax.mty.itesm.mx/redes2/material/Redes/ClienteServidor.htm
------
http://www.redes-neuronales.com.es/tutorial-redes-neuronales/tutorial-redes.htm
------
https://github.com/AIRLegend/Red-Neuronal
------
https://github.com/ivan-vasilev/neuralnetworks
------
https://www.journaldev.com/13121/java-9-features-with-examples
------
Spring MVC
https://zeroturnaround.com/rebellabs/java-tools-and-technologies-landscape-2016/
------
https://destaca.es/editores-visuales-wordpress/
https://wordpress.org/plugins/siteorigin-panels/
------
http://gantry.org/downloads
------
https://gist.github.com/rxaviers/7360908
------
Mobirise HTML Website Builder
------
https://www.aprenderaprogramar.com
------
https://www.youtube.com/watch?v=5iFnzr73XXk
------
https://stackoverflow.com/questions/2379197/how-to-mark-logical-sections-of-code-in-java-comments
------
https://archive.org/about/
------
http://descargacineclasico.com/
------
https://blog.desdelinux.net/comandos-arch-linux-todos-usuarios-deberian-saber/
------
http://www.tutorialspoint.com/codingground.htm
------
https://kernelpanicblog.wordpress.com/2016/07/21/manjaro-101-solucionando-algunos-errores/
------
https://unicenta.com/
------
usb-creator-gtk
------
#aptitude -r install linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') nvidia-kernel-dkms
#apt-get install nvidia-settings
------
FLATPAK
------
https://wiki.debian.org/DontBreakDebian
------
etcher
------
https://community.linuxmint.com/tutorial/view/328
------
vm.swappiness = 10
vm.vfs_cache_pressure = 50
TLP
------
https://itsfoss.com/speed-up-ubuntu-1310/
------
https://itsfoss.com/things-to-do-after-installing-ubuntu-18-04/
------
https://www.youtube.com/watch?v=RXV6FXVL6xI
------
https://itsfoss.tradepub.com/form/getting-started-with-arduino-a-beginners-guide/w_make121/prgm.cgi?sr=hicat&_t=hicat:1086
------
https://arduinobot.pbworks.com/f/Manual+Programacion+Arduino.pdf
------
http://www.dynamoelectronics.com/descargas/Arduinomanualbasico.pdf
------
https://sites.google.com/site/easylinuxtipsproject/first
------
gdebi
