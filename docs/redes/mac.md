# Direcciones MAC

Las direcciones MAC **identifican una tarjeta o dispositivo de Red**  ( **M** edia **A** ccess **C** ontrol ), oficialmente llamada "MAC-48"

Se codifican en hexadecimal con 6 pares de 2 cifras hexadecimales separados por ':' (dos puntos) y en teoría se trata de un identificador único para una tarjeta de red definido por su fabricante. Se puede considerar como si fuera una huella digital pero en la practica veamos como se puede cambiar : aunque ninguna otra tarjeta tenga el mismo, es la capa de sistema operativo la que gestiona y distribuye en la red, con lo que se puede modificar la dirección MAC que identifica la interfaz de red. Esta práctica es conocida como MAC spoofing. Un ejemplo de tool para ello es [macchanger](https://github.com/alobbs/macchanger), se pueden encontrar otros recursos como por ejemplo [aquí](https://www.ionos.mx/digitalguide/servidores/know-how/que-es-el-mac-spoofing/)  
Las direcciones mac pueden servir igualmente para **filtrar los hosts** y atribuir permisos en una red por los administradores. Supongamos que conseguimos modificar la nuesta para que sea la misma que la de alguien que tenga acceso a un servicio y nosotros no...

Un poco de numeración :  
2 cifras hexadecimales son un byte en binario (ocho bits o un octeto) Ejemplo [Hexa -> Decimal -> Binario]: FF = 255 = 11111111 

Los códigos de la dirección MAC tienen un significado :

* los 3 primeros bytes identifican al fabricante, es el identificador llamado **OUI (Identificador Único Organizacional)**
* los 3 últimos bytes  representan el **controlador de interfaz de red**, que es asignado por el fabricante.

---

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!-- Created with Inkscape (http://www.inkscape.org/) -->

<svg
   width="203.54251mm"
   height="112.47204mm"
   viewBox="0 0 203.54251 112.47204"
   version="1.1"
   id="svg5"
   inkscape:version="1.2.2 (b0a8486541, 2022-12-01)"
   sodipodi:docname="MAC.svg"
   inkscape:export-filename="addr_MAC.svg"
   inkscape:export-xdpi="66.1755"
   inkscape:export-ydpi="66.1755"
   xmlns:inkscape="http://www.inkscape.org/namespaces/inkscape"
   xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd"
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
     inkscape:zoom="1.4118735"
     inkscape:cx="113.3246"
     inkscape:cy="298.89364"
     inkscape:window-width="1916"
     inkscape:window-height="971"
     inkscape:window-x="1680"
     inkscape:window-y="107"
     inkscape:window-maximized="1"
     inkscape:current-layer="layer1"
     showguides="true">
    <inkscape:grid
       type="xygrid"
       id="grid7946" />
    <sodipodi:guide
       position="99.952485,-15.877225"
       orientation="1,0"
       id="guide7948"
       inkscape:locked="false" />
    <sodipodi:guide
       position="153.39159,17.085215"
       orientation="1,0"
       id="guide7950"
       inkscape:locked="false" />
    <sodipodi:guide
       position="62.026132,62.019455"
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
  </defs>
  <g
     inkscape:label="Calque 1"
     inkscape:groupmode="layer"
     id="layer1"
     transform="translate(-4.9280153,-10.242818)">
    <rect
       style="fill:#aaccff;fill-opacity:1;stroke:#002255;stroke-width:0.349699;stroke-linecap:round;stroke-linejoin:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:0.909804;image-rendering:auto"
       id="rect24128"
       width="203.19281"
       height="112.12234"
       x="5.1028652"
       y="10.417667" />
    <a
       id="a1514">
      <g
         id="direccion_mac"
         onmouseover="style=&quot;cursor: pointer; opacity = 0.5;&quot;"
         onmouseout="style=&quot;cursor: arrow; opacity=1;&quot;"
         onclick="window.open(&quot;https://es.wikipedia.org/wiki/Direcci%C3%B3n_MAC&quot;,&quot;_blank&quot;);"
         inkscape:label="#direccion_mac">
        <desc
           id="desc1518">Identificador de 48 bits (6 bloques de dos caracteres hexadecimales [8 bits]) que corresponde de forma única a una tarjeta o dispositivo de red.</desc>
        <title
           id="title1516">Dirección MAC</title>
        <rect
           style="fill:#00aad4;fill-opacity:0.907425;stroke:#002255;stroke-width:0.5;stroke-linecap:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
           id="rect294"
           width="94.897736"
           height="19.60424"
           x="57.075829"
           y="31.834736" />
        <text
           xml:space="preserve"
           style="font-style:normal;font-weight:normal;font-size:10.5833px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#002255;fill-opacity:1;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
           x="64.540283"
           y="45.177883"
           id="text350"><tspan
             sodipodi:role="line"
             style="fill:#002255;stroke:#002255;stroke-width:0.264583;stroke-opacity:1"
             x="64.540283"
             y="45.177883"
             id="tspan519">Dirección MAC</tspan></text>
      </g>
    </a>
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.23333px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.264583"
       x="57.556465"
       y="21.856413"
       id="text2667"><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="57.556465"
         y="21.856413"
         id="tspan2721"
         sodipodi:role="line">Identifica cada                  o dispositivo de red </tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.23333px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="57.556465"
         y="27.148075"
         sodipodi:role="line"
         id="tspan576">con un número único.</tspan></text>
    <rect
       style="fill:#00aad4;fill-opacity:0.907425;stroke:#002255;stroke-width:0.5;stroke-linecap:round;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
       id="rect294-70"
       width="95.722565"
       height="19.610729"
       x="56.85273"
       y="78.276337" />
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.2771px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.267318"
       x="65.758179"
       y="105.59221"
       id="text2667-0"
       transform="scale(1.0103384,0.98976738)"><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.2771px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.267318"
         x="65.758179"
         y="105.59221"
         id="tspan2721-1"
         sodipodi:role="line">6 grupos de 2 dígitos hexadecimales</tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.2771px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.267318"
         x="65.758179"
         y="110.93858"
         sodipodi:role="line"
         id="tspan19524">cada grupo representa 1 octeto</tspan><tspan
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:4.2771px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.267318"
         x="65.758179"
         y="116.28496"
         sodipodi:role="line"
         id="tspan19526">desde 00 hasta FF separados por ':'</tspan></text>
    <path
       style="fill:#5599ff;fill-opacity:1;fill-rule:evenodd;stroke:#00a9d4;stroke-width:0.720536;stroke-linecap:butt;stroke-linejoin:miter;stroke-dasharray:2.16161, 2.16161;stroke-dashoffset:0;stroke-opacity:0.909804;marker-end:url(#TriangleStart)"
       d="m 105.635,54.295174 0.33301,20.884342"
       id="path8039"
       inkscape:connector-type="polyline"
       inkscape:connector-curvature="0" />
    <text
       xml:space="preserve"
       style="font-style:normal;font-weight:normal;font-size:4.2771px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;fill:#000000;fill-opacity:1;stroke:none;stroke-width:0.267318"
       x="110.82432"
       y="76.697945"
       id="text11923-2"
       transform="scale(1.0103384,0.98976738)"><tspan
         sodipodi:role="line"
         id="tspan11921-0"
         style="font-style:italic;font-variant:normal;font-weight:normal;font-stretch:normal;font-size:4.2771px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Italic';stroke-width:0.267318"
         x="110.82432"
         y="76.697945">Hexadecimal (48 bits)</tspan></text>
    <a
       id="interfazLink"
       onmouseover="style=&quot;cursor: pointer; opacity:0.5;&quot;"
       onmouseup=""
       inkscape:label="#interfazLink"
       onclick="window.open(&quot;https://es.wikipedia.org/wiki/Tarjeta_de_red&quot;,&quot;_blank&quot;);"
       onmouseout="style=&quot;cursor: arrow; opacity:1;&quot;"
       transform="translate(-7.4083338,3.1750001)">
      <title
         id="title2511">Ver interfaz en wikipedia</title>
      <desc
         id="desc2278">En informática, una interfaz es un límite compartido a través del cual dos o más componentes separados de un sistema informático intercambian información.</desc>
      <a
         id="a1158">
        <g
           id="g1151">
          <g
             id="g560"
             transform="translate(0.52916667)">
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
               x="98.384056"
               y="18.745682"
               id="text1423"
               transform="scale(1.0110817,0.98903975)"><tspan
                 sodipodi:role="line"
                 id="tspan1421"
                 style="font-style:italic;font-variant:normal;font-weight:normal;font-stretch:normal;font-family:sans-serif;-inkscape-font-specification:'sans-serif Italic';stroke-width:0.267515"
                 x="98.384056"
                 y="18.745682">tarjeta</tspan></text>
          </g>
        </g>
      </a>
    </a>
    <text
       xml:space="preserve"
       style="font-size:9.87778px;line-height:1.25;font-family:sans-serif;letter-spacing:0px;word-spacing:0px;stroke-width:0.264583"
       x="63.898949"
       y="91.551727"
       id="text591"><tspan
         sodipodi:role="line"
         id="tspan589"
         style="font-style:normal;font-variant:normal;font-weight:bold;font-stretch:normal;font-size:9.87778px;font-family:sans-serif;-inkscape-font-specification:'sans-serif Bold';stroke-width:0.264583"
         x="63.898949"
         y="91.551727">91:75:1a:ef:9a:c7</tspan></text>
  </g>
</svg>



---

## Documentacion adicional

Estos temas se contemplan en : 

* [hack4u](https://hack4u.io/cursos/introduccion-al-hacking/) Introducción al Hacking.
* [THM](https://tryhackme.com/room/nmap01) sobre nmap scan.
  