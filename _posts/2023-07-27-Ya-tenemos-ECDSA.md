---
title: Ya tenemos ECDSA 
date: 2023-07-27 11:13:00 +0000
categories: [MaxiNET]
tags: [dns]
pin: false
toc: false
---
Hace unas horas se ha completado la implementación de **ECDSA** en [**DNSSEC**](https://es.wikipedia.org/wiki/DNSSEC) para el dominio maxinet.es, probablemente para este dominio no era necesario, al fin y al cabo, no presto ningún tipo de servicio en el que debe garantizar la integridad de los registros DNS pero bueno, si la tecnología está disponible y se puede usar... **¡adelante!**

**ECDSA** (*ECDSAP256SHA256*) proporciona una serie de ventajas sobre el algoritmo de firma RSA (*RSASHA256*) que actualmente utiliza [**DNSSEC**](https://es.wikipedia.org/wiki/DNSSEC), incluyendo:
- **Mayor seguridad**: ECDSA es más resistente a los ataques de fuerza bruta que RSA.
- **Mayor flexibilidad**: ECDSA se puede implementar en múltiples plataformas, incluyendo hardware de bajo coste.
- **Mayor eficiencia**: ECDSA utiliza claves más pequeñas, esto reduce los tiempos y recursos computacionales.

**Comprobación de la validación:**
```shell
maxi@dktna:~$ delv @1.1.1.1 maxinet.es
; fully validated
maxinet.es.             300     IN      A       188.114.96.5
maxinet.es.             300     IN      A       188.114.97.5
maxinet.es.             300     IN      RRSIG   A 13 2 300 20230728135813 20230726115813 34505 maxinet.es. bEY/D6dRAhZzBlnqrdM8/orjHpXkdJed6d8zZfbF8LO34xiP4gv6pIDA tGvKMSwP8jprb6ZaglADDn2f/8zNVA==
```
{: .nolineno }

Ahora, pese a que la zona raíz y el dominio `.es` utilizan **RSASHA256** para las firmas [**DNSSEC**](https://es.wikipedia.org/wiki/DNSSEC), maxinet.es usa el algoritmo **ECDSAP256SHA256**.

![DNSSCE - maxinet.es](dnssec-maxinetes.png)
_Análisis del dominio maxinet.es_

Para saber si tu dominio cuenta con [DNSSEC](https://es.wikipedia.org/wiki/DNSSEC) existen varias herramientas en Internet que te lo permiten como:
- [DNSSEC-Analyzer](https://dnssec-analyzer.verisignlabs.com/)
- [DNSCViz](https://dnsviz.net/)