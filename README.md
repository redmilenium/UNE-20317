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

Y una vez instalado en la caja del ICP y protegido del cableado:

![image](https://user-images.githubusercontent.com/48222471/219714987-1215b34d-6ef1-4d0c-9408-89d66fcf842e.png)

El toroide captador se encuentra en la parte superior y esta puesto sobre la linea de fase que alimenta a la vivienda.

VISTA GENERAL DEL SISTEMA

![image](https://user-images.githubusercontent.com/48222471/219717953-2f2091a9-315f-438e-8bae-c7326fb000a9.png)

Como unidad receptora, en principio esto usando el proyecto de captar los precios de la electricidad PVPC. He modificado el programa, añadiendole la funcionalidad del ESP NOW, y ademas he modificado la rutina del display para que presente los watios que se estan consumiendo en cada momento. 

La unidad remota envia el voltaje, la corriente, la potencia, la energia consumida, la frecuencia, el factor de potencia y la dirección grabada en el PZEM004:

  myDataSen.voltage= pzem.voltage();
  
  myDataSen.current= pzem.current();
  
  myDataSen.power = pzem.power();
  
  myDataSen.energy = pzem.energy();
  
  myDataSen.frequency = pzem.frequency();
  
  myDataSen.pf = pzem.pf();
  
  myDataSen.medidor=(pzem.readAddress(), HEX);
  
  Estos datos se meten dentro de una Estructura y se envian via ESP NOW.

  Por ahora solo estoy monitorizando la potencia que se esta consumiendo en tiempo real.
  
  En breve, el receptor, analizará la información recibida y en función de la potencia máxima contratada vigilará los excesos de consumo, desconectando durante
  un breve espacio de tiempo electrodomesticos que lo permitan, es decir que no se reinicien al volver a conectarlos, como planchas, freidoras, planchas de asar, 
  termos de agua, etc. para comprobar si al volver la potencia a niveles contratados, el tiempo que nos permitela UNE 20317 se resetea y volvemos a disponer 
  del máximo permitido.
  
  Este experimento tiene como finalidad exprimir los limites de potencia electrica contratada para poder utilizar mas potencia por la que muy generosamente pagamos.
  
  Ejemplo:

  Yo tengo contratados 4.6 KW. 
         
  Un exceso de 1,5 veces supondría alcanzar los 6,9 KW. Según la curva, dispondría de entre 30 segundos y 2 - 3 minutos,antes de que se produjera el disparo.
         
  Por debajo de 30 segundos consumiendo 1.5 veces la potencia contratada no debería desconectar el ICP nunca.
         
  Si a los 29 segundos, desconecto algún electrodomestico brevemente, un segundo por ejemplo, y mis valores de potencia consumida bajan a valores contratados (4,6 KW)
        
  ¿Volveré a disponer de 30 segundos a 6,9 KW?
  
  Para ello tengo que añadir al circuito receptor un SSR como este:
  
  ![image](https://user-images.githubusercontent.com/48222471/220998576-0d6f7752-51b5-4f61-851d-e7effba2a026.png)

  En cuanto este montado y haya realizado alguna prueba, pondre los resultados.
  
  Y ahora ya dentro de su traje de luces:
  
  ![image](https://user-images.githubusercontent.com/48222471/236435262-e4639030-45f1-465d-99fe-1066424c791f.png)

  Por cierto, la caja la he sacado de un sistema que dice corregir el factor de potencia y que nos ahorra mucho dinero en electricidad.
  
  Esto no es cierto por 2 razones: 
  
  1 - empiricamente he podido comprobar que al conectarlo a la red electrica no hacia que el factor de potencia se moviera lo mas minimo.
  
  2- Lleva un componente que trata de asemejarse a un condensador y que realmente esta relleno de arena, y que de de los dos terminales de que dispone, uno esta conectado a otros componentes y el otro terminal no esta conectado a ninguno, aunque si este soldado a la placa de circuito impreso.
  
  En resumen, solo enciende un par de led verdes y no hace nada mas, pero eso si, la caja me ha venido muy bien para mi proyecto (y que es por lo que pedi este "dispositivo") , ya que dispone de conector de CA tipo europeo y hueco suficiente para meter el ESP32, los 2 pulsadores, el buzzer y un alimentador CA/CC 5v.
  
  El SSR no lo he instalado dentro y queda para posterior montaje en otro dispositivo.
  
  Actualmente recibe la potencia que se esta consumiendo en la vivienda via ESP NOW y la muestra en el display. Tambien se baja de internet el precio de la electricidad PVPC para cada hora del día.  
  
  Si el consumo esta por debajo, en este caso de 4600 Watios, se queda encendido el led verde, si esta por encima, se apaga el led verde y se enciende el led rojo, ademas de indicarlo sonoramente mediante un  buzzer.
  
  Por ahora he detectado que consumiendo hasta 6000 Watios, puede estar mas de 30 segundos sin que el ICP del contador inteligente corte la corriente a la vivienda.
  
  
  
  
  
  

  
  
         
         



