# AMISR14 TUTORIAL
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

# NOTAS PARA EL MONITOREO AMISR 14
---
1. Verificar la aquisicion de datos con la hora actual en el directorio correspondiente, se debe estar generando un archivo cada minuto.
2. El Panel de control debe estar en verde, de esta manera se comprueba que no existen alarmas o fallos en el radar.
3. El nivel de potencia debe mantenerse a lo largo de todo el experimento, debemos anotar el nivel de potencia inicial y verificar en cada monitoreo que la potencia es bastante parecida.
4. El monitoreo se puede realizar a través de la pagina de Realtime, el grafico Noise puede retrasarse unos minutos dependiendo de las integraciones, por ejemplo:
   * Integración 1 min, delay aproximado 3 min.
   * Integracion 5 min, delay aproimado 10-12 min.
5. Durante la ejecución de un experimento o turno , debemos deshabilitar las tareas relacionados a la programacion del atenuador, estas tareas van de la mano con 5 archivos que se ejecutan a las 6,7 am y mediodia, noche.
   * En operacion continua o normal se deben habilitar la ejecucion automatica de las tareas con sus respectivos  archivos.
   * Si hay error se va a notar con una caida de potencia por unos minutos.
6. Para la operacion continua y correcto funcionamiento se recomienda realizar una limpieza de filtros
7. La limpieza de la fuente, filtros y mantenimiento oportuno evita las alarmas por temperatura en el radar.

# PROCESAMIENTO PARA INVESTIGADORES
1. Juan Pablo.
   * /home/soporte/Desktop/scripts/2024/python
   * esf_merge_snrDays.py
2. Marco
   * /home/soporte/Desktop/scripts/2024/Turnos/ISR_Mayo
   * isr_offline.py
3. Fabiano
   * /home/soporte/Desktop/scripts/2024/bash/esf_offline.sh
   * Envia los datos de potencia al servidor de Fabiano: /home/soporte/Desktop/scripts/2024/python/ryncToDallas.py
   * Contactar a Jose Maria en caso problemas de conexion con el servidor y datos.
# REALTIME EXPERIMENTO ACTUAL 14/05/2024
* /home/soporte/Desktop/scripts/2024/Turnos/ISR_Mayo
* isr_online.py

# OPERACION CONTINUA - SCHEDULED TASKS

START-> ALL PROGRAM -> ACCESORIES -> SYSTEM TOOLS ->  SCHEDULED TASKS
* 5 PROGRAMAS QUE DEBEN SER HABILITADOS DESPUES DE LOS TURNOS PARA OPERACION DIARIA O CONTINUA DE AMISR.
   - attenuator_right
   - attenuator_map3
   - attenuator_map2
   - attenuator_map1
   - attenuator_day


  # OPERACION CONTINUA DE AMISR

  1. INGRESAR A LA PC DE ADQUISICION
  2. Ubicar el directorio C:\Documents and Settings\radar\Desktop\scripts
  3. Activar el programa attenuate_radar2.py hasta observar el mensaje starting steady
  4. En la dtc0, apretamos Record, esperamos , Run , esperamos , RF , esperamos y apretamos Abort Experiment.
  5. Luego volvemos a ejecutar attenuate_radar2.py hasta observar el mensaje starting steady
  6. Apretamos el boton dentro la opcioens system de Manual para pasar a la configuracion automatica.
  7. Despues de esto nos vamos a el menu Start -> All Programs -> Accesorios -> System Tools -> Scheduled Tasks. Aqui activamos los 5 programas:
      * attenuator_night
      * attenuator_map3
      * attenuator_map2
      * attenuator_map1
      * attenuator_day
      Doble click y luego check en Enabled(Scheduled task runs at specified time)
  8. Ahora entramos a la PC de procesamiento.
  9. Descomentamos las siguiente lineas de codigo
     # m h  dom mon dow   command

     58 17 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/killing_schain.sh
     ##  #05 18 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/isr_offline.sh
     07 18 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_online.sh
     #
     58 06 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/killing_schain_SYNC.sh
     01 07 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_offline.sh
     ##  #01 12 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/esf_offline_snr.sh
     07 07 * * * export DISPLAY=:0 && /home/soporte/Desktop/scripts/2024/bash/isr_online.sh

