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


## Funcionamiento del cargador sin transformador
Conociendo parte del comportamiento de la batería, podemos analizar el proceso y circuito de carga utilizado en este tipo de cargadores.
### Proceso de carga
El proceso de carga se basa en explotar la anteriormente vista **etapa 3 o etapa "De flotación"**, esto debido a que es la única etápa que puede permanecer con una corriente constante sin dañar la batería, ya que la tensión o corriente de flotación es la que está 
*permanentemente* aplicada a las baterías para evitar que estas se descarguen.
<p>El principio es sencillo, sabiendo que la resistencia interna de la batería disminuye con la carga, si mantengo constante la corriente que aplico sobre esta, la tensión será inversamente proporcional a la resistencia interna, es decir que cuando la batería esté descargada será cuando mayor tensión tenga aplicada, a medida que se va cargando la tensión disminuirá</p>




