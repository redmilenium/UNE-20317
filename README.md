# UNE20317
Experimentación con la curva de disparo de los contadores de electricidad inteligentes

![image](https://user-images.githubusercontent.com/48222471/219492947-e7747d4d-90d1-499b-b493-321c5ba3bfa8.png)

Este proyecto tiene como fin experimentar con las tolerancias por sobreconsumo de los contadores de electricidad inteligentes.

Necesitare un medidor remoto de potencia, que estará situado a la entrada del suministro electrico a la vivienda y que va a medir la 
potencia total que se esta consumiendo. 

Este dispositivo ya lo tengo construido y esta plenamente operativo. 

Para enviar la informacion obtenida, utilizaré el protocolo ESP NOW de Expressif. Dado que va a estar instalado dentro de la caja de disyuntores, en concreto donde
antes se encontraba el ICP, que ya no es necesario.

He habilitado el envio via OTA de nuevas programaciones, para no tener que estar abriendo y cerrando dichas cajas.

Esquema y foto del dispositivo de medida remoto:
![image](https://user-images.githubusercontent.com/48222471/219496738-8e9a7dd9-9772-4752-a8ce-3a03f290bc8c.png)

Y una vez instalado en la caja del ICP:

![image](https://user-images.githubusercontent.com/48222471/219714644-a326c7a9-073b-46c9-9ab5-386df6488618.png)

El toroide captador se encuentra en la parte superior y esta puesto sobre la linea de fase que alimenta a la vivienda.

         

