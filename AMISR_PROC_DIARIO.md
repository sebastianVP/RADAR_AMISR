# DIRECTORIO DE PROGRAMAS

Este directorio contiene los archivos bash configurados en el crontab.
$crontab -l

```
# m h  dom mon dow   command
58 17 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/killing_schain.sh
# ojo para isr test
05 18 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/isr_offline.sh
#
07 18 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_online.sh
#
#58 06 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/killing_schain_SYNC.sh
01 07 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_offline.sh
##  #01 12 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_offline_snr.sh
07 07 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/isr_online.sh
```


Este directorio contiene los programas de ISR y ESF en modo offline y online, estos programas se ejecutan diariamente,archivos en python

```
$cd /home/soporte/Desktop/scripts/2024/python/
$ ls -l

esf_merge_snrDays.py
esf_offline.py
esf_online.py
h5_spcRead.py
isr_eej_check.py
isr_offline.py
isr_online_2.py
move_data.py
proc_isr_days.py
proc_isr.py
remove_RTIs.py
ryncToDallas.py
scanEEJ.pt
send_ckan.py
```
