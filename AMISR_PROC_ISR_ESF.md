# REVISION DE PROCESAMIENTO Y ENTENDIMIENTO DE OPERACIONES

Nuestra referencia en este caso van a ser los experimentos de ESF Y ISR.

## CASO 1: ESF_OFFLINE.py
Este script en principio tiene los siguientes path:

- inpath='/mnt/data_amisr'
- outpath='/mnt/DATA/AMISR14/2024/ESF' 
Aqui tenemos la carpeta 2024218 por ejemplo y una imagen de rti

- path_hdf5_out='/mnt/DATA/data2Fabiano/POWER_H5_AMISR/2024'

├── ESF2024227 


│   ├── d2024227 


│   │   └── D2024227000.hdf5 


│   └── pow_20240814.png

l = startDate.split('/')
doy = str(DOY).zfill(3)

outpath1 = outPath+"/"+l[0]+doy

outpath2 = path_hdf5_out+ "/ESF"+l[0]+doy

## outPath1
opObj11 = proc_spc1.addOperation(name='RTIPlot', optype='external')
opObj11.addParameter(name='save', value=outPath1, format='str')

## outPath2
writer1 = proc_param1.addOperation(name='HDFWriter',optype='other')
writer1.addParameter(name='path', value=outPath2)
