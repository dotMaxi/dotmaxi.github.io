---
title: Papelera de reciclaje en bash
date: 2004-10-14 14:00:00 +0000
categories: [GNU/Linux]
tags: [scripting, bash, linux]
---
Eduardo Suarez, corresponsal de guerra en Pakistán… es broma!! es un amigo mío que se le vio el detalle de ofrecerme una joyita de script para Linux. Pensé buab! vamos a publicárselo que le hace ilusión al chico. El script consiste en una papelera de reciclaje.

El script está documentado y dedicado :)
```bash
#!/bin/bash
#AUTOR: Eduardo Luis Suarez Lorenzo
#Programa que simula una papelera de reciclaje. Envia los archivos indicados como #parametros a un directorio oculto para dar la posibilidad de restaurarlos en otro momento.

	if test $# -lt 1 #comprueba que el numero de argumentos no sea menor que 1
	then		  #en caso contrario sale del programa
		echo "Error. Faltan argumentos"
		echo "Uso: mirm [-l][-r][-h] fichero [fichero,...]"
		exit 1
	fi

	if test ! -d /$HOME/.papelera #comprueba si el directorio que hara de
	then				#papelera exista, y si no lo crea
		mkdir /$HOME/.papelera
	fi

	while getopts lrh opts $* #se utiliza para definir los posibles
	do			   #parametros funcionales del script
		case $opts in

	#en el caso de que como parametro se introduzca -l se mostrara un listado
	#de los ficheros contenidos en la papelera
		l) echo "LISTADO DE ARCHIVOS DE LA PAPELERA DE RECICLAJE"
		   echo
		   for i in /$HOME/.papelera/* #toma todas las entradas del
		   do				#directorio
			echo "$i"   #muestra la entrada actual
		   done
		   exit 1;; #sale del script

	#en caso de que el parametro sea -r se borrar el contenido de la papelera

		r) read -p "Esta seguro de que desea vaciar la papelera? (s/n):" resp	#se pide confirmacion para la eliminacion de los archivos.
		   case $resp in

			s|S)rm -r /$HOME/.papelera/* 2>/dev/null #si la respuesta 
#"s" o "S" se eliminaran los archivos, y si la papelera ya esta vacia se ocultara 
#el error.
		   	    echo "Se ha vaciado la papelera."
			    exit 1;;
			n|N)exit 1;;#si la respuesta es "n" o "N" saldra del script
		   esac;;

		h) echo "Argumentos de $0:" #si el argumento es -h se mostrara
		   echo			     #una ayuda de la utilizacion
		   echo "[-l] -> Lista el Contenido de la Papelera"
		   echo "[-r] -> Borra todo el Contenido de la Papelera"
		   exit 1;; #sale del script
#en el caso de que el argumento introducido no sea ninguno de los anteriores se #muestra un mensaje de error y sale del script
		*) echo "Error. Opcion incorrecta"
		   exit 1;;

		esac
	done
#si los parametros introducidos se corresponden con archivos con su ruta absoluta
#se pedira confirmacion de eliminacion
	read -p "Esta seguro de qu desea borrar los archivos?(s/n):" resp

	case $resp in

	s|S) for i in $* #si la respuesta es "s" o "S"
	     do
		if test -f $i #se comprueba que los archivos existan
		then
			mv $i /$HOME/.papelera #si existen se mueven a la papelera
			echo "Borrando $i..."
		else
			echo "Error. El Fichero $i no se encuentra en la ruta especificada" #si no existen se muestra un mensaje de error.
		fi
	     done;;

	n|N) echo "Los Archivos no han sido borrados" #si la respuesta es "n" o "N" se sale del script
	     exit 1;;
	esac

# este script va dedicado pa maxi un xiko reciklado a la par q retractil. Un beso! :)~
```