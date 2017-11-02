<!-- TITLE: Comunicacion Biometrico -->
<!-- SUBTITLE: A quick summary of Comunicacion Biometrico -->

# Header
# Identificar: #
**Envío:**    
```
#!python

40 11 00 00 00 00 00 00 00 00 00 51 0a

```

**Time Out:** 
```
#!python

40 11 00 00 00 00 00 00 00 00 6c bd 0a 
```


**Dedo:**	  
```
#!python

40 11 00 00 00 00 00 00 00 00 62 b3 0a
40 11 0b 00 00 00 00 00 00 00 61 bd 0a
```


**# Dedo No enrolado: #**
	  
```
#!python

40 11 00 00 00 00 00 00 00 00 62 b3 0a 
40 11 00 00 00 00 00 00 00 00 69 ba 0a 
```



# Free Scan: #
**Envío:**    
```
#!python

40 01 00 00 00 00 31 00 00 00 84 f6 0a
```

**Recibo:**   
```
#!python

40 01 84 00 00 00 00 00 00 00 61 26 0a 
```


**Envío:**    
```
#!python

40 01 00 00 00 00 30 00 00 00 84 f5 0a
```

**Recibo:**   
```
#!python

40 01 84 00 00 00 00 00 00 00 61 26 0a 
```