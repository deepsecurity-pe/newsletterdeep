---
layout: post
title: "Criptominería en Dockers mal configurados"
author: zero
categories: [Cryptocurrency]
tags: [Docker-API]
image: assets/images/docker-api-mineria-01.jpg
rating: 4.5
---

Investigadores de Trend Micro han detectado una campaña que aprovecha instancias de Docker con APIs expuestas para desplegar mineros de criptomonedas de forma encubierta.



## Explotación de APIs expuestas  
Los atacantes inician el ataque consultando la API de Docker en busca de contenedores activos. Si no encuentran ninguno, crean uno basado en la imagen Alpine y montan “/hostroot”, es decir la raíz del sistema anfitrión, como volumen. Esta configuración permite al contenedor escapar al host y modificar archivos críticos.



## Configuración de Tor como capa de anonimato  
Mediante un script Base64, el adversario instala Tor dentro del contenedor y configura ‘socks5h’ para dirigir todo el tráfico y las resoluciones DNS a través de una dirección .onion. Esto oculta el origen de las conexiones cuando se descarga y ejecuta un payload remoto desde dominios ocultos.



## Persistencia y herramientas de apoyo  
Tras la creación del contenedor, el malware despliega “docker-init.sh” para habilitar el acceso SSH como root, añadiendo una clave controlada por el atacante. Luego instala utilidades como masscan, libpcap, zstd y torsocks, y envía información del sistema al C&C antes de colocar el dropper de XMRig con la configuración de minería y direcciones de wallet.



## Riesgos y recomendaciones  
Esta táctica ha afectado a empresas tecnológicas, financieras y del sector salud, donde la alta utilización de CPU puede pasar desapercibida si el atacante ajusta sus tasas de hash. Para mitigar el riesgo, se aconseja:
- Deshabilitar el acceso remoto a la API de Docker o restringirlo mediante TLS y autenticación.  
- Monitorear la creación de contenedores y los volúmenes montados potencialmente peligrosos.  
- Inspeccionar procesos de red para detectar conexiones a nodos Tor y actividad inusual de SSH. 
