<!-- TITLE: Dhcp Y Dns -->
<!-- SUBTITLE: A quick summary of Dhcp Y Dns -->

# Header

# ######Configuracion DNS##################### #

Servidor utilizado: dnsmasq
archivo de conf principal: /etc/dnsmasq.conf

tambien proporciona DHCP, pero se detalla por separado.
Comandos de interes:
-service dnsmasq (restart/stop/start)
-nslookup nombreDeDominio

## ##### config en /etc/hosts ##


```
#!javascript

127.0.0.1       localhost
################################## servers, varios, otros
10.0.0.1        recinto.local server.recinto.local
192.168.3.30    server.recinto.local huellas.intranet.com.ar

################################### equipos
10.0.0.131  fran  #fran
10.0.0.132 jm   #jm
10.0.0.133 impresora   #impresora(futura)
10.0.0.134 turco   #turco(wlan)Note
10.0.0.139 turco2
10.0.0.135 ups   #ups
10.0.0.136 ale0   #ale(wlan)Note
10.0.0.137 ale1   #ale(lan)
10.0.0.138 maxi   #maxi(wlan)

################################## routers/infraestructura
10.0.0.3 router #ciscoBurgues

################################## bancas
10.0.0.21 banca1 #raspBanca1

```


## ##### config en /etc/dnsmasq.conf ##

##DNS externas
resolv-file=/etc/resolv.conf.dnsmasq
###forzamos orden
strict-order
###definimos dominio local
local=/local/
### ignoramos request de interface externa
except-interface=em2
### agrega nombres simples para el dominio:
expand-hosts

# ######Configuracion DHCP#################### #


Servidor utilizado: dnsmasq
archivo de conf principal: /etc/dnsmasq.conf

Comandos de interes:
-service dnsmasq (restart/stop/start)
-arp ("-a" o "-f /etc/ethers") mac ip dominio asociados.


## ##### config en /etc/dnsmasq.conf ##

### carga archivo de configuracion con mac->dominio en /etc/ethers
read-ethers
### configura el nombre simple para el dominio:
domain=local
### rango del servidor dhcp para los equipos no especificados:
dhcp-range=10.0.0.10,10.0.0.20,255.0.0.0,12h
### se incluye un archivo de configuracion distinto para el seteo mac->ip
conf-file=/etc/dnsmasq.more.macIp.conf


## ##### config en /etc/dnsmasq.more.macIp.conf ##

######## DHCP SERVER DNSMASQ
################################### equipos  mac/ip
## se detalla mac,ip

```
#!javascript

dhcp-host=00:19:db:a5:7f:3b,10.0.0.131    #fran
dhcp-host=00:1c:c0:77:e5:98,10.0.0.132    #jm
dhcp-host=30:cd:a7:c7:c9:1d,10.0.0.133    #impresora(futura)
dhcp-host=ac:e0:10:19:aa:85,10.0.0.134    #turco(wlan)Note
dhcp-host=f0:76:1c:a9:ca:0b,10.0.0.139    #turco(lan)
dhcp-host=00:02:99:16:66:00,10.0.0.135    #ups
dhcp-host=b4:6d:83:6d:ce:23,10.0.0.136    #ale(wlan)Note
dhcp-host=f0:76:1c:fc:81:33,10.0.0.137    #ale(lan)
dhcp-host=90:a4:de:e8:3d:92,10.0.0.138    #maxi(wlan)
```








