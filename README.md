# Задача "Исследование JVM через VisualVM"
## Описание

В момент загрузки класса, Classloader`ы  выделяют в Metaspace память для списка констант, данных о методах, полях и об имени самого класса

Стрелка 1  - интервал подгрузки 529 классов 

Стрелка 2 - интервал подгрузки 2117 классов

Стрлека 3 - интервал подгрузки 869 классов

Стрелка 4 показывает, что JVM так же выделяет память в Metaspace для классов, которые участвуют при создании объектов

![image3](https://raw.githubusercontent.com/MaximeNefedov/VisualVM_JVM/master/screenshots/screen1.png)

![image2](https://raw.githubusercontent.com/MaximeNefedov/VisualVM_JVM/master/screenshots/metaspace.png)


Два следующих изображения демонстрируют, что в момент создания объекта JVM выделяет для него место в области памяти, называемой Heap. Heap подразделяется на: 
* Young generation:
    * Eden. Cюда попадают все вновь созданные объекты
    * Survivor. Если вновь созданный объект выживает в ходе сборки мусора, то попадет в эту группу.
    Survivor делится на: 
        * S0
        * S1
* Old generation. Под "старым поколением" понимаются долгоживущие объекты, прошедшие проверки сборщика мусора. Как правило, ссылки на такие объекты существуют долго (например, в течение всего фрейма в Stack Memory)

Такое разделение позволяет сборщику мусора не проверять весь Heap а проводить сборку фрагментарно


![image4](https://raw.githubusercontent.com/MaximeNefedov/VisualVM_JVM/master/screenshots/screen2.png)

![image](https://raw.githubusercontent.com/MaximeNefedov/VisualVM_JVM/master/screenshots/heap.png)