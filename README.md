# EDR Incident Response — MITRE ATT&CK Mapping

Documentación de patrones de detección y respuesta a incidentes de seguridad,
basados en experiencia operativa real con CrowdStrike EDR en un entorno
corporativo multinacional. Los casos están generalizados para proteger
confidencialidad — se documenta el patrón técnico, no datos identificables
de infraestructura, cliente o empresa.

## Índice de casos

| # | Tipo de incidente | Táctica MITRE | Técnica |
|---|---|---|---|
| 01 | [Phishing / ejecución de malware](./01-phishing-malware-execution/README.md) | Initial Access / Execution | TXXXX |
| 02 | [PowerShell sospechoso](./02-suspicious-powershell-activity/README.md) | Execution / Defense Evasion | TXXXX |
| 03 | [Movimiento lateral](./03-lateral-movement-attempt/README.md) | Lateral Movement | TXXXX |
| 04 | [Acceso no autorizado](./04-unauthorized-access-attempt/README.md) | Credential Access | TXXXX |

## Metodología
Cada caso sigue esta estructura: patrón de ataque → indicadores en CrowdStrike →
técnica MITRE ATT&CK → acción de respuesta → lección aprendida.
