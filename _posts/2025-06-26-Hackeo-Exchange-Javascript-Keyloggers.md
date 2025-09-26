---
layout: post
title: "Hackeo de credeciales en Exchange con Keyloggers en Javascript"
author: zero
categories: [Vulnerability]
tags: [ProxyShell]
image: assets/images/exchange-keylogger-01.jpg
rating: 4.5
---

Microsoft ha confirmado que servidores de Exchange expuestos en Internet, han sido infectados con código Javascript malicioso, específicamente en sus páginas de autenticación. La explotación de esta vulnerabilidad, ha permitido a distintos grupos de actores malicosos, extraer credenciales de usuarios. Dentro de la investigación, también han sido mencionadas, las tecnicas de Bypass usadas por estos actores exfiltrar información y evadir mecanismos de detección.


## Alcance del ataque en Exchange  
Un análisis de Positive Technologies reveló que al menos 65 servidores en 26 países fueron comprometidos desde 2021. Entre las víctimas se cuentan agencias gubernamentales, entidades financieras, empresas de TI e instituciones educativas.



## Mecanismo de inserción de keyloggers  
Los atacantes aprovechan vulnerabilidades conocidas de Exchange (ProxyLogon y ProxyShell) para inyectar JavaScript malicioso en la interfaz de login de Outlook. Este código actúa como keylogger y presenta dos variantes:
- Guardado local: escribe credenciales y datos de navegación en un archivo accesible vía web.  
- Exfiltración remota: envía credenciales inmediatamente a un servidor externo o a un bot de Telegram.



## Canales de exfiltración y evasión  
Para exfiltrar la información obtenida con el JavaScript malicioso, los atacantes camuflaban la información en APIKey y AuthToken en solicitudes XHR hacia un Telegram bot, algunos payloads usaban requests por POST via HTTPS y en los casos mas avanzados un túnel DNS para evadir firewalls y sistemas de detección. Con estos métodos, el tráfico de salida casi imperceptible.



## Vulnerabilidades explotadas  
Entre los CVE utilizados destacan:  
- CVE-2021-26855, CVE-2021-26857, CVE-2021-26858, CVE-2021-27065 (ProxyLogon)  
- CVE-2021-31206, CVE-2021-31207, CVE-2021-34473, CVE-2021-34523 (ProxyShell)  
- CVE-2020-0796 (SMBv3 RCE)  
- CVE-2014-4078 (IIS Security Bypass)



## Recomendaciones de mitigación  
Se aconseja aplicar todos los parches de Exchange y Windows Server, deshabilitar accesos innecesarios a OWA desde Internet y monitorear cambios en archivos estáticos de las páginas de login. La segmentación de red y la implementación de reglas de protección contra inyecciones de Javascript en los WAF, son esenciales para prevenir reinfecciones.
