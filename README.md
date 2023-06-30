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
![1](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%201.png)
