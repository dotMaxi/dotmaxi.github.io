---
title: Fix de Power Mode en Visual Studio Code
date: 2023-07-15 14:00:00 +0000
categories: [Programación]
tags: [vscode]
pin: false
---
Si has llegado hasta aquí es porque probablemente estés usando la extensión [Power Mode](https://github.com/hoovercj/vscode-power-mode) de Visual Studio Code o entraste en la Web y de casualidad caíste en este post.   

Por defecto la extensión viene acompañado con una animación que no me termina de convencer, no me refiedo al efecto de las partículas sino al movimiento hacia arriba y hacia abajo que hace que descuadre el texto de la línea actual. Aquí va un ejemplo:

![Efecto del Power Mode](https://github.com/hoovercj/vscode-power-mode/raw/master/images/demo-v3.gif)
_Efecto del Power Mode_

Para desactivar esta animación podemos hacerlo de dos maneras:
1. En la configuración de la extensión, desactivar la opción `Power Mode > Shake`.
2. En las preferencias de usuario del Visual Studio Code (`settings.jason`), añadir esta línea:
```json
"powermode.shake.enabled": false
```
