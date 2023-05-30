# Dancing

![Dancing](../img/Dancing.png)  
Windows

**Introduction**

Il existe plusieurs façons de transférer un fichier entre deux hôtes (ordinateurs) sur le même réseau. L'un de ces protocoles est étudié ici, il s'agit de **SMB** (Server Message Block). Ce protocole de communication **fournit un accès partagé aux fichiers**, aux **imprimantes** et aux **ports série** entre les terminaux d'un réseau. Nous voyons principalement des services SMB s'exécuter sur des machines Windows.  
Lors de l'analyse, nous verrons généralement le port **445 TCP** ouvert sur la cible, réservé au protocole **SMB**.

Habituellement, SMB s'exécute au niveau des couches Application ou Présentation du [modèle OSI](https://rnek0.github.io/lunarDocs/redes/modeloOSI/), illustré ci-dessous. Pour cette raison, il s'appuie sur des protocoles de niveau inférieur pour le transport. Le protocole de couche transport avec lequel le protocole Microsoft [SMB](https://fr.wikipedia.org/wiki/Server_Message_Block) est le plus souvent utilisé est [**NetBIOS**](https://fr.wikipedia.org/wiki/NetBIOS) sur **TCP/IP** (**NBT**). C'est pourquoi, lors des analyses, nous verrons très probablement les deux protocoles avec des ports ouverts en cours d'exécution sur la cible lors de la phase d'énumération.

Nous pouvons apprendre plus sur les reseaux avec le module de [htb : Introduction to Networking ](https://academy.hackthebox.eu/module/details/34), le module d'introduction au Hacking de [hack4u](https://hack4u.io/cursos/introduccion-al-hacking/) ou sur [THM](https://tryhackme.com/room/introtolan) (par exemple).

Grace au protocole SMB, une application (ou l'utilisateur d'une application) peut accéder à des fichiers sur un serveur distant, ainsi qu'à d'autres ressources telles que des imprimantes. Ainsi, une application cliente peut lire, créer et mettre à jour des fichiers sur le serveur distant. Il peut également communiquer avec n'importe quel programme serveur configuré pour recevoir une demande de client SMB.

Un stockage compatible SMB sur le réseau est appelé un **partage**, il est posible que vous en ayez vu déjà dans un explorateur windows. Ceux-ci sont accessibles par tout client disposant de l'adresse du serveur et des informations d'identification appropriées. Comme de nombreux autres protocoles d'accès aux fichiers, SMB nécessite certaines couches de sécurité pour fonctionner correctement dans une topologie de réseau. Si SMB permet aux clients de créer, de modifier, de récupérer et de supprimer des fichiers sur un partage, un mécanisme d'authentification est clairement nécessaire. Au niveau de l'utilisateur, les clients SMB doivent fournir une combinaison nom d'utilisateur/mot de passe pour voir ou interagir avec le contenu du partage SMB.

Bien qu'il ait la possibilité de sécuriser l'accès au partage, un administrateur réseau peut parfois faire des erreurs et autoriser accidentellement des connexions sans informations d'identification valides ou en utilisant des comptes invités ou des connexions anonymes. Nous en serons témoins dans les sections suivantes.

## Énumération

rhost : 10.129.39.30  
lhost : 10.10.15.253

On teste que la machine est accesible avec un ping :

```bash
--- 10.129.39.30 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2014ms
rtt min/avg/max/mdev = 28.358/29.434/31.122/1.208 ms
```

Puis on scanne la cible.  
L'exécution de la commande suivante avec **nmap** va analyser tous les ports et tenter d'afficher les versions de service pour chacun d'eux.

> -sV  : sonde les ports ouverts pour déterminer les informations de service/version  
> -vvv : augmente la verbosité des résultats dans la console (affiche plus de résultats)

```bash
❯ nmap -sV -vvv 10.129.39.30
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-20 00:37 CEST
NSE: Loaded 45 scripts for scanning.
Initiating Ping Scan at 00:37
Scanning 10.129.39.30 [4 ports]
Completed Ping Scan at 00:37, 0.06s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:37
Completed Parallel DNS resolution of 1 host. at 00:37, 0.00s elapsed
DNS resolution of 1 IPs took 0.00s. Mode: Async [#: 2, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating SYN Stealth Scan at 00:37
Scanning 10.129.39.30 [1000 ports]
Discovered open port 139/tcp on 10.129.39.30
Discovered open port 445/tcp on 10.129.39.30
Discovered open port 135/tcp on 10.129.39.30
Completed SYN Stealth Scan at 00:37, 0.52s elapsed (1000 total ports)
Initiating Service scan at 00:37
Scanning 3 services on 10.129.39.30
Completed Service scan at 00:37, 7.64s elapsed (3 services on 1 host)
NSE: Script scanning 10.129.39.30.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 00:37
Completed NSE at 00:37, 0.01s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 00:37
Completed NSE at 00:37, 0.07s elapsed
Nmap scan report for 10.129.39.30
Host is up, received echo-reply ttl 127 (0.031s latency).
Scanned at 2023-05-20 00:37:49 CEST for 8s
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE       REASON          VERSION
135/tcp open  msrpc         syn-ack ttl 127 Microsoft Windows RPC
139/tcp open  netbios-ssn   syn-ack ttl 127 Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds? syn-ack ttl 127
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.99 seconds
           Raw packets sent: 1004 (44.152KB) | Rcvd: 1001 (40.040KB)
```

* On va apliquer 45 scripts .nse (Loaded 45 scripts) qui font partie de nmap.
* Il y a un 'Ping Scan' que l'on aurait pu éviter avec -Pn ([disable host discovery](https://nmap.org/book/host-discovery-controls.html#host-enum-p0))
* Une resolution DNS (a éviter avec -n)
* Attention : ici on scanne seulement les 1000 premiers ports, si on veut tout scanner il faut -p- ou --allports

Comme mentionné précédemment, nous observons que le port **445 TCP pour SMB est opérationnel**, ce qui signifie que nous avons un **partage actif** que nous pourrions potentiellement explorer. Considérez ce partage comme un dossier accessible via Internet. Pour ce faire, nous aurons besoin des services et des scripts appropriés installés.
Afin d'énumérer avec succès le contenu partagé sur le système distant, nous pouvons utiliser un script appelé **smbclient** . 

On cherche a savoir si nous avons smbclient dans notre machine.

```bash
❯ which smbclient
/usr/bin/smbclient
❯ smbclient -V
Version 4.17.7-Debian
```

Si le script n'est pas présent sur notre machine, nous pouvons l'installer en tapant la commande suivante dans le terminal (pour les systèmes d'exploitation basés sur Debian)

```bash
sudo apt install smbclient
```

Smbclient tentera de se connecter à l'hôte distant et vérifiera si une authentification est requise. Si c'est le cas, il vous demandera un mot de passe pour votre nom d'utilisateur local. 

```bash
❯ smbclient 10.129.39.30
Password for [WORKGROUP\root]:
```

Nous devrions en prendre note. Si nous ne spécifions pas de nom d'utilisateur spécifique à smbclient lors de la tentative de connexion à l'hôte distant, il utilisera simplement le nom d'utilisateur de votre machine locale. C'est celui avec lequel vous êtes actuellement connecté à votre machine virtuelle. En effet, l'authentification SMB nécessite toujours un nom d'utilisateur, donc en ne lui en donnant pas un explicitement pour essayer de se connecter, il lui suffira de transmettre votre nom d'utilisateur local actuel pour éviter de générer une erreur avec le protocole.

Néanmoins, utilisons notre nom d'utilisateur local car nous ne connaissons aucun nom d'utilisateur distant présent sur l'hôte cible avec lequel nous pourrions potentiellement nous connecter. Ensuite, après cela, nous serons invités à entrer un mot de passe.
Ce mot de passe est lié au nom d'utilisateur que vous avez entré auparavant. En théorie, si nous étions un utilisateur distant légitime essayant de se connecter à sa ressource, nous connaîtrions notre nom d'utilisateur et notre mot de passe et nous nous connecterions normalement pour accéder à notre partage. Dans ce cas, nous n'avons pas de telles informations d'identification, donc ce que nous essaierons d'effectuer est l'une des opérations suivantes :

* Authentification des invités
* Authentification anonyme

Chacun de ces éléments nous obligera à nous connecter sans connaître la combinaison nom d'utilisateur/mot de passe appropriée et à voir les fichiers stockés sur le partage. Continuons à essayer cela. Nous laissons le champ du mot de passe vide, en appuyant simplement sur Entrée pour dire au script de continuer.

```bash
❯ smbclient -L 10.129.39.30
Password for [WORKGROUP\root]:

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      
SMB1 disabled -- no workgroup available
```

Comme toujours, nous pouvons taper le nom de notre script dans le terminal suivi du commutateur -h ou --help pour en savoir plus sur les capacités de ce script ainsi que sur son utilisation.

> [-L|--list=HOST] : Selecting the targeted host for the connection request.

Quelques exemples :  

```bash
❯ smbclient --help | grep -E "^ {1,}-L"
  -L, --list=HOST                              Get a list of shares available
❯ smbclient --help | grep -E "^ {1,}-A"
  -A, --authentication-file=FILE               Get the credentials from a file
❯ smbclient --help | grep -E "^ {1,}-D"
  -D, --directory=DIR                          Start from directory
```

En exécutant la commande ci-dessus, nous voyons que quatre partages distincts sont affichés. Passons en revue chacun d'eux et voyons ce qu'ils signifient.

* **ADMIN$** - Les partages administratifs sont des partages réseau cachés créés par la famille de systèmes d'exploitation Windows NT qui permettent aux administrateurs système d'avoir un accès à distance à chaque volume de disque sur un système connecté au réseau. Ces partages ne peuvent pas être définitivement supprimés mais peuvent être désactivés.
* **C$** - Partage administratif pour le volume de disque C:\. C'est là que le système d'exploitation est hébergé.
* **IPC$** - Le partage de communication inter-processus. Utilisé pour la communication inter-processus via des canaux nommés et ne fait pas partie du système de fichiers.
* **WorkShares** - Partage personnalisé.

Si on demande des infos avec la commande **apropos** : 

```bash
❯ apropos smbclient
libsmbclient (7)     - An extension library for browsers and that can be used as a generic browsing API.
smbclient (1)        - ftp-like client to access SMB/CIFS resources on servers
```

Il existe un outil d'aide pour linux, en dehors de **man** ou **apropos** ou **info**, qui s'appelle [tldr](https://github.com/tldr-pages/tldr). Voici ce qu'il nous dit sur smbclient :

```bash
❯ tldr smbclient

  smbclient

  FTP-like client to access SMB/CIFS resources on servers.
  More information: https://manned.org/smbclient.

  - Connect to a share (user will be prompted for password; `exit` to quit the session):
    smbclient //server/share

  - Connect with a different username:
    smbclient //server/share --user username

  - Connect with a different workgroup:
    smbclient //server/share --workgroup domain --user username

  - Connect with a username and password:
    smbclient //server/share --user username%password

  - Download a file from the server:
    smbclient //server/share --directory path/to/directory --command "get file.txt"

  - Upload a file to the server:
    smbclient //server/share --directory path/to/directory --command "put file.txt"

  - List the shares from a server anonymously:
    smbclient --list=server --no-pass
```

## Foothold

Nous allons essayer de nous connecter à chacun des partages, à l'exception du partage **IPC$**, qui n'a pas d'intérêt pour nous car il n'est pas consultable comme un répertoire normal et ne contient pas de fichiers que nous pourrions utiliser à ce stade de notre apprentissage.  Nous utiliserons la même tactique que précédemment, en tentant de nous connecter sans les les informations d'identification appropriées pour trouver des autorisations mal configurées sur l'un ou l'autre de ces partages. Nous donnerons un mot de passe pour chaque nom d'utilisateur pour voir si cela fonctionne. Tout d'abord, essayons le nom ADMIN$.

On peut également se connecter avec le flag -N (null session) si on a pas de creds. 

```bash
❯ smbclient -L 10.129.39.30 -N

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      
SMB1 disabled -- no workgroup available
```

Essai sur ADMIN$ : 

```bash
❯ smbclient \\\\10.129.39.30\\ADMIN$
Password for [WORKGROUP\root]:
tree connect failed: NT_STATUS_ACCESS_DENIED
```

La reponse est NT_STATUS_ACCESS_DENIED nous indiquant que nous n'avons pas les informations d'identification appropriées pour nous connecter à ce partage. Nous testons sur 'C$' avec le même resultat.

Même idée ici. Dernière chance. Nous tentons de nous connecter au partage SMB WorkShares personnalisé.
Cela semble être créé par l'homme, donc sujet à une mauvaise configuration.

```bash
❯ smbclient \\\\10.129.39.30\\WorkShares
Password for [WORKGROUP\root]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Mon Mar 29 10:22:01 2021
  ..                                  D        0  Mon Mar 29 10:22:01 2021
  Amy.J                               D        0  Mon Mar 29 11:08:24 2021
  James.P                             D        0  Thu Jun  3 10:38:03 2021

		5114111 blocks of size 4096. 1752038 blocks available
smb: \> 
```
Succès!  
Nous avons reussi a entrer dans ce partage et avons un prompt qui nous indique qu'on est dans un repertoire.

Le partage WorkShares SMB était mal configuré, nous permettant de nous connecter sans les informations d'identification appropriées. Nous pouvons voir notre invite de terminal changée en smb: \> , nous faisant savoir que notre shell interagit maintenant avec le service. Nous pouvons utiliser la commande **help** pour voir ce que nous pouvons faire dans ce shell.  
C'est un bon tip que de connaitre la commande help, elle peut être souvent utile.

Sur la sortie console, nous pouvons remarquer que la plupart des commandes auxquelles nous sommes habitués sous Linux sont présentes. Nous utiliserons les éléments suivants pour naviguer dans le partage :

> ls : fais un listing du contenu des répertoires dans le partage  
cd : modification des répertoires actuels dans le partage  
get : téléchargement du contenu des répertoires dans le partage   
exit : sortie du shell smb  

Taper la commande **ls** nous montrera deux répertoires, un pour *Amy.J* et un pour *James.P* . Nous visitons le premier et rencontrons un fichier appelé **worknotes.txt** , que nous pouvons télécharger à l'aide de la commande get.

Il en va de même pour le repertoire de James.P sauf qu'ici nous avons un fichier nommé flag.txt (il s'agit du drapeau a capturer) 

On peut aussi voir le contenu des fichiers à l'aide de la commande more, si on ne veut pas les télécharger.  
Pour savoir où l'on est on peu faire un pwd : 

```bash
smb: \James.P\> pwd
Current directory is \\10.129.39.30\WorkShares\James.P\
```

Une fois le shell SMB fermé, nous pouvons lire les deux documents que nous avons exfiltrés. Le document worknotes.txt semble faire allusion à d'autres services qui pourraient être exploités. Généralement, ce type de fichiers se trouve sur les machines d'une entreprise. dans les machines d'un laboratoire Hack The Box Pro, indiquant votre prochaine cible ou pouvant être être utilisés comme ressource pour une exploitation plus poussée ou un mouvement latéral au sein du laboratoire. Dans notre cas, il s'agit juste d'une preuve de concept. Nous n'aurons pas besoin de ce fichier.

Le fichier **flag.txt**, cependant, est ce que nous recherchons. Nous le lisons et entrons le drapeau dans la plate-forme, possédant la machine à danser.

Toutes nos félicitations!
