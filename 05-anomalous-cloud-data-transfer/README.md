# Transferencia masiva de datos desde almacenamiento en la nube (Falso Positivo)

## Contexto
CrowdStrike EDR generó una alerta de alta severidad por volumen anómalo de
descarga de archivos desde un servicio de almacenamiento en la nube (Dropbox)
hacia un endpoint corporativo. La política de seguridad configurada aisló
el equipo de forma automática antes de que el analista recibiera la alerta,
dejándolo sin salida a internet.

## Indicadores detectados (CrowdStrike EDR)
- Volumen de descarga fuera del patrón habitual del usuario
- Actividad sostenida de transferencia de archivos desde servicio cloud de terceros
- Aislamiento automático de endpoint disparado por política de contención

## Mapeo MITRE ATT&CK

| Táctica | Técnica | Código |
|---|---|---|
| Collection | Data from Cloud Storage | T1530 |

## Respuesta / Acción tomada
El equipo ya se encontraba aislado al momento de recibir la alerta (contención
automática). Se coordinó con el usuario y su línea de reporte para entender
el contexto de la actividad antes de tomar acciones adicionales, en lugar de
asumir intención maliciosa solo por el volumen de la descarga.

## Investigación y resultado
Se determinó que la descarga correspondía a una migración planificada:
el usuario estaba respaldando su información de Dropbox hacia SharePoint,
ya que la plataforma Dropbox sería dada de baja organizacionalmente en los
meses siguientes. **Veredicto: falso positivo — actividad legítima de negocio.**
El equipo fue liberado del aislamiento tras validar el contexto.

## Lección aprendida
No toda alerta de volumen anómalo implica exfiltración maliciosa. Es clave
correlacionar el comportamiento detectado con el contexto operativo del
usuario (cambios de plataforma, migraciones planificadas) antes de escalar
como incidente confirmado. Este caso reforzó la importancia de tener
comunicación fluida entre el equipo de seguridad y las áreas de negocio para
reducir fricción en migraciones legítimas sin debilitar la postura de
detección.
