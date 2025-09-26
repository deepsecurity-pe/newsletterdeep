---
layout: post
title: "Salt Typhoon explota vulnerabilidad en Cisco IOS XE para espiar telecoms Canadiences"
author: zero
categories: [APT]
tags: [Cisco IOS XE]
image: assets/images/salt-typhoon-01.jpg
rating: 4.5
---

El Canadian Centre for Cyber Security y el FBI han emitido una advertencia sobre una operación de espionaje donde actores vinculados a China han comprometido dispositivos de red de un operador de telecomunicaciones en Canadá.



## Explotación de Cisco IOS XE  
Los atacantes aprovecharon sla vulnerabilidad CVE-2023-20198 (CVSS 10.0) en Cisco IOS XE para extraer archivos de configuración de tres dispositivos en febrero de 2025. Modificaron al menos uno de los ficheros para establecer un túnel GRE y capturar tráfico de la red interna.



## Persistencia y reconocimiento de red  
Según las agencias, las actividades iniciales se centraron en reconocimiento, aunque la puerta abierta podría servir para comprometer otros sistemas. Los dispositivos edge siguen siendo puntos de entrada prioritarios para mantener acceso continuo a infraestructuras críticas.



## Coincidencias con informes anteriores  
Recorded Future documentó la explotación de CVE-2023-20198 y CVE-2023-20273 contra proveedores de telecom e ISPs en EE.UU., Sudáfrica e Italia. En esos casos también se desplegaron túneles GRE para exfiltrar datos y asegurar un canal de largo plazo.



## Contramedidas urgentes  
Se recomienda aplicar sin demora los parches de Cisco IOS XE, restringir el acceso al plano de gestión de los routers y auditar configuraciones de GRE en la infraestructura. El monitoreo continuo de cambios en archivos de configuración es esencial para detectar inyecciones no autorizadas.
