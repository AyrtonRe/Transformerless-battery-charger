# Cargador de baterias de gel sin transformador
Este tipo de cargadores consiste en utilizar y explotar una de las 3 etapas de carga usualmente utilizadas en las baterias de gel plomo.

   Primero, antes de entender como se dá la carga de una batería debemos conocer ciertos parámetros utilizados en estas:
   
>*C: Capacidad de la batería, se expresa como el valor de corriente por tiempo (Ah), sirve para comparar la cantidad de energía
          que puede almacenar una batería*

       
>*CX: Hace referencia al tiempo que le lleva a la bateria cargar/descargar la totalidad de su energía a una taza constante
             de corriente, por ejemplo, una batería de 300Ah C30 le lleva 30 horas otorgar los 300Ah, por lo que la capacidad 
             de corriente máxima de esta será 10A (300Ah/30h = 10A)
             si utilizamos mayor corriente que esta, la capacidad de la batería disminuirá.*



>Resistencia interna: Se posee dos tipos de resistencia interna, siendo "Rohm" la resistencia ohmica dada entre los contactos
           de la batería y la resistencia "Rpol" llamada de polarización, la cual depende de la resistividad entre anódo-electrólito-cátodo.
           Donde esta última es variable en función del estado de carga, mientras que la primera es constante

       

**Es importante conocer estos conceptos debido a que todas las curvas que veamos sobre baterías dependerán de la capacidad y del tiempo de cada batería en específico.**
   
<div align="center">
  <p>Para conocer un poco más sobre estas etapas podemos observarlas en el siguiente gráfico</p>
        
</div>

<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/f4d6a19c4276a8062f505b1403d495276769aebb/Images/Shield-fig-3.jpg" alt="curvadecarga" width="500">
</p>

<div align="center">
  <p> 
    <a href="https://www.shieldbatteries.co.uk/documents/BESTmag%20issue%2072%20charging.pdf">Curva de carga gel plomo para batería C20</a>
  </p>
</div>



   >Etapa 1 "Bulk": Carga a corriente constante.
     En esta étapa la corriente es constante y la mayor de las 3 etapas debido a que la batería tiene la menor tensión entre bornes (debido a que está descargada), esto se logra aumentando progresivamente la tensión aplicada a la batería a medida que aumenta la tensión absorvida, a su vez la resistencia interna es la más alta de todas las etapas. Esta etápa finaliza al alcanzar el valor de tensión conocido como "tensión de absorción".
      <p>Etapa 2 "Absorción": Carga a tensión constante.
     En esta étapa, a tensión constante igual a la de absorción, la corriente disminuye progresivamente, esto debido a que la tensión en bornes de la batería aumenta gradualmente, si bien la resistencia interna disminuye (lo que debería aumentar la corriente) esta 
     disminución es menor en proporción al aumento de la tensión en bornes, por lo que la corriente disminuirá.<p/>
      Etapa 3 "Flotación": Carga a tensión constante, menor a la etapa 2.
     En esta étapa la tensión se disminuye hasta la conocida como "tensión de flotación", a su vez la corriente sigue disminuyendo progresivamente, pero será menor a la presente en la anterior etapa debido a que la tensión aplicada será menor.
     
