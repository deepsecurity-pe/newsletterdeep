---
layout: post
title: "El CERT-UA revela que APT28, usó Signal para distribuir BEARDSHELL y COVENANT"
author: zero
categories: [APT]
tags: [APT28]
image: assets/images/apt28-signal-01.jpg
rating: 4.5
---

El Computer Emergency Response Team de Ucrania (CERT-UA) ha alertado de una nueva campaña de ciberataques que emplea mensajes de Signal para distribuir dos familias de malware previamente desconocidas: BEARDSHELL y COVENANT.


## Vectores de acceso inicial ligados y explotación de vulnerabilidades  
CERT-UA en el 2023, atribuyó el [acceso inicial de las operaciones del APT28](https://cert.gov.ua/article/4905829) a la explotación de vulnerabilidades XSS en Roundcube, Horde, MDaemon y Zimbra, permitiendo capturar credenciales de cuentas “gov.ua”. También se aprovecharon fallos como CVE-2020-35730 y CVE-2021-44026 para tomar control de más infraestructura de las entidades gubernamentales.

## Señuelos en Signal: documentos con macros maliciosas  
En esta nueva actualización del modus-operandi del APT28, el CERT-UA reportó que los operadores de [APT28 enviaron a través de Signal](https://cert.gov.ua/article/6284080), un archivo Word (“Акт.doc”) con macros ocultas. Al autorizar la ejecución, el documento descarga un DLL malicioso (“ctec.dll”) y un PNG (“windows.png”), además de modificar el registro para cargarse junto con explorer.exe.


## BEARDSHELL y SLIMAGENT: ejecución de scripts y capturas de pantalla  
BEARDSHELL, programado en C++, descarga y ejecuta scripts de PowerShell, subiendo los resultados a través de la Icedrive API. Junto a él, SLIMAGENT toma capturas del escritorio para exfiltrar información visual de las víctimas.



## COVENANT en memoria: framework modular  
El PNG contiene shellcode que, al cargarse en memoria, activa el framework COVENANT. Este componente descarga payloads intermedios que finalmente instalan el backdoor BEARDSHELL en el sistema comprometido.



## Medidas de detección y mitigación  
Para contener la amenaza, se recomienda monitorizar conexiones a app.koofr[.]net y api.icedrive[.]net, aplicar reglas WAF contra inyecciones de scripts, y validar la integridad de páginas de login en plataformas web. La actualización e implementación de parches en los clientes de webmail, es esencial para cerrar los vectores de entrada.
