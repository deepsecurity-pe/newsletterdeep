---
layout: post
title: "Desactivan Botnets de criptominería con bad shares y XMRogue "
author: zero
categories: [ Cryptocurrency ]
tags: [ XMRogue ]
image: assets/images/xmrogue-disrupcion-01.jpg
rating: 4.5
---

Un informe de Akamai Security detalla dos métodos para desestabilizar botnets dedicadas a la minería de criptomonedas, aprovechando la topología de Stratum y las políticas de los pools usados por los crypto-miners .



## Explotando malas participaciones para vetar proxies  
La primera técnica, conocida como bad shares, conecta un cliente controlado por el defensor al proxy de minería del atacante y envía resultados de trabajo inválidos. El pool termina por banear el proxy tras recibir múltiples shares erróneas, lo que provoca que la tasa de hash de la botnet caiga de 100 % a 0 % y paraliza por completo la operación.



## XMRogue: emulación de minero para forzar el baneo  
Para automatizar el proceso, los investigadores emplean XMRogue, una herramienta que simula la actividad de un minero legítimo. XMRogue se conecta al proxy objetivo, introduce secuencias de bad shares y provoca el bloqueo del proxy en el pool, convirtiendo este componente en un punto único de falla.



## Inhabilitación de wallets por exceso de conexiones  
El segundo método ataca escenarios sin proxy, donde el minero se conecta directamente a un pool público. Al generar más de 1.000 inicios de sesión concurridos con la misma dirección de wallet, el pool aplica un baneo temporal de una hora, interrumpiendo la minería hasta que el atacante reconfigure su infraestructura.



## Amplitud del enfoque y limitaciones  
Aunque las pruebas se han centrado en Monero, las técnicas se extienden a otros activos compatibles con el protocolo Stratum. Los mineros legítimos recuperan rápidamente el servicio cambiando IP o wallet, mientras que los operadores de botnets deben rehacer gran parte de su red para eludir estas defensas.
