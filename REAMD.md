# AMISR TUTORIAL
---
LINK DEL MANUAL

https://docs.google.com/document/d/1rlvfqkruhY_HSygER4kBjM4mQinlJhCRRvEd5ohMy0Q/edit?usp=sharing


CONEXION REMINA PC ADQUISICION -DTC0

10.10.40.121

conexion para el Puenta de la red amisr14  red 40

$ssh -oKexAlgorithms=+diffie-hellman-group-exchange-sha1 -oHostKeyAlgorithms=+ssh-rsa -oPubkeyAcceptedKeyTypes=+ssh-rsa -i /home/operaciones/.ssh/id_rsa-umetops.txt umetops@10.10.40.121 -L 4901:localhost:80 -L 3950:dtc0:5900 -L 3941:dtc0:9000

password= amisr14

log de usuario radar para los paneles de control
password: umet14radar
---
CONEXION REMINA PC PROCESAMIENTO

password: soporte

PAGINA DE AMISR
1. PAGINA UMET AMISR / VERIFICAR ENCENDIDO START ARRAY IN TX/RX
2. PAGINA RADAC DAQ CONTROL VERIFICAR MODULOS START ARRAY IN TX/RX
3. EJECUTAR EL SCRIPT DEL ATENUADOR

DIRECTORIO DEL ARCHIVO DE ATENUADOR PC ADQUISICION

C:\Documents and Settings\radar\Desktop\scripts
attenuate_radar2.py
