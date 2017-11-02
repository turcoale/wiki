<!-- TITLE: Sistema De Video -->
<!-- SUBTITLE: A quick summary of Sistema De Video -->

# Header
# Sintaxis general de los Protocolos de Control #



## Principios Básicos ##
Los comandos de control para las cámaras PTZ  están en conformidad con la comunicación HTTP1.1.

Su formato se da a continuación:






```
http://[IP Address]/cgi-bin/aw_ptz?cmd=[Command]&res=[Type] 

```

### Donde: ###


** [IP Address]: ** Dirección IP de la cámara


** [Command]: ** Es donde ira los comandos que deseamos que la cámara ejecute. su sintaxis es la siguiente ** #"nombre_del_comando""valor" **. El "#" puede ser remplazado por "%23" que seria su interpretación en ASCII.


** [Type]: ** fijado en "1"

## **Protocolos de Gestion** ##

| Nombre                 | Protocolo           | Valor                                |
| ----------             | -----------         |:-----------------------------------: |
| Zoom(get)              | #GZ                 |                                      |
| Zoom(set)              | #AXZ[valor]         | De 555 a FFF                         |
| Pan/tilt position(get) | #APC                |                                      |
| Pan/tilt position(set) | #APC[valor1][valor2]| V1 de 0000 a FFFF ; V2 de 0000 a FFFF|
| Foco(get)              | #GF                 |                                      |
| Foco(set)              | #AXF[valor]         | De 000 a FFF                         |
| Auto Foco(Act o Desac) | #D1[valor]          | 1 o 0                                | 
| iris(get)              | #GI                 |                                      |
| iris(set)              | #I [valor]          | De 01 a 99                           |
| Auto Iris(Act o Desac) | #D3[valor]          | 1 o 0                                |
| Prest (set)            | #R[valor]           | De 01 a 99                           |
| Prest (get)            | #M[valor]           | De 01 a 99                           |


## Ejemplos ##

### Zoom ###


```

[Control] PC → CAMARA

http://192.168.0.10/cgi-bin/aw_ptz?cmd=%23AXZFFF&res=1

[Respuesta] CAMARA → PC

200 OK “axzFFF” 

```

### P/T ###


```
[Control] PC → CAMARA
http://192.168.0.10/cgi-bin/aw_ptz?cmd=%23APC7FFF7FFF&res=1

[Respuesta] CAMARA → PC
200 OK “aPC7FFF7FFF” 
```


### Foco ###


```
[Control] PC → CAMARA
http://192.168.0.10/cgi-bin/aw_ptz?cmd=%23AXF555&res=1

[Respuesta] CAMARA → PC
200 OK “axf555”
```


### Iris ###


```
[Control] PC → CAMARA
http://192.168.0.10/cgi-bin/aw_ptz?cmd=%23I99&res=1

[Respuesta] CAMARA → PC
200 OK “iC99”


```


### Preset ###


```
[Control] PC → CAMARA
http://192.168.0.10/cgi-bin/aw_ptz?cmd=%23R02&res=1

[Respuesta] CAMARA → PC
200 OK “So02”


```