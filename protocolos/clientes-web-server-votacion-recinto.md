<!-- TITLE: Clientes Web Server Votacion Recinto -->
<!-- SUBTITLE: A quick summary of Clientes Web Server Votacion Recinto -->

# Header
# Protocolo de comunicación server-cliente #

## Debug ##

### /debug ###
* get: página de debug
* post: json con el número de request por X tiempo

## Votacion ##

### /votacionResul ###
* post: json con el resultado de la última votación:
  {
   si: votos positivos,
   no: votos negativos,
   abs: abstenciones,
   result: resultado de la votacion(bool)
  }
### /votacionPresentes ###
* post: json con la cantidad de sentados, ausentes y datos de la sesión.
  {
   presentes: cant. sentados,
   ausentes: cant. totales - sentados,
   sesion: sesion del día,
   expendiente: nro de exp,
   quorum: si hay quorum. Bool,
   tiempo: tiempo en votación. Se actualiza 
  }
### /votacionImpresionResul ###
* Get: página a imprimir con el resultado de la última votación. Es la que se usa para generar el pdf para imprimir.

## sensores ##

### /sentadosNum ###
* Post: json total sentados
  {
   totales: toal sentados.
  }
### /sentados ###
* Post: json con el array de los sensores
  {
   array con todos los sensores de butaca
  }
### /sensorNum ###
* Post: json con el número total de identificados.
  {
   totales: nro total
  }
### /sensorPresentesNum ###
* Post: json con el número de presentes
  {
   totales: nro total de presentes en la sesión.
  }

### /sensorPresentes ###
* Post: json con lista de presentes en sesión.
  {
   totales: array con la lista de presentes.
  }

### /estadoBancas ###
*Post: json con matriz de boolenos con el estado de los sensores de la banca(butaca, biometrico).
  {
   matriz de booleeanos.
  }

## Palabra ##

### /palabra ###
* post: json de lista de pedidos de palabra en espera.
  {
   array con el pedido de palabra.
  }

### '/palabraOtorgada' ###
* post: json con lista de bancas y estado de palabra.
 {
  {
   {palabra: false, id: 0},
   {palabra: true, id: 1},   
   {palabra: false, id: 2},
       ....
   {palabra: false, id: 50},
  }
 }

## Cliente ##

### /cliente ###
* Post: recibe un json con los comandos del cliente. La opción se define en el atributo configuracion:

```
#!javascript

                        1. test: modo test.
                        2. datos de sesion: 
                           {
                            operacion: 2
                            sesion: numero de sesion
                            periodo: periodo de la sesion
                            clavePres: id del presidente                                       
                            tipoSesion: id del tipo de sesion
                           }
                        3. diputado:
                           {
                            operacion: 3
                            bloqPres: accion bloquear (bool)
                            desbloqPres: accion desBloquear (bool)
                            banca: número de banca
                            dip: identificador del diputado
                            desident: accion desident (bool)                                       
                            identif: accion identif (bool)
                           }
                        4. datosVotacion
                           {
                            operacion: 4
                            exp: expendiente
                            tiempo: tiempo de votacion
                            tipoVot: identificador del tipo de votacion
                            lanzar: (bool) lanzar votacion
                           }
                        21. setear id de votacion
                           {
                            operacion: 21
                            sesionId: identificador del número de sesion en la DB
                           }
```
### /diputado:bancaId ###
* Post: devuelve datos del diputado en la banca determinada, ejemplo /diputado24: son los datos del diputado en la banca 24.
 json de respuesta:

```
#!javascript
    {
     estado": identificado (bool),
     diputadoId": identificador del diputado,
     bloqPres": si la banca tiene bloqueada presencia (bool),
     nombre": no del diputado,
     apellido": apellido,
     bloque": bloque
    }
```

### /sesion ###
* Post: Devuelve datos de la sesión activa.


```
#!javascript
        {
         sesion: número de sesion.
         periodo: periodo de la sesión.
         clavePresidente: clave del presidente.
         tipoSesion: identificador del tipo de sesion.
        }
```

### '/votacion' ###
* Post: Devuelve un json con datos de la votacion activa/selecionada.

```
#!javascript
   { 
     expediente: código de expediente,
     tipoVotacion: identificador del tipo de votación,
     tiempoVotacion: tiempo de votación, en ml segundos (global.tiempoVotacion / 1000)
   }

```

### '/parlamentaria' ###
* Post: recibe un json con la lista de expedientes a agregar a la BD. Formato del JSON:
       
```
#!javascript
    {
      { lista: [ 'nombreExpendiente1', 'nombreExpendiente2' ] }

    }

```

### '/pedidopalabra' ###
* Post: ???? se está manejando desde '/'

### '/votacionLista' ###
* Post: devuelve un json con la lista de votaciones, de la siguiente manera:
       
```
#!javascript
    {
      votaciones: []
    }
```
## root ##

### /estado ###

* Post: puede o no recibir el identificador de la banca agregandole al request un JSON: {banca: identificador}, responde un JSON con variables del sistema:

```
#!javascript

 {
   votacion: booleano que indica si está en modo votación,
   modoPrueba: booleano que indica si está en modo prueba,
   bloquearPresencia: booleano del estado de la banca que se especificó en el request. Opcional.
 }
```