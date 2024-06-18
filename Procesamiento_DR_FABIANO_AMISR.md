# **PROCESAMIENTO INVESTIGADORES**
---

Investiador: Dr. Fabiano Rodriguez.

Programas para obtención de datos:

El script que se ejecuta y genera los archivo es:
/home/soporte/Desktop/scripts/2024/bash/esf_offline.sh

```
LOGFILE=$(pwd)"/LOGFILE_ESF_OFF.txt"
#Move AMISR data to RAWDATA.
#Process data
/home/soporte/anaconda3/envs/schain3/bin/python3.8 /home/soporte/Desktop/scripts/2024/python/esf_offline.py > $LOGFILE 
#Send data to ckan
/home/soporte/Desktop/scripts/2024/python/send_ckan.py -type rti
```

Este script en bash tiene dos programas python a ejecutar:

/home/soporte/Desktop/scripts/2024/python/send_ckan.py

El programa esf_merge.py generar los datos en 2 carpetas, para el **procesamiento que nos interesa nos enfocamos en el directorio path_hdf5_out**
```
inPath = '/mnt/data_amisr'
outPath = '/mnt/DATA/AMISR14/2024/ESF
path_hdf5_out= '/mnt/DATA/data2Fabiano/POWER_H5_AMISR/2024'
```
