 
Hasta aquí ya está el ordenador con todo funcionando, pero no tiene apenas programas, por lo que tengo un listado con el que se instalan casi todos con un comando, son los que uso yo, podeis eliminar y añadir según lo que necesiteis.

Pero en primer lugar elimino algunos que vienen que no utilizo.

`sudo apt purge kwrite xterm konqueror kwalletmanager`

Y ahora instalar:

`sudo apt install linux-headers-$(uname -r) flatpak plasma-discover-backend-flatpak gwenview krita okular kget ktorrent kdenlive korganizer kdeconnect ark kate kde-spectacle git synaptic pulseaudio pulseaudio-module-bluetooth pavucontrol bluez-firmware freecad librecad inkscape gimp firefox-esr chromium vlc audacity libreoffice libreoffice-kde5 gparted gnome-disk-utility qalculate keepassxc zim simplescreenrecorder obs-studio telegram-desktop cups timeshift samba system-config-printer build-essential cmake remmina`

Tras reiniciar:

`sudo apt install module-assistant`

Repositorio de flatpak.

`flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`

Aquí el listado un poco más claro:

## De KDE (repositorio):
- plasma-discover-backend-flatpak
- gwenview
- krita
- okular
- kget
- ktorrent
- kdenlive
- korganizer
- kdeconnect
- ark
- kate
- kde-spectacle

## Útiles necesarios (repositorio):
- linux-headers-$(uname -r)
- flatpak
- git
- synaptic
- pulseaudio
- pulseaudio-module-bluetooth
- pavucontrol
- bluez-firmware
- freecad
- librecad
- inkscape
- gimp
- firefox-esr
- chromium
- vlc
- audacity
- libreoffice
- libreoffice-kde5
- gparted
- gnome-disk-utility
- qalculate
- keepassxc
- zim
- simplescreenrecorder
- obs-studio
- telegram-desktop
- cups
- timeshift
- samba
- system-config-printer
- build-essential
- cmake
- remmina

## Varios Extra (repositorio o páginas oficiales):
- arduino
- visual studio code
- virtualbox
- processing
- fritzing
- xmind zen
- discord
- olive video editor
- kdevelop
- qtcreator


## Otros (repositorio o páginas oficiales):
- steam
- gnome-boxes (en lugar de virtualbox y vmware)
- Android studio
- scratch
- blender
- vmware
- playonlinux

## Youtube-dl

Instalar youtube-dl sin apt, porque no está actualizado al día. 

Mediante el tutorial de su [github](https://github.com/ytdl-org/youtube-dl/blob/master/README.md#how-do-i-update-youtube-dl) es de la siguiente manera.

`sudo wget https://yt-dl.org/downloads/latest/youtube-dl -O /usr/local/bin/youtube-dl`

`sudo chmod a+rx /usr/local/bin/youtube-dl`

Y para descargar los vídeos es.

`youtube-dl LINK`

Se puede descargar eligiendo la calidad (con este comando se visualiza la lista).

`youtube-dl -F LINK`

Con este se descarga (donde XXX es el número que pertenece a la calidad que queremos).

`youtube-dl -f XXX LINK`

## Configuración LibreOffice

Para tener una interfaz interesante, yo lo hago de la siguiente manera, tras tener instalado los siguientes paquetes.

`sudo apt install libreoffice-kde5 libreoffice-style-elementary`

Realizo los siguientes pasos:  
Ir a herramientas -> opciones -> libreoffice -> ver -> estilo de los iconos -> elementary.

Además de tener un tema oscuro para Plasma.

## Microcode

Hay unos paquetes que ayudan con la seguridad de los procesadores.

Para intel:

`sudo apt install intel-microcode`

Para AMD:

`sudo apt install amd-microcode`
