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
El envio de los de potencia al servidor del Dr. Fabiano, se realiza ejecutando el siguiente script:

/home/soporte/Desktop/scripts/2024/python/ryncToDallas.py

El contenido del archivo se puede visualizar a continuacion:
```
import os

path_hdf5_out= '/mnt/DATA/data2Fabiano/POWER_H5_AMISR/2024/' #ruta ESF
localfolder = path_hdf5_out+"*"
remotefolder = '/mfs/io/groups/uars/amisr14/DATA_2024/'
keyPath = "/home/soporte/Documents/AMISR_SSH_KEY/AMISR14.key"
server = 'debyedata.utdallas.edu'
username = "scintpi"
port = 2222
cmd = """rsync -a --progress -e "ssh -i {} -p {}" {} {}@{}:{}""".format(keyPath,port,localfolder,username,server,remotefolder )
print("Executing command\n {}".format(cmd))
try :
    os.system(cmd)
except Exception as e:
    print(e)
```

Para ejecutar usar  el comando:

/home/soporte/anaconda3/envs/schain3/bin/python3.8 /home/soporte/Desktop/scripts/2024/python/ryncToDallas.py

