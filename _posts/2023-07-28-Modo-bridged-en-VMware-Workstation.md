---
title: Modo bridged en VMware Workstation
date: 2023-07-28 11:52:00 +0000
categories: [How-to]
tags: [vmware, red, howto]
pin: false
toc: false
---
La convivencia entre VMware y Windows Sandbox siempre me ha dado algún que otro problema. Esta vez, tras la instalación de VMware Workstation 17 Pro, las máquinas arrancan sin conexión a Internet.

En la versión VMware Workstaation 17 Player, me resultaba más sencillo solucionar el problema, básicamente había que seguir los siguientes pasos:

Botón derecho sobre la máquina virtual, clic en `Settings`, sección `Network Adapter`, modo `Bridged`, y en las opciones avanzadas desmarcar todas las inferfaces de red, entre otras *Hyper-V Virtual Ethernet Adapter*, y dejar solo la interfaz de red principal del equipo. Con esto tendríamos solucionado el problema.

En la versión **VMware Workstation 17 Pro**, ha desaparecido la opción que acabo de comentar y hay que hacerlo de la siguiente manera:

Clic en `Edit` del menú principal, seleccionamos `Virtual Network Editor` y ahí es donde tenemos que seleccionar que para el modo Bridget, nuestra interfaz de red, en vez de automática, será la tarjeta de red principal del equipo.  De este modo, evitaremos que pueda coger cualquier interfaz de red que tengas, ya sea de la VPN, Windows Shadows o cualquier otra.

![VMware en modo Bridget](workstation17pro.png)
_Forzar la interfaz para el modo bridged_

Espero que te sirva de ayuda :)