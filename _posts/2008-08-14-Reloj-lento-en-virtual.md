---
title: Reloj lento en virtual
date: 2008-08-14 11:30:00 +0000
categories: [How-to]
tags: [howto, vmware]
pin: false
toc: false
---
Llevaba varios días tranquinando con una máquina virtual en VMware. Había instalado un Centos 5.2 y estaba teniendo problemas con la hora del sistema.

Volvía a poner la hora bien y al cabo de 5 minutos se iba quedando retrasado. Un segundo dentro de la máquina virtual no duraba lo mismo que en la máquina física.

Empecé a buscar información en la Web de VMware hasta que encontré que había que indicarle al final de la linea de carga del Kernel lo siguiente:

`clock=pit nosmp noapic nolapic``

Reinicié la máquina y funcionó :)