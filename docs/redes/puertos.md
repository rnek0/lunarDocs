# Puertos

Muchos programas que utilizan TCP/IP se pueden ejecutar simultáneamente en Internet (por ejemplo, puedes abrir varios navegadores simultáneamente o navegar por páginas HTML mientras descargas un archivo a través de FTP, o enviar un mail). Cada uno de estos programas trabaja con un protocolo diferente, sin embargo, la computadora debe ser capaz de distinguir entre las diferentes fuentes de datos (programas).

## 65536
A cada una de estas aplicaciones se le asigna una *dirección única en la máquina*, codificada en 16 bits: **un puerto** (la combinación **dirección IP** + **puerto** es entonces una dirección única en el mundo, se llama [**socket**](https://es.wikipedia.org/wiki/Socket_de_Internet) ).

Un poco de numeración :

* 1 bit = unidad atómica, (la mas pequeña unidad binaria que represente una información)
* 1 octeto = 8 bits = 2 cifras en hexadecimal. Ejemplo de hex a bin : A = 1010 y 5 = 0101
* 16 bits = 2 octetos = 4 cifras hexa
* Puertos : 2 ^ 16 = **65536** en decimal

## Cliente / Servidor

El número de puerto indica la aplicación para la que están destinados los datos. De esta forma, cuando el ordenador recibe información con destino a un puerto, los datos se envían a la aplicación correspondiente. Si es una solicitud a la aplicación, la aplicación se denomina aplicación de **servidor**. Si es una respuesta, se denomina aplicación **cliente**.

## Clasificación de los puertos

* los números de puerto del 0 al 1023 corresponden a los puertos "bien conocidos", utilizados para los servicios de red más comunes
* los números de puerto del 1024 al 49151 corresponden a puertos registrados, asignados por la IANA
* los números de puerto del 49.152 al 65.535 corresponden a los puertos dinámicos, los cuales pueden ser utilizados para cualquier tipo de solicitudes TCP o UDP distintas a las mencionadas anteriormente.