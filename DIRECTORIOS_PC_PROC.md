
# DIRECTORIOS EN LA PC DE PROCESAMIENTO AMISR  - UPDATE 30/05/2024
---

* Servidor: 10.10.40.122
* Usuario: soporte
* Contraseña: soporte


## ADQUISICION AMISR-JULIA:

Este directorio es el path de lectura de los programas  isr_online.py, isr_offline.py, esf_online.py y esf_offline.py

DIRECTORIO: /mnt/data_amisr

soporte@IGP-153:/mnt/data_amisr$ ls

20240512.005  20240521.003  20240522.002  20240523.001  20240523.005  20240524.004\
20240513.009  20240521.004  20240522.003  20240523.002  20240524.001  20240524.005\
20240521.001  20240521.005  20240522.004  20240523.003  20240524.002  20240527.001\
20240521.002  20240522.001  20240522.005  20240523.004  20240524.003


## EL DISCO ESTA MONTADO COMO SE APRENCIA EN LA SIGUIENTE FIGURA:
$ df -h
//192.168.10.20/data  932G  400G  533G  43% /mnt/data_amisr

# PROCESAMIENTO

Los datos procesados de ISR Y ESF se encuentran en el siguiente directorio:

$ cd /mnt/DATA/AMISR14/2024/

$ ls

EEJ  ESF  ISR  MET

# DISCO EXTERNO TOSHIBA

Este disco esta montado e el siguiente directorio:

/dev/sdb2             3.7T  2.9T  829G  78% /media/soporte/TOSHIBA EXT1 


## DISCO EXTERNO - USOS

El disco externo TOSHIBA se utiliza para copiar los datos del directorio de adquisicion /mnt/data_amisr y darle la alternativa de tener mas espacio y no interrumpir
la adquisicion y grabado de datos.  El disco de adquisicion solo tiene un espacio de 932 Gb es importante revisar que le disco no se llene. Por eso se recomienda
despues de procesar mover la data a el disco externo.

### REVISION DE DATOS AMIR- TORMENTA - DIAS 10 Y 11 DE MAYO DEL 2024

DIA 10

soporte@IGP-153:/media/soporte/TOSHIBA EXT1/DATA_AMISR/2024$ du -sh 20240510*

27G	20240510.001 \
1.4G	20240510.002 \
31G	20240510.004 \
35G	20240510.005 


DIA 11

soporte@IGP-153:/media/soporte/TOSHIBA EXT1/DATA_AMISR/2024$ du -sh 20240511*

27G	20240511.001 \
1.4G	20240511.002 \
31G	20240511.004 \
35G	20240511.005 

