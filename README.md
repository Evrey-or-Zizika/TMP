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
![7](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%204.png)
```
class Studying_In_Institute:
 
    def accept(self, visitor):
        visitor.visit(self)
 
    def teaching(self, visitor):
        print(self, "Taught by ", visitor)
 
    def studying(self, visitor):
        print(self, "studied by ", visitor)
 
    def __str__(self):
        return self.__class__.__name__
 
class SDE(Studying_In_Institute): pass
 
class STL(Studying_In_Institute): pass
 
class DSA(Studying_In_Institute): pass
 
class Visitor:
 
    def __str__(self):
        return self.__class__.__name__
 
class Instructor(Visitor):
    def visit(self, crop):
        crop.teaching(self)
 
 
class Student(Visitor):
    def visit(self, crop):
        crop.studying(self)
 
sde = SDE()
stl = STL()
dsa = DSA()
 
instructor = Instructor()
student = Student()
 
sde.accept(instructor)
sde.accept(student)
 
stl.accept(instructor)
stl.accept(student)
 
dsa.accept(instructor)
dsa.accept(student)
```
Вывод:
```
SDE Taught by  Instructor
SDE studied by  Student
STL Taught by  Instructor
STL studied by  Student
DSA Taught by  Instructor
DSA studied by  Student
```
```
@startuml
interface Visitor.Studying_In_Institute {
+ void accept()
+ void teaching()
+ void studying()
}
class Visitor.Instructor {
+ void visit()
+ void teaching()
}
class Visitor.Student {
+ void visit()
+ void studying()
}
class Visitor.SDE {
+ void create(ProjectClass)
+ void create(DataBase)
+ void create(Test)
}
class Visitor.STL {
+ void beWritten(Developer)
}
class Visitor.DSA {
+ {static} void main(String[])
}
Visitor.DSA <|.. Visitor.Student
Visitor.DSA <|.. Visitor.Instructor
Visitor.SDE <|.. Visitor.Student
Visitor.SDE <|.. Visitor.Instructor
Visitor.STL <|.. Visitor.Student
Visitor.STL <|.. Visitor.Instructor
Visitor.Studying_In_Institute <|.. Visitor.Instructor
Visitor.Studying_In_Institute <|.. Visitor.Student
@enduml
```
![8](https://github.com/Evrey-or-Zizika/TMP/blob/main/lab%20%204_1.png)
# Практика 5
```
class WindowFactory:
    @classmethod
    def create_window(cls, name):
        return cls.Window(name)
    @classmethod
    def create_button(cls, name):
        return cls.Button(name)

class MacOsFactory(WindowFactory):
    class Window:
        def __init__(self, name):
            self.name = name
            self.button = []
            self.style = 'Mac Os window style'
        def add_button(self, btn):
            self.button.append(btn.name)
        def show(self):
            print( '{} - {} and {}'.format(self.name, self.style, self.button))
    class Button:
        def __init__(self, name):
            self.name = name
            self.style = 'Mac Os button style'

class LinuxFactory(WindowFactory):
    class Window:
        def __init__(self, name):
            self.name = name
            self.button = []
            self.style = 'Ubuntu window style'
        def add_button(self, btn):
            self.button.append(btn.name)
        def show(self):
            print( '{} - {} and {}'.format(self.name, self.style, self.button))
    class Button:
        def __init__(self, name):
            self.name = name
            self.style = 'Ubuntu button style'

def create_dialog(factory):
    wind = factory.create_window('Form1')
    button = factory.create_button('Button1')
    wind.add_button(button)
    return wind


w = create_window(LinuxFactory)
w.show()
```
```
from lance import *
class Builder(object):
    def build_body(self):
        raise NotImplementedError()
 
    def build_lamp(self):
        raise NotImplementedError()
 
    def build_battery(self):
        raise NotImplementedError()
 
    def create_flashlight(self):
        raise NotImplementedError()
 
 
class Flashlight(object):
    def __init__(self, body, lamp, battery):
        self._shine = False
        self._body = body
        self._lamp = lamp
        self._battery = battery
 
    def on(self):
        self._shine = True
 
    def off(self):
        self._shine = False
 
    def __str__(self):
        shine = 'on' if self._shine else 'off'
        return 'Flashlight [%s]' % shine
 
 
class Lamp(object):
    """Лампочка"""
 
 
class Body(object):
    """Корпус"""
 
 
class Battery(object):
    """Батарея"""
 
 
class FlashlightBuilder(Builder):
    def build_body(self):
        return Body()
 
    def build_battery(self):
        return Battery()
 
    def build_lamp(self):
        return Lamp()
 
    def create_flashlight(self):
        body = self.build_body()
        lamp = self.build_lamp()
        battery = self.build_battery()
        return Flashlight(body, lamp, battery)
 
 
builder = FlashlightBuilder()
flashlight = builder.create_flashlight()
flashlight.on()
print flashlight
```
```
from abc import ABCMeta, abstractmethod
class IA(metaclass=ABCMeta):
    "An interface for an object"
    @staticmethod
    @abstractmethod
    def method_a():
        "An abstract method A"
class ClassA(IA):
    "A Sample Class the implements IA"
    def method_a(self):
        print("method A")
class IB(metaclass=ABCMeta):
    "An interface for an object"
    @staticmethod
    @abstractmethod
    def method_b():
        "An abstract method B"
class ClassB(IB):
    "A Sample Class the implements IB"
    def method_b(self):
        print("method B")
class ClassBAdapter(IA):
    "ClassB does not have a method_a, so we can create an adapter"
    def __init__(self):
        self.class_b = ClassB()
    def method_a(self):
        "calls the class b method_b instead"
        self.class_b.method_b()

ITEMS = [ClassA(), ClassB()]
for item in ITEMS:
    if isinstance(item, ClassB):
        item.method_b()
    else:
        item.method_a()

ITEMS = [ClassA(), ClassBAdapter()]
for item in ITEMS:
    item.method_a()
```
Вывод:
```
method A
method B
method A
method B
```
```
from abc import ABCMeta, abstractmethod
class IMediator(metaclass=ABCMeta):
    "The Mediator interface indicating all the methods to implement"
    @staticmethod
    @abstractmethod
    def colleague1_method():
        "A method to implement"
    @staticmethod
    @abstractmethod
    def colleague2_method():
        "A method to implement"
class Mediator(IMediator):
    "The Mediator Concrete Class"
    def __init__(self):
        self.colleague1 = Colleague1()
        self.colleague2 = Colleague2()
    def colleague1_method(self):
        return self.colleague1.colleague1_method()
    def colleague2_method(self):
        return self.colleague2.colleague2_method()
class Colleague1(IMediator):
    "This Colleague calls the other Colleague via the Mediator"
    def colleague1_method(self):
        return "Here is the Colleague1 specific data you asked for"
    def colleague2_method(self):
        "not implemented"
class Colleague2(IMediator):
    "This Colleague calls the other Colleague via the Mediator"
    def colleague1_method(self):
        "not implemented"
    def colleague2_method(self):
        return "Here is the Colleague2 specific data you asked for"
MEDIATOR = Mediator()

DATA = MEDIATOR.colleague2_method()
print(f"COLLEAGUE1 <--> {DATA}")

DATA = MEDIATOR.colleague1_method()
print(f"COLLEAGUE2 <--> {DATA}")
```
Вывод:
```
COLLEAGUE1 <--> Here is the Colleague2 specific data you asked for
COLLEAGUE2 <--> Here is the Colleague1 specific data you asked for
```
