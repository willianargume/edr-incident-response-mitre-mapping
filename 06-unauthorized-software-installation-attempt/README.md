# Intento de instalación no autorizada con escalamiento de privilegios

## Contexto
Un usuario final intentó instalar una herramienta de administración de bases
de datos en su equipo corporativo, a pesar de que la política organizacional
restringe instalaciones de software para perfiles de usuario estándar. El
instalador requería permisos de administrador y, pese al bloqueo, generó una
tarea programada como mecanismo de ejecución, lo cual fue detectado por
CrowdStrike EDR y disparó la alerta.

## Indicadores detectados (CrowdStrike EDR)
- Ejecución de instalador de software no autorizado por un perfil sin
  privilegios administrativos
- Creación de tarea programada (scheduled task) por el proceso del instalador
  como intento de bypass de la restricción de instalación

## Mapeo MITRE ATT&CK

| Táctica | Técnica | Código |
|---|---|---|
| Privilege Escalation | Scheduled Task/Job: Scheduled Task | T1053.005 |

## Respuesta / Acción tomada
Se identificó al usuario y equipo origen de la alerta, se validó que el
perfil del usuario no correspondía al uso de esa herramienta y que el
software no está diseñado ni soportado para ejecutarse en equipos finales.
Se concientizó al usuario sobre la política de instalación de software y
los riesgos de seguridad asociados a permisos administrativos en endpoints.

## Investigación y resultado
Se determinó que el usuario tenía una necesidad legítima de trabajo (acceso
a base de datos), pero la vía elegida no era la correcta. Como solución, se
le otorgó acceso a un servidor on-premise de SQL mediante usuario propio,
permitiéndole conectarse de forma remota desde su equipo final usando una
herramienta cliente de administración (SQL Server Management Studio), sin
necesidad de instalar el motor de base de datos localmente ni requerir
privilegios administrativos en su endpoint.

## Lección aprendida
Los intentos de instalación no autorizada no siempre son maliciosos —
frecuentemente reflejan una necesidad operativa real sin la vía adecuada
para resolverla. Ofrecer una alternativa sancionada (acceso remoto
controlado a un servidor on-premise) resuelve la necesidad del usuario sin
comprometer la postura de seguridad del endpoint, reduciendo el riesgo de
que el usuario busque vías no sancionadas en el futuro.
