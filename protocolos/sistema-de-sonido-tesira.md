<!-- TITLE: Sistema De Sonido Tesira -->
<!-- SUBTITLE: A quick summary of Sistema De Sonido Tesira -->

# Header

# **Método de interacción con el sistema**  

La comunicación con el sistema de Sonido se lleva adelante a través de SSH. Lo que significa que a partir de un conjunto de Protocolos preestablecidos es posible acceder por red al mismo.

## **Sintaxis de los métodos** ##

La Sintaxis estándar para un protocolo de comunicación es:

**Instance_Tag Command Attribute [Index] [Value]**    

 
### **Instance_Tag:** ###

Es el nombre único o clave de una instancia o dispositivo del proyecto
  La etiqueta **SESSION** (SIEMPRE en MAYUSCULAS)Se utiliza para enviar atributos y comandos específicos de la sesión. Esto incluye el método de "respuesta" que retorna comandos y dispositivos setiados en la sesión.  
 

```
*Ejemplo: 
SESSION get aliases
+OK "list":["123" "AudioMeter1" "AudioMeter2" "AudioMeter3" "DEVICE" "Input1"     
"Mixer1" "Mute1" "Level1" "Output1"]

```
### **Command:** ###

El protocolo de texto de Tesira admite diferentes comandos de atributos como se enumeran a continuación 

* **get** 

String: Instance_Tag get [Index][Index]
```

Ejemplo:
!123 get level 1 
+OK "value":-10.000000


```
* **set**

String: Instance_Tag Service [[Index](Link URL)][[Value](Link URL)]

```

Ejemplo: 

Level1 set mute 1 true

```

* **increment**

Este atributo incrementa el valor especifico de un dispositivo. Si el valor es negativo el atributo disminuye.


String: Instance_Tag Service [Index][Index]

```
Ejemplo:

Level1 increment level 1 3

```

* **decrement**

Este atributo disminuye el valor especifico de un dispositivo. Si el valor es negativo el atributo incrementa.


String: Instance_Tag Service [Index][Value]


```

Ejemplo:
Level1 increment level 1 10
```


* **toggle**

Invierte el estado del dispositivo
 
String: Instance_Tag Service Attribute [Index]

```
Ejemplo:
Level1 toggle mute 1

```

  
### **Attribute** ###

El atributo define la parte del bloque de procesamiento DSP a controlar, como un nivel, crosspoint mute, etc. 

### **[Index]** ###

Attribute usa index para acceder al input o output del bloque DSP. Dependiendo del Bloque DPS se necesitaran uno o dos index en el caso de un mute solo uno pero en una mixer de matriz 2 uno para la entrada o fila y el segundo para la salida o columna.

### **[Value]** ###

Puede ser un Numero Ej: I_T set mixer 1 100

string (entre doble comillas)

Booleano (true o false) Ej: I_T mute 1 false



