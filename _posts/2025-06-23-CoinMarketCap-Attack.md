---
layout: post
title: "Alerta Web3: ataque a la cadena de suministro de CoinMarketCap drena carteras con popup falso"
author: zero
categories: [ Cryptocurrency ]
tags: [ CoinMarketCap, Supply Chain Attack, Wallet Drainer ]
image: assets/images/cryptocurrency-01.jpg
rating: 4.5
---
Alerta Web3: ataque a la cadena de suministro de CoinMarketCap drena carteras con popup falso## Resumen del incidente

El 20 de junio de 2025, visitantes de **CoinMarketCap** comenzaron a ver un popup Web3 inesperado solicitando la conexión de sus carteras. Al aceptar, un script malicioso sustraía de inmediato los fondos. La firma de seguridad **c/side** y el propio equipo de CoinMarketCap confirmaron que se trató de un **ataque a la cadena de suministro**, no de un acceso directo a sus servidores.

## Vector de ataque: doodle comprometido

Los atacantes explotaron una vulnerabilidad en el API que sirve la imagen “doodle” de la página principal:

1. Alteraron la respuesta JSON del servicio de doodle para incluir una etiqueta `<script>`.  
2. El script malicioso cargaba un **wallet drainer** desde `static.cdnkit[.]io`.  
3. Al renderizarse, mostraba un popup idéntico al legitimo de Web3 para engañar al usuario.

Esta táctica demuestra cómo un recurso aparentemente benigno puede convertirse en puerta de entrada.

## Funcionamiento del wallet drainer

Una vez que la víctima conectaba su cartera:

- El código solicitaba permisos para firmar transacciones.  
- Inmediatamente transfería el saldo al monedero del atacante.  
- Ocultaba la maniobra con animaciones y mensajes simulando actividad normal.

Según datos filtrados en un canal de Telegram, los operadores obtuvieron unos **US$ 43 266** de 110 usuarios antes de ser neutralizados.

## Detección y contramedidas

CoinMarketCap actuó con rapidez:

- Bloqueó el endpoint del doodle y retiró la imagen comprometida.  
- Aisló los recursos de terceros y reforzó la validación de payloads JSON.  
- Declaró todos los sistemas “operativos y seguros” tras una auditoría interna.

## Contexto y tendencias

Los **wallet drainers** robaron cerca de **US$ 500 M** en 2024 de más de 300 000 direcciones, usando:

- Sitios clonados y anuncios maliciosos.  
- Extensiones de navegador contaminadas.  
- Campañas en redes sociales con enlaces de phishing.

Mozilla ya implementó mecanismos en su repositorio de complementos para detectar estos drainer scripts.

## Recomendaciones de seguridad

1. Emplear **hardware wallets** para validar transacciones fuera del navegador.  
2. Activar **CSP** (Content Security Policy) que restrinja la carga de scripts externos.  
3. Verificar el origen de los recursos en la consola de desarrollador antes de interactuar.  
4. Evitar conectar carteras en popups inesperados o sin HTTPS válido.  
5. Mantener navegadores y extensiones auditados y actualizados.
