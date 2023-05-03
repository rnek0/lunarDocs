# El protocolo IP

Un **protocolo de comunicaciones** es un sistema de reglas que permiten que dos o más entidades (computadoras, teléfonos celulares, etc.) de un sistema de comunicación se comuniquen entre ellas para transmitir información.

**Comunicar consiste en transmitir información**, pero mientras los interlocutores no le atribuyan un significado, son solo datos y no información. Por lo tanto, los interlocutores deben no solo **hablar un idioma común**, sino también **dominar las reglas mínimas para transmitir y recibir datos**. El papel de un protocolo es asegurarse de todo esto.

## El papel del protocolo IP

[El protocolo IP](https://es.wikipedia.org/wiki/Protocolo_de_internet) (no confundir con dirección ip), es parte de la capa de Internet del [conjunto de protocolos TCP/IP](https://es.wikipedia.org/wiki/Familia_de_protocolos_de_internet) que "no es un estándar estricto, como lo es el [modelo OSI de ISO](../modeloOSI/)". Es uno de los protocolos más importantes de Internet porque permite el desarrollo y transporte de **datagramas IP (paquetes de datos)** , sin asegurar su "entrega". De hecho, el protocolo IP trata los datagramas IP independientemente unos de otros definiendo su representación, enrutamiento y reenvío.  

El protocolo IP es el protocolo que ```permite identificar las máquinas y enrutar la información a través de Internet```.  
Protocolo de comunicación de datos digitales clasificado funcionalmente en la capa de red según el modelo internacional OSI. 

El protocolo IP determina el destinatario del mensaje mediante 3 campos:

- El campo de **dirección IP**: dirección de la máquina. En IPv4 **4 octetos** (32bits) representados en decimal y separados por puntos. 
- El campo de [**máscara de subred**](https://es.wikipedia.org/wiki/M%C3%A1scara_de_red): una máscara de subred permite que el protocolo IP determine la **parte de la dirección IP que concierne a la red**
- El campo de [puerta de enlace predeterminada](https://es.wikipedia.org/wiki/Puerta_de_enlace) (en inglés gateway): "nodo que sirve como enlace entre dos redes informáticas" que permite que el protocolo de Internet sepa a qué máquina entregar el datagrama si la máquina de destino no está en la red local.

## Direcciones IP

[Una dirección IP](#Dirección+Internet) (del inglés, Internet Protocol) es una ```etiqueta numérica que identifica de manera lógica y jerárquica``` a [una interfaz](https://en.wikipedia.org/wiki/Interface_(computing)) —habitualmente un dispositivo (computadora, laptop, teléfono inteligente)— conectada a [la red](https://es.wikipedia.org/wiki/Red_de_computadoras), que utilice el protocolo de internet o que corresponda al nivel de red del modelo TCP/IP.  

Inicialmente se denominaba 'Dirección Internet', esta compuesta por una dirección de 32bits (4 octetos)

Ejemplo de conversion de una dirección IP (192.168.0.1) de decimal hacia binario :

```bash
❯ echo "$(echo "obase=2; 192" | bc | numfmt --format=%08f).$(echo "obase=2; 168" | bc | numfmt --format=%08f).$(echo "obase=2; 0" | bc | numfmt --format=%08f).$(echo "obase=2; 1" | bc | numfmt --format=%08f)"
11000000.10101000.00000000.00000001
```

[Un script para tenerlo mas a mano](https://gist.github.com/rnek0/2152fd058edd7a97af2a4b1688761937)

Un post sobre 

### Dirección Internet vs URL

La dirección IP fué llamada dirección internet en la especificación inicial, actualmente (por extension de lenguaje) es común llamar dirección internet al sitio donde esta un recurso, pero no hay que confundir IP con [URL](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme) (uniform resource locator) por ejemplo (con el protocolo http o https).

>  **Dirección Internet** : una dirección de origen o destino de 4 octetos (32 bits) en la version IPv4 que ```identifica una maquina o interfaz (hardware)```  

>  **URL** : gracias al protocolo DNS el URL corresponderá con una dirección IP pero se busca un recurso que sera servido por una aplicación (servidor) que puede igualmente servir recursos de otras maquinas (proxy). ```Se solicitan datos (Software)```

Véase también algunas referencias en los [RFC](https://es.wikipedia.org/wiki/Request_for_Comments) : 

* en [Pág. 8] de [la RFC 791 de INTERNET PROTOCOL](https://www.rfc-es.org/rfc/rfc0791-es.txt)
* [RFC1180: Un tutorial de TCP/IP (en español)](https://www.rfc-es.org/rfc/rfc1180-es.txt) que no te puedes perder ! si quieres profundizar en el tema.  
  El mismo en [FR] pero en [pdf](http://abcdrfc.free.fr/rfc-vf/pdf/rfc1122.pdf). 

<a name="Dirección+Internet"></a>

---

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!-- Created with Inkscape (http://www.inkscape.org/) -->

<svg
   width="203.54251mm"
   height="151.57936mm"
   viewBox="0 0 203.54251 151.57936"
   version="1.1"
   id="svg5"
   inkscape:version="1.2.2 (b0a8486541, 2022-12-01)"
   sodipodi:docname="ip_img_map.svg"
   inkscape:export-filename="ip.svg"
   inkscape:export-xdpi="66.1755"
   inkscape:export-ydpi="66.1755"
   xmlns:inkscape="http://www.inkscape.org/namespaces/inkscape"
   xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd"
   xmlns:xlink="http://www.w3.org/1999/xlink"
   xmlns="http://www.w3.org/2000/svg"
   xmlns:svg="http://www.w3.org/2000/svg">
  <sodipodi:namedview
     id="namedview7"
     pagecolor="#ffffff"
     bordercolor="#666666"
     borderopacity="1.0"
     inkscape:showpageshadow="2"
     inkscape:pageopacity="0.0"
     inkscape:pagecheckerboard="0"
     inkscape:deskcolor="#d1d1d1"
     inkscape:document-units="mm"
     showgrid="true"
     inkscape:zoom="1.4247736"
     inkscape:cx="321.45458"
     inkscape:cy="279.34263"
     inkscape:window-width="1916"
     inkscape:window-height="1047"
     inkscape:window-x="1680"
     inkscape:window-y="29"
     inkscape:window-maximized="1"
     inkscape:current-layer="layer1"
     showguides="true">
    <inkscape:grid
       type="xygrid"
       id="grid7946" />
    <sodipodi:guide
       position="99.952481,23.230098"
       orientation="1,0"
       id="guide7948"
       inkscape:locked="false" />
    <sodipodi:guide
       position="153.39159,56.192537"
       orientation="1,0"
       id="guide7950"
       inkscape:locked="false" />
    <sodipodi:guide
       position="48.011662,36.964447"
       orientation="1,0"
       id="guide7952"
       inkscape:locked="false" />
  </sodipodi:namedview>
  <defs
     id="defs2">
    <linearGradient
       id="linearGradient55287"
       inkscape:swatch="solid">
      <stop
         style="stop-color:#002255;stop-opacity:1;"
         offset="0"
         id="stop55285" />
    </linearGradient>
    <marker
       style="overflow:visible"
       id="TriangleStart"
       refX="0"
       refY="0"
       orient="auto-start-reverse"
       inkscape:stockid="TriangleStart"
       markerWidth="4"
       markerHeight="4"
       viewBox="0 0 5.3244081 6.1553851"
       inkscape:isstock="true"
       inkscape:collect="always"
       preserveAspectRatio="xMidYMid">
      <path
         transform="scale(0.5)"
         style="fill:context-stroke;fill-rule:evenodd;stroke:context-stroke;stroke-width:1pt"
         d="M 5.77,0 -2.88,5 V -5 Z"
         id="path135" />
    </marker>
    <linearGradient
       id="linearGradient1202"
       inkscape:swatch="gradient">
      <stop
         style="stop-color:#00b500;stop-opacity:1;"
         offset="0"
         id="stop1198" />
      <stop
         style="stop-color:#00b500;stop-opacity:0;"
         offset="1"
         id="stop1200" />
    </linearGradient>
    <marker
       style="overflow:visible"
       id="TriangleStart-9"
       refX="0"
       refY="0"
       orient="auto-start-reverse"
       inkscape:stockid="TriangleStart"
       markerWidth="4"
       markerHeight="4"
       viewBox="0 0 5.3244081 6.1553851"
       inkscape:isstock="true"
       inkscape:collect="always"
       preserveAspectRatio="xMidYMid">
      <path
         transform="scale(0.5)"
         style="fill:context-stroke;fill-rule:evenodd;stroke:context-stroke;stroke-width:1pt"
         d="M 5.77,0 -2.88,5 V -5 Z"
         id="path135-2" />
    </marker>
  </defs>
  <g
     inkscape:label="Calque 1"
     inkscape:groupmode="layer"
     id="layer1"
     transform="translate(-4.9280158,-10.242818)">
    <rect
       style="fill:#aaccff;fill-opacity:1;stroke:#002255;stroke-width:0.406;stroke-linecap:round;stroke-linejoin:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:0.909804;image-rendering:auto"
       id="rect24128"
       width="203.13651"
       height="151.17337"
       x="5.1310158"
       y="10.445818" />
    <rect
       style="fill:#00aad4;fill-opacity:0.907425;stroke:#002255;stroke-width:1;stroke-linecap:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
       id="rect294"
       width="74.720932"
       height="19.727665"
       x="67.597458"
       y="33.360523" />
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:10.5833px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
       x="75.123627"
       y="46.765385"
       id="text350"><tspan
         sodipodi:role="line"
         id="tspan348"
         style="fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
         x="75.123627"
         y="46.765385">Dirección IP</tspan></text>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="64.964806"
       y="18.68141"
       id="text2667"><tspan
         id="tspan2665"
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="64.964806"
         y="18.68141"
         sodipodi:role="line">Identifica cada                  &quot;dispositivo&quot; </tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="64.964806"
         y="23.973072"
         id="tspan2719"
         sodipodi:role="line">que usa el Protocolo de Internet para </tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="64.964806"
         y="29.264734"
         id="tspan2721"
         sodipodi:role="line">comunicarse a través de una red.</tspan></text>
    <a
       id="ipv4Link"
       xlink:href=""
       xlink:title=""
       xlink:actuate=""
       onclick="window.open(&quot;https://es.wikipedia.org/wiki/Direcci%C3%B3n_IP#Direcciones_IP&quot;,&quot;_blank&quot;);"
       inkscape:label="#ipv4Link"
       onmouseover="style=&quot;cursor: pointer; opacity:0.5;&quot;"
       onmouseout="style=&quot;cursor: arrow; opacity:1;&quot;"
       style="image-rendering:auto"
       target=""
       onload="">
      <title
         id="title41087">Direcciones IPv4 en Wikipedia.</title>
      <g
         id="g32650"
         inkscape:label="IPv4"
         style="display:inline">
        <rect
           style="fill:#00aad4;fill-opacity:0.907425;stroke:#002255;stroke-width:1;stroke-linecap:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
           id="rect294-7"
           width="74.720932"
           height="19.727665"
           x="15.136299"
           y="102.08038" />
        <text
           xml:space="preserve"
           style="font-style:normal;font-weight:normal;font-size:10.5833px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
           x="41.712486"
           y="115.48524"
           id="text350-5"><tspan
             sodipodi:role="line"
             id="tspan348-3"
             style="fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
             x="41.712486"
             y="115.48524">IPv4</tspan></text>
      </g>
    </a>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:5.64444px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
       x="35.625954"
       y="131.81195"
       id="text350-5-2"><tspan
         sodipodi:role="line"
         id="tspan348-3-3"
         style="font-size:5.64444px;fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
         x="35.625954"
         y="131.81195">192.168.1.15</tspan></text>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:5.64444px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
       x="113.91325"
       y="132.0208"
       id="text350-5-2-7"><tspan
         sodipodi:role="line"
         id="tspan348-3-3-5"
         style="font-size:5.64444px;fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
         x="113.91325"
         y="132.0208">2001:db8:85a3:0:0:8a2e:370:7334</tspan></text>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="19.37422"
       y="139.49667"
       id="text2667-5"><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="19.37422"
         y="139.49667"
         id="tspan2721-9"
         sodipodi:role="line">4 grupos de 3 digitos decimales </tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="19.37422"
         y="144.78833"
         sodipodi:role="line"
         id="tspan14209">de 0 a 255 (1 octeto), </tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="19.37422"
         y="150.08"
         sodipodi:role="line"
         id="tspan26588"><tspan
   style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:sans-serif;-inkscape-font-specification:sans-serif"
   id="tspan30342">(11111111)^2</tspan> = (255)^10 = <tspan
   style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:sans-serif;-inkscape-font-specification:sans-serif"
   id="tspan30344">FF</tspan></tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="19.37422"
         y="155.37166"
         sodipodi:role="line"
         id="tspan19528">separados por puntos '.'</tspan></text>
    <a
       id="ipv6Link"
       onmouseover="style=&quot;cursor: pointer; opacity = 0.5;&quot;"
       onmouseout="style=&quot;cursor: arrow; opacity=1;&quot;"
       onclick="window.open(&quot;https://es.wikipedia.org/wiki/IPv6&quot;,&quot;_blank&quot;);"
       inkscape:label="#ipv6Link">
      <title
         id="title52587">Direcciones IPv6 en Wikipedia.</title>
      <g
         id="g32655"
         style="display:inline"
         inkscape:label="IPv6"
         onclick="window.open(&quot;https://es.wikipedia.org/wiki/Direcci%C3%B3n_IPv6&quot;);"
         onmouseover="style.opacity = 0.5;"
         onmouseout="style.opacity = 1;">
        <g
           id="g40372">
          <rect
             style="fill:#00aad4;fill-opacity:0.907425;stroke:#002255;stroke-width:1;stroke-linecap:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
             id="rect294-70"
             width="74.720932"
             height="19.727665"
             x="120.84269"
             y="101.85594" />
          <text
             xml:space="preserve"
             style="font-style:normal;font-weight:normal;font-size:10.5833px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
             x="147.41859"
             y="115.2608"
             id="text350-9"><tspan
               sodipodi:role="line"
               id="tspan348-36"
               style="fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
               x="147.41859"
               y="115.2608">IPv6</tspan></text>
        </g>
      </g>
    </a>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="120.3181"
       y="139.27225"
       id="text2667-0"><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="120.3181"
         y="139.27225"
         id="tspan2721-1"
         sodipodi:role="line">8 grupos de 4 dígitos hexadecimales</tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="120.3181"
         y="144.5639"
         sodipodi:role="line"
         id="tspan19524">cada grupo representa 2 octetos</tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="120.3181"
         y="149.85558"
         sodipodi:role="line"
         id="tspan28840">desde 0000 hasta FFFF</tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="120.3181"
         y="155.14723"
         sodipodi:role="line"
         id="tspan19526">separados por 2 puntos ':'</tspan></text>
    <path
       style="fill:#5599ff;fill-opacity:1;fill-rule:evenodd;stroke:#00a9d4;stroke-width:0.901475;stroke-linecap:butt;stroke-linejoin:miter;stroke-dasharray:2.70443, 2.70443;stroke-dashoffset:0;stroke-opacity:0.909804;marker-end:url(#TriangleStart)"
       d="M 109.073,54.484641 143.67274,98.53939"
       id="path8039"
       inkscape:connector-type="polyline"
       inkscape:connector-curvature="0" />
    <path
       style="fill:#5599ff;fill-opacity:1;fill-rule:evenodd;stroke:#00a9d4;stroke-width:0.901475;stroke-linecap:butt;stroke-linejoin:miter;stroke-dasharray:2.70443, 2.70443;stroke-dashoffset:0;stroke-opacity:0.909804;marker-end:url(#TriangleStart-9)"
       d="M 101.11578,53.920652 66.516223,97.975362"
       id="path8039-2"
       inkscape:connector-type="polyline"
       inkscape:connector-curvature="0" />
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="15.179116"
       y="98.185951"
       id="text11923"><tspan
         sodipodi:role="line"
         id="tspan11921"
         style="font-style:italic;font-variant:normal;font-weight:normal;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Italic';stroke-width:0.264583"
         x="15.179116"
         y="98.185951">Decimal (32 bits)</tspan></text>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="153.40794"
       y="97.94323"
       id="text11923-2"><tspan
         sodipodi:role="line"
         id="tspan11921-0"
         style="font-style:italic;font-variant:normal;font-weight:normal;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Italic';stroke-width:0.264583"
         x="153.40794"
         y="97.94323">Hexadecimal (128 bits)</tspan></text>
    <a
       id="interfazLink"
       onmouseover="style=&quot;cursor: pointer; opacity:0.5;&quot;"
       onmouseup=""
       inkscape:label="#interfazLink"
       onclick="window.open(&quot;https://en.wikipedia.org/wiki/Interface_(computing)&quot;,&quot;_blank&quot;);"
       onmouseout="style=&quot;cursor: arrow; opacity:1;&quot;">
      <title
         id="title2511">Ver interfaz en wikipedia</title>
      <desc
         id="desc2278">En informática, una interfaz es un límite compartido a través del cual dos o más componentes separados de un sistema informático intercambian información.</desc>
      <g
         id="g2178"
         inkscape:label="interfaz">
        <rect
           style="fill:#0facd8;fill-opacity:1;stroke:#000000;stroke-width:0.52375;stroke-linecap:round;stroke-linejoin:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
           id="rect53205"
           width="17.792856"
           height="5.0735517"
           x="97.02758"
           y="14.629653" />
        <text
           xml:space="preserve"
           style="font-size:4.28024px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;stroke-width:0.267515"
           x="97.337318"
           y="18.745682"
           id="text1423"
           transform="scale(1.0110817,0.98903976)"><tspan
             sodipodi:role="line"
             id="tspan1421"
             style="font-style:italic;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:sans-serif;-inkscape-font-specification:'sans-serif Italic';stroke-width:0.267515"
             x="97.337318"
             y="18.745682">interfaz</tspan></text>
      </g>
    </a>
  </g>
</svg>

---

## IP Datagram header

El [encabezado IP](https://es.wikipedia.org/wiki/Cabecera_IP) muestra los bits y para que sirven, podemos apreciar las 2 direcciones (origen y destino), el TTL y une Checksum para verificar el estado (por ejemplo)  

Un consejo, aunque leas los articulos en wikipedia en tu idioma, pasate por los que esten en inglés porque, a menudo la informacion puede ser mas precisa; por ejemplo :

**An IP header is header information at the beginning of an Internet Protocol (IP) packet.** An IP packet is the smallest message entity exchanged via the Internet Protocol across an IP network. ```IP packets consist of a header for addressing and routing, and a payload for user data```. The header contains information about IP version, source IP address, destination IP address, time-to-live, etc. The payload of an IP packet is typically a datagram or segment of the higher-level transport layer protocol, but may be data for an internet layer (e.g., ICMP or ICMPv6) or link layer (e.g., OSPF) instead. 

```
3.1.  Internet Header Format

  A summary of the contents of the internet header follows:

                                    
    0                   1                   2                   3   
    0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |Version|  IHL  |Type of Service|          Total Length         |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |         Identification        |Flags|      Fragment Offset    |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |  Time to Live |    Protocol   |         Header Checksum       |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                       Source Address                          |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                    Destination Address                        |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                    Options                    |    Padding    |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

                    Example Internet Datagram Header

                               Figure 4.

  Note that each tick mark represents one bit position.
```  
Ver la [RFC 791](https://www.ietf.org/rfc/rfc791.txt)

Se podría comparar un paquete IP con una pagina HTML, los dos tienen encabezado y contenido.
