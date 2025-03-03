# Cargador de baterias de gel sin transformador
Este tipo de cargadores consiste en utilizar y explotar una de las 3 etapas de carga usualmente utilizadas en las baterias de gel plomo.

   Primero, antes de entender como se dá la carga de una batería debemos conocer ciertos parámetros utilizados en estas:
   
>*C: Capacidad de la batería, se expresa como el valor de corriente por tiempo (Ah), sirve para comparar la cantidad de energía
          que puede almacenar una batería*

       
>*CX: Hace referencia al tiempo que le lleva a la bateria cargar/descargar la totalidad de su energía a una taza constante
             de corriente, por ejemplo, una batería de 300Ah C30 le lleva 30 horas otorgar los 300Ah, por lo que la capacidad 
             de corriente máxima de esta será 10A (300Ah/30h = 10A)
             si utilizamos mayor corriente que esta, la capacidad de la batería disminuirá.*

       

**Es importante conocer estos conceptos debido a que todas las curvas que veamos sobre baterías dependerán de la capacidad y del tiempo de cada batería en específico.**
   
<div align="center">
  <p>Para conocer un poco más sobre estas etapas podemos observarlas en el siguiente gráfico</p>
        
</div>


<p align="center">
  <img src="https://github.com/AyrtonRe/Transformerless-battery-charger/blob/f4d6a19c4276a8062f505b1403d495276769aebb/Images/Shield-fig-3.jpg" alt="curvadecarga" width="500">
</p>
<div align="center">
  <p>Curva de carga gel plomo para batería C20</p>
</div>

    Etapa 1 "Bulk": Carga a corriente constante.
     En esta étapa, a corriente constante y siendo la mayor de las 3 etapas, la bateria absorve hasta un 80% de su capacidad. Esta etapa tiene una duración de aproximadamente 4 horas. 

