#!/bin/bash

menu (){

clear
	echo "1-comprimir"
	echo "2-descomprimir"
	echo "0-salir"
read opcion
}

###COMPRIMIRs###

comprimir (){
	echo "INTRODUZCA ARCHIVO A COMPRIMIR"
	read archivo
	echo "INTRUDUZCA LA CARPETA DEL ARCHIVO"
read carpeta

        cd $carpeta 2>>/tmp/error.txt

if [ $archivo ]
	then
tar -czvf $archivo.tgz $archivo
else
	echo "EL $archivo NO SE PUEDE COMPRIMIR"
fi
}

###DESCOMPRIMIR###


descomprimir (){ 
        echo "INTRODUZCA FICHERO A DESCOMPRIMIR"
	read archivo
	echo "INTRUDUZCA LA CARPETA DEL ARCHIVO"
read carpeta

       cd $carpeta 2>>/tmp/error.txt

	if [ $archivo ]
	then
	tar -xzvf $archivo
else 
	echo "EL $archivo NO SE PUEDE DESCOMPRIMIR"
fi
}


###OPCIONES###

	opciones (){
	case $funcion in
	1)comprimir;;
	2)descomprimir;;
	0)salir 0;;
esac
}


	while true
do
###MENU###
 menu
	if [ $funcion -le 2 ] && [ $funcion -ge 0 ] 
then
	opciones
	else  echo "ELIGA UNA OPCION"
fi
	read -p "PRESIONE UNA TECLA PARA CONTINUAR"
done
