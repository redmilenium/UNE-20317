# UNE20317
Experimentación con la curva de disparo de los contadores de electricidad inteligentes

![image](https://user-images.githubusercontent.com/48222471/219492947-e7747d4d-90d1-499b-b493-321c5ba3bfa8.png)

Este proyecto tiene como fin experimentar con las tolerancias por sobreconsumo de los contadores de electricidad inteligentes.

Necesitare un medidor remoto de potencia, que estará situado a la entrada del suministro electrico a la vivienda y que va a medir la 
potencia total que se esta consumiendo. 

Este dispositivo ya lo tengo construido y esta plenamente operativo. 

Para enviar la informacion obtenida, utilizaré el protocolo ESP NOW de expresiff. Dado que va a estar instalado dentro de la caja de disyuntores, en concreto donde
antes se encontraba el ICP, que ya no es necesario, he habilitado el envio via OTA de nuevas programaciones, para no tener que estar abriendo
y cerrando dichas cajas.

Esquema y foto del dispositivo de medida remoto:
![image](https://user-images.githubusercontent.com/48222471/219491638-14fb87c1-97d6-48e1-ba34-ba93350dca81.png)



         

