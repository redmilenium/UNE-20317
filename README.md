# UNE20317
Experimentación con la curva de disparo de los contadores de electricidad inteligentes

![image](https://user-images.githubusercontent.com/48222471/219492947-e7747d4d-90d1-499b-b493-321c5ba3bfa8.png)

Este proyecto tiene como fin experimentar con las tolerancias por sobreconsumo de los contadores de electricidad inteligentes.

Necesitare un medidor remoto de potencia, que estará situado a la entrada del suministro electrico a la vivienda y que va a medir la 
potencia total que se esta consumiendo. 

Este dispositivo ya lo tengo construido y esta plenamente operativo. 

Para enviar la informacion obtenida, utilizaré el protocolo ESP NOW de Expressif. Dado que va a estar instalado dentro de la caja de disyuntores, en concreto donde
antes se encontraba el ICP, que ya no es necesario y ya tenía desmontado, he habilitado el envio via OTA de nuevas programaciones, para no tener que estar abriendo y cerrando dicha caja.

La función de limitación de la corriente máxima que antes realizaba el ICP, ahora la realizan los contadores inteligentes.

Esquema y foto del dispositivo de medida remoto:
![image](https://user-images.githubusercontent.com/48222471/219496738-8e9a7dd9-9772-4752-a8ce-3a03f290bc8c.png)

Advertencia: Si no estas familiarizado con los trabajos electricos, solo mira y no toques. 

Y una vez instalado en la caja del ICP:

![image](https://user-images.githubusercontent.com/48222471/219714987-1215b34d-6ef1-4d0c-9408-89d66fcf842e.png)

El toroide captador se encuentra en la parte superior y esta puesto sobre la linea de fase que alimenta a la vivienda.


         

