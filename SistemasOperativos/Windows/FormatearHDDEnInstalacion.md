Abrir CMD
Comandos:
diskpart
list disk
select disk
clean
create partition primary
format fs=NTFS "quick"	(((Donde pone NTFS se pone el formato -NTFS, FAT, FAT32- Donde pone quick se puede quitar)))
assign
exit


Desde el programa de instalación de Windows, presiona Mayús+F10 para abrir el cmd.
diskpart
list disk
select disk <disk number>
clean
convert gpt
exit