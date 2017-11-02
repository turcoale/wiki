<!-- TITLE: Bancas Server Recinto -->
<!-- SUBTITLE: A quick summary of Bancas Server Recinto -->

# Header
Protocolo de comunicación Bancas:
Definimos el protocolo de las bancas de la siguiente manera:
Se define un JSON de la siguiente manera:
 {
  banca: número de banca,
  accion: la codificación requerida según se especifique para cada caso
 }
accion
Cada campo estará separado por / todos los campos en minúscula:
Estado de la butaca:
butaca/true
butaca/false
butaca/null <= estado de la banca
butaca/all <= estado de todas las bancas
Sentado identificado:
sensor/IdHuellaDiputado
Pedido de la Palabra:
palabra/IdBanca
palabra/remover/IdDiputado
Estado de votación:
voto/true
voto/false
Estado de Micrófono:
banca1/mic/TRUE
banca1/mic/FALSE
Además tenemos que definir unos comandos de envío donde se puede encuestar a la banca en caso de que no esté respondiendo o en caso que necesitemos hacer algo especial
Votación Tipo:
'votacionTipo/identificadorDelTipoDeVotación'
Votación Abierta:
votación/open
Votación tiempo:
votación/setTiempo/milisegundos
Keep Alive: (Permite encuestar a una banca individual para saber si responde)
banca1/KA
También podemos consultar cualquier parametro en cualquier momento:
banca1/voto
banca1/palabra
banca1/butaca
banca1/id