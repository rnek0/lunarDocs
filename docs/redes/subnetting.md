# Subnetting

Imagina que tu maquina tenga que memorizar la Dirección IP de todas las maquinas de internet e igualmente el camino para llegar a ellas. Debería conservar una lista de mil millones y mucho mas de maquinas, y eso no es algo muy optimo. Para que podamos acceder a todos los dispositivos (aunque sea una cámara ip o una tostadora de red) se ha dividido la red en subredes, para que sea mas fácil de utilizar y optimizar los intercambios de información en la red, esas subredes se encargaran de atribuir las Direcciones IP para encontrar las maquinas y distribuir la información.  

Es lo mismo como cuando mandas una carta a alguien, poniendo el nombre de la ciudad, es la oficina de correo de la ciudad la que distribuye a la dirección correcta. Como sabemos, en las ciudades a menudo hay calles o avenidas que tienen el mismo nombre que en otras ciudades. Por ello en casa, en la LAN (local area network) yo puedo tener la misma IP que tu en tu casa, sin embargo la Dirección IP de tu router (el punto de entrada a tu subred en tu area local) sera una IP expuesta al exterior de la red. Ese nodo (tu router) tiene dos Direcciones IP en interfaces distintas (una para casa y otra para la calle) es decir una **ip publica** y una **ip privada**.

Por ello hace falta dos direcciones para identificar a una maquina, una para la subred y otra para la maquina en si. Pero como funciona esto si solo tenemos una dirección IP para identificar una maquina ? Pues añadiendo la dirección de la red, y como encontramos la dirección de la red ? pues con la **mascara de red**.

> La máscara de subred es un separador entre la parte de la red y la parte de la máquina de una dirección IP.  

Puedes ver tu mascara de subred en la configuración de tu tarjeta de red, por ejemplo con el comando netstat en windows o ifconfig en Linux :

```bash
$ ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.16  netmask 255.255.255.0  broadcast 192.168.1.255
```

A menudo vemos esta notación : 192.168.1.16/24 ya veremos con la mascara de subred que el 24 corresponde al numero de bits a 1.

El numero detrás del "/" es el **CIDR** (Classless Inter-Domain Routing)

Pero como utilizo la "netmask" para conocer la dirección de la red? 

Como sabemos, una IP son 32 bits separados por puntos, es decir 4 octetos separados por puntos. El mayor valor posible de 8 bits en decimal es 255, para hacer el calculo ver [en esta web](https://www.rapidtables.com/convert/number/binary-to-decimal.html) :

![Binario to decimal](../assets/binToDec-255.png "Conversion de 11111111 hacia decimal")

Podemos pues decir que nuestra mascara de red en binario es :

11111111.11111111.11111111.00000000

De la misma manera podemos convertir nuestra dirección ip de decimal a binario :

11000000.10101000.00000001.00010000

La dirección IP completa se calcula realizando un AND lógico solo con aquellos bits a 1 que indique la máscara de subred (MS). 

|  Direcciones    | Direcciones en binario               | Direcciones en decimal |  
| ------------    | ------------------------------------ | ---------------------- |  
| mascara   :     | 11111111.11111111.11111111.00000000  | 255.255.255.000        |  
| ip        :     | 11000000.10101000.00000001.00010000  | 192.168.001.016        |  
| resultado :     | 11000000.10101000.00000001.00000000  | 192.168.001.000        |  

La parte de **dirección de la subred** es : **192.168.1.0** y el nombre de maquinas permitidas sera 254

## Direcciones especificas (red y broadcast)

En la red, la primera dirección y la ultima tienen un papel particular :

* La primera est la **dirección de la red**. En nuestro ejemplo : **192.168.1.0**
* La ultima es la dirección de **broadcast**, esta dirección es la que permite transmitir a todas las máquinas de la red. Así, cuando queremos enviar información a todas las máquinas, utilizamos esta dirección. En nuestro ejemplo : **192.168.1.255**

