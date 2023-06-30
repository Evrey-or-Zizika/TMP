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
