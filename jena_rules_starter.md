
# Начало работы и заметки по [Jena](https://jena.apache.org) [Rules](https://jena.apache.org/documentation/inference)


Перечень встроенных "функций" языка правил: [https://jena.apache.org/documentation/inference/#RULEbuiltins](https://jena.apache.org/documentation/inference/#RULEbuiltins).


### Префиксы пространств имён

Обязательны. Опускать префиксы нельзя. Например:

``` my:some_entity rdf:type owl:Class```

Способа не указывать префикс: `:some_entity` (как в Turtle) пока не найдено.
Сокращение `rdf:type` до `a` (как в Turtle) не допускается.


### Комментарии

Строка, начинающаяся с символа `#` (без отступа), считается однострочным комментарием. Отступ перед `#` в начале строки приведёт к синтаксическим ошибкам или неверной интерпретации правила.
Многострочные комментарии, насколько мне известно, не предусмотрены.


### Создание новых объектов (узлов, экземпляров)

Возможно создание только узлов типа bnode (blank node) - так называемых "анонимных" узлов. Такие узлы не имеют своего IRI (т.е. не имеют ни пространства имён, ни локального имени). В редакторе Standford Protege такие узлы нельзя редактировать и можно весьма ограниченно просматривать.

Для создания новых bnode предназначены функции (см. [документацию](https://jena.apache.org/documentation/inference/#RULEbuiltins)):

```
makeTemp(?x)
makeInstance(?x, ?p, ?v)
makeInstance(?x, ?p, ?t, ?v)
makeSkolem(?x, ?v1, ... ?vn)
```

Для того, чтобы их правильно применять, стоит прочитать этот [ответ на StackOverflow](https://stackoverflow.com/questions/22072403/create-individuals-inside-of-jena-rules).
