# Protocolos comunes

Los protocolos mas comunes son el [TCP](https://fr.wikipedia.org/wiki/Transmission_Control_Protocol) o [UDP](https://fr.wikipedia.org/wiki/User_Datagram_Protocol) pero hay muchos mas que se utilizan la pila OSI.

* **TCP** (Transmission Control Protocol) orientado a conexión, en la capa de "transporte" 
* **UDP** (User Datagram Protocol) **no orientado a conexión** y no ofrece control de errores.

## Les caractéristiques du protocole TCP

TCP (qui signifie Transmission Control Protocol, soit en français: Protocole de Contrôle de Transmission) est un des principaux protocoles de la couche transport du modèle TCP/IP. Il permet, au niveau des applications, de gérer les données en provenance (ou à destination) de la couche inférieure du modèle (c'est-à-dire le protocole IP). Lorsque les données sont fournies au protocole IP, celui-ci les encapsule dans des datagrammes IP, en fixant le champ protocole à 6 (Pour savoir que le protocole en amont est TCP...). TCP est un protocole orienté connexion, c'est-à-dire qu'il permet à deux machines qui communiquent de contrôler l'état de la transmission.
Les caractéristiques principales du protocole TCP sont les suivantes :

* TCP permet de remettre en ordre les datagrammes en provenance du protocole IP
* TCP permet de vérifier le flot de données afin d'éviter une saturation du réseau
* TCP permet de formater les données en segments de longueur variable afin de les "remettre" au protocole IP
* TCP permet de multiplexer les données, c'est-à-dire de faire circuler simultanément des informations provenant de sources (applications par exemple) distinctes sur une même ligne
* TCP permet enfin l'initialisation et la fin d'une communication de manière courtoise (3 way handshake)

```
This document describes TCP, which uses TCP headers.

A TCP header, followed by any user data in the segment, is formatted as follows, using the style from [66]:

    0                   1                   2                   3
    0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |          Source Port          |       Destination Port        |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                        Sequence Number                        |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                    Acknowledgment Number                      |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |  Data |       |C|E|U|A|P|R|S|F|                               |
   | Offset| Rsrvd |W|C|R|C|S|S|Y|I|            Window             |
   |       |       |R|E|G|K|H|T|N|N|                               |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |           Checksum            |         Urgent Pointer        |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                           [Options]                           |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                                                               :
   :                             Data                              :
   :                                                               |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

          Note that one tick mark represents one bit position.
Figure 1: TCP Header Format
```  
cf: [RFC 9293](https://datatracker.ietf.org/doc/html/rfc9293)

### Puertos TCP comunes:

* 21: [FTP](https://fr.wikipedia.org/wiki/File_Transfer_Protocol) (File Transfer Protocol) – permite la transferencia de archivos entre sistemas.
* 22: [SSH](https://fr.wikipedia.org/wiki/Secure_Shell) (Secure Shell) – un protocolo de red seguro que permite a los usuarios conectarse y administrar sistemas de forma remota.
    - Cf: [Bandit lvl 13](https://overthewire.org/wargames/bandit/bandit14.html)
* 23: [Telnet](https://fr.wikipedia.org/wiki/Telnet) – un protocolo utilizado para la conexión remota a dispositivos de red.
    - Cf: [Meow (HTB)](/lunarDocs/tiers0/meow/) 
* 80: [HTTP](https://fr.wikipedia.org/wiki/Hypertext_Transfer_Protocol) (Hypertext Transfer Protocol) – el protocolo que se utiliza para la transferencia de datos en la World Wide Web. [rfc9110 'HTTP Semantics'](https://www.rfc-editor.org/rfc/rfc9110#name-syntax-notation)
* 443: [HTTPS](https://fr.wikipedia.org/wiki/Hypertext_Transfer_Protocol_Secure) (Hypertext Transfer Protocol Secure) – la versión segura de HTTP, que utiliza encriptación [SSL](https://fr.wikipedia.org/wiki/Transport_Layer_Security)/TLS para proteger las comunicaciones web.

## Les caractéristiques du protocole UDP

Le protocole [UDP](https://fr.wikipedia.org/wiki/User_Datagram_Protocol) (User Datagram Protocol) est un protocole non orienté connexion de la couche transport du modèle TCP/IP. Ce protocole est très simple étant donné qu'il ne fournit pas de contrôle d'erreurs (il n'est pas orienté connexion...).

```
The pseudo  header  conceptually prefixed to the UDP header contains the
source  address,  the destination  address,  the protocol,  and the  UDP
length.   This information gives protection against misrouted datagrams.
This checksum procedure is the same as is used in TCP.

                  0      7 8     15 16    23 24    31
                 +--------+--------+--------+--------+
                 |          source address           |
                 +--------+--------+--------+--------+
                 |        destination address        |
                 +--------+--------+--------+--------+
                 |  zero  |protocol|   UDP length    |
                 +--------+--------+--------+--------+
```
L'en-tête du segment UDP est donc très simple : voir sur la [RFC 768](https://datatracker.ietf.org/doc/html/rfc768)

### Puertos UDP comunes:

* 53: [DNS](https://es.wikipedia.org/wiki/Sistema_de_nombres_de_dominio) (Domain Name System) – un sistema que traduce nombres de dominio en direcciones IP.
* 67/68: [DHCP](https://es.wikipedia.org/wiki/Protocolo_de_configuraci%C3%B3n_din%C3%A1mica_de_host) (Dynamic Host Configuration Protocol) – un protocolo utilizado para asignar direcciones IP y otros parámetros de configuración a los dispositivos en una red.
* 69: [TFTP](https://es.wikipedia.org/wiki/TFTP) (Trivial File Transfer Protocol) – un protocolo simple utilizado para transferir archivos entre dispositivos en una red.
* 123: [NTP](https://es.wikipedia.org/wiki/Network_Time_Protocol) (Network Time Protocol) – un protocolo utilizado para sincronizar los relojes de los dispositivos en una red.
* 161: [SNMP](https://es.wikipedia.org/wiki/Protocolo_simple_de_administraci%C3%B3n_de_red) (Simple Network Management Protocol) – un protocolo utilizado para administrar y supervisar dispositivos en una red.

## Mas lejos con protocolos

Para entrar a jugar con protocolos, es decir si haces algun tool o quieres ver cosas sobre protocolos en linea de comandos, hay una lib en Python llamada [Scapy](https://scapy.readthedocs.io/en/latest/introduction.html#) (Scapy is a Python program that enables the user to send, sniff and dissect and forge network packets.)

Un ejemplo de como utilizarlo, aqui forjamos un paquete IP (capa 3) y lo enviamos al router, luego vamos a encapsular una traza ICMP y ver que nos devuelve; un ping casero que nos permite ver el [encabezado ICMP](https://es.wikipedia.org/wiki/Protocolo_de_control_de_mensajes_de_Internet#Cabecera_ICMP)

```bash
❯ sudo scapy -H
[sudo] Mot de passe de rnek0 : 
Welcome to Scapy (2023.03.29) using IPython 8.11.0
>>> a=IP(ttl=10)
>>> a.src
'127.0.0.1'
>>> a
<IP  ttl=10 |>
>>> a.dst="192.168.1.1"
>>> a
<IP  ttl=10 dst=192.168.1.1 |>
>>> a.src
'192.168.1.19'
>>> a.dst
'192.168.1.1'
>>> send(a/ICMP())
.
Sent 1 packets.
>>> p = sr1(a/ICMP())
Begin emission:
Finished sending 1 packets.

Received 1 packets, got 1 answers, remaining 0 packets
>>> p.show()
###[ IP ]### 
  version   = 4
  ihl       = 5
  tos       = 0x0
  len       = 28
  id        = 32331
  flags     = 
  frag      = 0
  ttl       = 64
  proto     = icmp
  chksum    = 0x7931
  src       = 192.168.1.1
  dst       = 192.168.1.19
  \options   \
###[ ICMP ]### 
     type      = echo-reply
     code      = 0
     chksum    = 0xffff
     id        = 0x0
     seq       = 0x0
     unused    = ''
###[ Padding ]### 
        load      = '\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00'
```

Una miradita con nuestro amigo [wireshark](https://www.wireshark.org/docs/) : 

Aqui vemos el ttl de 10 que le pusimos al envio (por ejemplo)

![ICMP y Wireshark1](../assets/icmp1.png)

Aqui mas cosillas como la encapsulacion de icmp dentro de ip para nuestro ping casero.

![ICMP y Wireshark2](../assets/icmp2.png)

Para acabar con el tema que da para largo, un enlace para ver como se vé el protocolo TCP desde un punto de vista de desarrollador con [C y sockets](https://broux.developpez.com/articles/c/sockets/#LIII-A) :fr:

---
