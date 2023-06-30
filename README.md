# Практика 1
```
@startuml "Лабораторная работа 1"
left to right direction 
skinparam packageStyle rect
actor Читатель
actor Управляющий
rectangle информационная_система_библиотеки {
:Читатель: -- (Поиск книги)
:Читатель: -- (Возврат книги)
:Читатель: -- (Добавить книгу в фонд)
:Поиск книги: ..> (Выдача книги):<<include>>
:Управляющий: -- (Списать книги из фонда)
:Управляющий: -- (Отслеживание сданных книг)
:отслеживание сданных книг: ..> (Выдача книги):<<include>>
:Возврат книги: ..> (Отслеживание сданных книг):<<include>>
}
@enduml
```
![1](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%201.png)
```
@startuml
class Читатель {
+Паспортные данные
+ФИО
+Список взятых книг
}
class Управляющий{
+Паспортные данный
+ФИО
+список читателей
}
class взять_книгу{
+Название книги
+ФИО автора
+взятие книги
}
class сдать_книгу{
+Название книги
+ФИО автора
+сдача книги
}
Читатель --> взять_книгу:заявка на взятие книги
Управляющий --> взять_книгу:проверка несданных книг
Читатель --> сдать_книгу:сдача книги
Управляющий --> сдать_книгу:удаление из списка не сданных книг
взять_книгу --> выполнение_действия
сдать_книгу --> выполнение_действия
@enduml
```
![2](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%201_1.png)
# Практика 2
```
@startuml
title диаграмма последовательности
participant Читатель
participant Заявка
participant Управляющий
activate Читатель
Читатель -> Заявка:подает заявку
activate Заявка
Заявка -> Управляющий:выдает заявку
deactivate Читатель
activate Управляющий
Управляющий -> Заявка:оценивает заявку
Заявка -> Управляющий:заявка одобрена
deactivate Заявка
activate Читатель
Управляющий -> Читатель:оценивает читателя
Читатель -> Управляющий:читатель одобрен
Управляющий -> Читатель:выдача или принятие книги
@enduml
```
![3](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%202.png)
```
@startuml
left to right direction
title диаграмма развертывания
database Заявка
node Читатель
node Управляющий
Управляющий - Читатель: оценивает
Управляющий - Заявка: оценивает.    
Читатель - Заявка: подает
Управляющий - Читатель: выдает книги
@enduml
```
![4](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%202_1.png)
# Практика 3
```
@startuml
title Пратическая работа 3: Strategy
class Variant{
selection()
}
class Game{
strategy: Variant
init()
play()
}
class Paper{
selection()
}
class Rock{
selection()
}
class Scissors{
selection()
}
class Bottle{
selection()
}
class Hand{
selection()
}
class main{
int n
str vibor
playtime()
player1.play(player2)
}
note right of main::"playtime()"
player1 = playtime(vibor)
player2 = playtime(vibor)
end note
Paper --> Variant
Rock --> Variant
Scissors --> Variant
Bottle --> Variant
Hand --> Variant
main *--> Variant
main --Game
@enduml
```
![5](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%203.png)
```
@startuml
title Пратическая работа 3: Template Method
class Algorithm{
template_method()
flagstock()
draw_1()
draw_2()
draw_3()
final()
printer()
}
note right of Algorithm::"template_method()"
self.flagstock()
self.draw_1()
self.draw_2()
self.draw_3()
self.final()
self.printer()
end note
class colors{
painwhite()
painred()
painblue()
}
class France{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
final()
}
class  Germany{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
}
Algorithm <|-- Germany :Немецкий флаг
Algorithm <|-- France : Французский флаг
France -  Germany
(France, Germany) - colors:Задает цвет
@enduml
```
![6](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%203_1.png)
# Практика 4
```
def alphabets_upto(letter):
    for i in range(65, ord(letter)+1):
            yield chr(i)
 
if __name__ == "__main__":
 
    alphabets_upto_K = alphabets_upto('K')
    alphabets_upto_M = alphabets_upto('M')
 
    for alpha in alphabets_upto_K:
        print(alpha, end=" ")
 
    print()
 
    for alpha in alphabets_upto_M:
        print(alpha, end=" ")

def inBuilt_Iterator1():
     
    alphabets = [chr(i) for i in range(65, 91)]
     
    for alpha in alphabets:
        print(alpha, end = " ")
    print()
 
def inBuilt_Iterator2():
     
    alphabets = [chr(i) for i in range(97, 123)]
     
    for alpha in alphabets:
        print(alpha, end = " ")
    print()
 
if __name__ == "__main__" :
    inBuilt_Iterator1()
    inBuilt_Iterator2()
```
Вывод:
```
A B C D E F G H I J K 
A B C D E F G H I J K L M A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 
a b c d e f g h i j k l m n o p q r s t u v w x y z
```
```
@startuml
interface Iterator.Iterator {
+ boolean hasNext()
+ Object next()
}
interface Iterator.Aggregate {
+ Create Iterator()
+ Iterator()
}
class Iterator.Concrete_Iterator {
+ {static} void hasNext():Next
}
class Iterator.Concrete_Aggregate {
+ {static} void Create Iterator():Iterator
}
Iterator.Iterator <|..|> Iterator.Aggregate
Iterator.Aggregate ..> Iterator.Concrete_Iterator
Iterator.Concrete_Iterator ..> Iterator.Iterator
Iterator.Concrete_Aggregate ..> Iterator.Aggregate
@enduml
```
