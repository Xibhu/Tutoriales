# Comandos


#### Saber paquetes (programas) disponibles para instalar por repositorios.

sudo apt-cache search PROGRAMA

#### Saber los programas instalados en derivados de debian

dpkg --get-selections > fichero
cat fichero

#### Instalar cosas en la carpeta /opt

Crear la carpeta por termianal con sudo del programa, luego darle persmisos a la carpeta

sudo chown -R $USER:$USER /opt/CarpetaPrograma

o bien

sudo chmod 777 /opt/CarpetaPrograma

#### Entrar en modo texto (Quitar interfaz)

control+alt+f1 hasta f6 (como 6 escritorios distintos)

Para volver al modo interfaz

control+alt+f7

#### Comando para cerrar forzadamente ventanas

xkill

#### Cambiar la imagen del grub.
pegar una imagen en /boot/grub/ (png preferiblemente)
sudo update-grub

#### Poder utilizar usb en Visual Studio Code para arduino

sudo adduser yourUserName dialout

#### Utilizar usb y otros permisos para VirtualBox

sudo adduser yourUserName vboxusers

#### Cambiar identificador máquina virtual

VBoxManage internalcommands sethduuid "nombrehdd.vdi"

#### Arreglar error en konsole `"Configuration file not available: "konsole.knsrc" "`
Este error se da cuando se intenta añadir nuevas apariencias a konsole.

`sudo touch /etc/xdg/konsole.knsrc` o `touch $HOME/.config/konsole.knsrc`

Y añadir el siguiente texto.

```
[KNewStuff3]
ProvidersUrl=https://download.kde.org/ocs/providers.xml
Categories=Konsole Color Schemes
TargetDir=konsole
AcceptHtmlDownloads=false
Uncompress=archive
```