Presentadas las **etapas ideales de carga**, cabe recalcar que la variación de la resistencia interna (principalmente Rpol) se dá debido a que en estado descargada, el electrolíto disminuye su concentración de ácido sulfúrico (H₂SO₄), esto genera que la resistencia entre ánodo-electrilíto-cátodo sea mayor, debido a que la conductividad eléctrica del electrolíto depende de la concentración de ácido sulfúrico, comparados al estado de carga, en el cual el electrolíto tiene la mayor concentración de ácido sulfúrico, lo que provoca que se tenga menor resistencia interna. La variación de la concentración de H₂SO₄ está explicada en el [siguiente artículo](https://www.pveducation.org/pvcdrom/batteries/lead-acid-batteries#:~:text=A%20lead%20acid%20battery%20consists,of%20sulfuric%20acid%20and%20water.)

<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/44719e3852ff6166a3bef7ba67029e644e6f465f/Images/partone-22f.jpg" alt="curvadecarga" width="500">
</p>
<div align="center">
  <p> 
    <a href="https://batteryuniversity.com/article/how-does-internal-resistance-affect-performance">Variación de la resistencia interna en función de la tensión en bornes</a>
  </p>
</div>

   Entonces, esta es la única forma de cargar las baterías?
   
 >No, esta es la **forma ideal de carga** en cuanto a velocidad y seguridad, respetando ciertos estándares y valores para no generar sobrecalentamiento ni desgastes innecesarios en la batería.

 <p>No sería más rápido mantener la etapa 1 (Bulk) todo el tiempo? <p/>
    
  >Sí, pero la tensión de mantenimiento de la batería es la tensión de flotación, si mantenemos alimentada la batería con una tensión mayor a esta estaríamos generando una sobrecarga constante.


## Funcionamiento del cargador
Conociendo parte del comportamiento de la batería, podemos analizar el proceso y circuito de carga utilizado en este tipo de cargadores.
### Proceso de carga
El proceso de carga se basa en explotar la anteriormente vista **etapa 3 o etapa "De flotación"**, esto debido a que es la única etápa que puede permanecer con una corriente constante sin dañar la batería, ya que la tensión o corriente de flotación es la que está 
*permanentemente* aplicada a las baterías para evitar que estas se descarguen.
<p>El principio es sencillo, sabiendo que la resistencia interna de la batería disminuye con la carga, si mantengo constante la corriente que aplico sobre esta, la tensión en la batería será inversamente proporcional a la resistencia interna, es decir que cuando la batería esté descargada será cuando menor tensión tenga aplicada, a medida que se va cargando la tensión aumenta.</p>
<p> Esto es más sencillo de ver si se dibuja el circuito</p>
<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/9d37872dae6c7b9087c2393add23b4f8aac79e50/Images/DFSGWSERTAHRTWSH.png" alt="Circuito de carga" width="500">
</p>
<div align="center">
  <p> 
    <a>Circuito de carga corriente constante</a>
  </p>
</div>

Si aplicamos las leyes de Kirchoff en el circuito, vemos que:
>Vfuente = Vbat - I * Rbat

Si ahora de alguna manera logramos que esa corriente sea constante, teniendo en cuenta que la "Rbat" disminuirá con el tiempo, si ademas mantenemos la "Vfuente" constante, el producto I*Rbat disminuirá en igual medida que el incremento de Vbat.
>Es decir que la tensión en la batería aumentará debido a la disminución de su resistencia interna, este proceso se dará hasta que se llegue al punto en que la variación de la Resistencia sea muy pequeña, todo este proceso se tiene en cuenta en la etapa de flotación, ya que la misma consiste en aplicar tanto tensión como corriente prácticamente constante.

### Circuito de carga
Sabiendo en qué consiste el proceso de carga, vemos que para realizar la carga de la batería solo basta con aplicar una corriente constante tal que sea similar a la prevista para la etápa de flotación, este proceso solo se aplica de forma eficiente para baterías del tipo "stand by" (baterías que solo se descargan rara vez, diferente a las baterías "cíclicas" las cuales cumplen ciclos de descarga rápidos) debido a que es un ciclo de carga muy lento, por lo que solo llegará a cargar totalmente la batería si esta no se utiliza en mucho tiempo.
<p>Ahora veamos el circuito genérico de carga que se utiliza en estos cargadores<p/>
<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/ce79e21a618f1887ee3a131c80c7e21291c04631/Images/DFSGWSERdfghdfghTAHRTWSH.png" alt="Circuito de carga" width="500">
</p>
<div align="center">
  <p> 
    <a>Circuito de carga</a>
  </p>
</div>
Lo primero que notamos es que la entrada es de 220V CA, y que el circuito tiene el paralelo de una resistencia (R1) y un capacitor (C1) en serie con la batería, pasando previamente por un puente rectificador.
<p>La parte más imporante para este circuito es la elección del capacitor "C1", ya que este será el que limite la corriente de todo el circuito, esto es sencillo de ver si aplicamos Kirchoff</p>
<p>Si ignoramos las caídas en los diodos, tendríamos</p>

> Vrms= I * Zeq + I * Rbat + Vbat

Pero como vimos anteriormente, la Rbat suele ser muy pequeña, sobretodo comparado con los 2100 (Ohms) del capacitor, por lo que el cálculo de la corriente se puede expresar como 
> Vrms= I * Zeq + Vbat

Es decir que la corriente será prácticamente constante, ya que solo variará en función de la carga de la batería, pero esta será a lo sumo de 5 o 12 (V), lo cual no representaría nada respecto a los 220(Vrms) de la onda aplicada, por lo que la corriente de carga o flotación solo dependerá de la reactancia del capacitor.

<p>El problema de este circuito es que no posee ningún tipo de protección, solo se limíta la carga por el valor de corriente, el cual debe estar bien calculado dependiendo de la capacidad de la batería a cargar</p>

>Diferentes marcas de baterías recomiendan diferentes valores de corrientes de flotación, pero estos valores suelen estar entre el 2 y 1 por ciento de la capacidad de la batería, es decir, si tengo una batería de 1,2 (Ah) debería cargarla con una corriente de entre 24 a 12(mA)

Para el caso del circuito presentado, el mismo alimenta dos baterías de 2,4 (Ah) en parelelo, por lo que por recomendación la corriente de flotación debería ser de entre 48 y 96 (mA)
*<p>Pero, se cumplirá este valor?</p>*
Para ver esto basta con medir la corriente de alimentación del circuito, lo cual se puede ver en la siguiente imagen

<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/e3fb73e702baee1251ceca604a9c3a3724d86178/Images/IMG_20250302_210753_300.jpg" alt="Corriente de flotación" width="500">
</p>
<div align="center">
  <p> 
    <a>Corriente de flotación, medida con un nucleo de 50 vueltas</a>
  </p>
</div>
Vemos que la pinza marca 4.58(A), pero como está pasando por un nucleo de 50 vueltas, la medición real es de 91(mA) por lo que vemos que se cumple lo recomendado. 

## Posibles mejoras para el circuito
Como se mencionó anteriormente, uno de los puntos débiles de este circuito es que no posee corte por tensión, es decir que en caso de no estár bien calculada la corriente de flotación (caso de agregar baterías diferentes a las de fábrica) la tensión de la batería subiría por encima de la recomendada, generando una sobrecarga
<p>Para evitar esto, se puede proteger la batería mediante uno de dos posibles dispositivos</p>

### Mediante diodo zenner
Esta es tal vez la forma más fácil, consiste en agregar un diodo zenner en paralelo a bornes de la batería, para así limitar la tensión que se pérmite en estos, este diodo podría ser de 5.1(V) para el caso de cargar una batería de 4(V), el mismo debe estár acompañado por una resistencia previa a este para limitar la corriente, idealmente de valor bajo (pero teniendo en cuenta la corriente/potencia del zenner) para no interferir con el valor del capacitor.
<p>Un ejemplo de este circuito podría verse así</p>

<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/f84a6abce74bc7af588f4ce4edd388ffbc325e99/Images/zenner.png" alt="Zenner protection" width="500">
</p>
<div align="center">
  <p> 
    <a>Circuito con protección por zenner</a>
  </p>
</div>
El valor de 220(ohm) de R2 no debe tomarse a cuenta, ya que solo es ilustrativo, este corresponderá a la potencia del zenner, tensión de éste y a la tensión de flotación de la batería.

### Mediante regulador de tensión
Esta es la forma más correcta
<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/e841dd973e3d1456ab5a55cb48bc1cfc342af701/Images/zenner.png" alt="Zenner protection" width="500">
</p>
<div align="center">
  <p> 
    <a>Circuito con protección por zenner</a>
  </p>
</div>
El valor de 10(ohm) de R2 no debe tomarse a cuenta, ya que solo es ilustrativo, este corresponderá a la potencia del zenner y a la tensión de flotación de la batería
