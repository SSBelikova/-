# Тема 10. Декораторы и исключения
Отчет по Теме #10 выполнил(а):
- Беликова Софья Сергеевна
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### В школе, где вы учились, узнали, что вы крутой программист и попросили написать программу для учителей, которая будет при вводе кабинета писать для него ключ доступа и статус, занят кабинет или нет. При написании программы необходимо использовать словарь (dict), который на вход получает номер кабинета, а выводит необходимую информацию. Если кабинета, который вы ввели нет в словаре, то в консоль в виде значения ключа нужно вывести “None” и виде статуса вывести “False”.

```python
class Car:
    def __init__(self, manufacturer, model):
        # Инициализация атрибутов класса
        self.manufacturer = manufacturer  # Произведитель машины
        self.model = model  # Модель машины
# Создаем объект класса Car
my_car = Car("Toyota", "Corolla")
# Выводим информацию о машине
print(f"Бренд: {my_car.manufacturer}, Модель: {my_car.model}")
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Лаб8_1.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Лабораторная работа №2
### Дополните код из первого задания, добавив в него атрибуты и методы класса, заставьте машину “поехать”. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.
```python
class Car:
    def __init__(self, manufacturer, model):
        self.manufacturer = manufacturer  
        self.model = model 
        self.is_moving = False  # Флаг движения, изначально машина стоит на месте
    def drive(self):
        # Метод, заставляющий машину ехать
        if not self.is_moving:  
            self.is_moving = True  
            print(f"{self.manufacturer} {self.model} движется.")  
        else:
            print(f"{self.manufacturer} {self.model} едет.")
    def stop(self):
        # Метод, останавливающий машину
        if self.is_moving:  
            self.is_moving = False  
            print(f"{self.manufacturer} {self.model} остановлена.")
        else:
            print(f"{self.manufacturer} {self.model} стоит.")
# Создаем объект класса Car
my_car = Car("Toyota", "Corolla")
my_car.drive()  # Машина начинает движение
my_car.stop()   # Машина останавливается
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Лаб8_2.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Лабораторная работа №3
### Создайте новый класс “ElectricCar” с методом “charge” и атрибутом емкость батареи. Реализуйте его наследование от класса, созданного в первом задании. Заставьте машину поехать, а потом заряжаться. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:
    def __init__(self, manufacturer, model):
        self.manufacturer = manufacturer
        self.model = model
    def drive(self):
        print(f"{self.manufacturer} начинает движение.")
class ElectricCar(Car):
    def __init__(self, manufacturer, model, battery_capacity):
        super().__init__(manufacturer, model)
        self.battery_capacity = battery_capacity
    def charge(self):
        print(f"{self.manufacturer} с емкостью батареи заряжается.")
my_electric_car = ElectricCar("Tesla", "Model S", 100)
my_electric_car.drive()
my_electric_car.charge()
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Лаб8_3.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Лабораторная работа №4
### Реализуйте инкапсуляцию для класса, созданного в первом задании. Создайте защищенный атрибут производителя и приватный атрибут модели. Вызовите защищенный атрибут и заставьте машину поехать. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:
    def __init__(self, manufacturer, model):
        self._manufacturer = manufacturer  # Защищенный атрибут для производителя
        self.__model = model  # Приватный атрибут для модели
        self.is_moving = False  # Флаг движения, изначально машина стоит на месте
    def drive(self):
        if not self.is_moving:
            self.is_moving = True
            print(f" {self._manufacturer} {self.__model} едет.")
    def stop(self):
        if self.is_moving:
            self.is_moving = False
            print(f"The {self._manufacturer} {self.__model} стоит.")
# Создаем объект класса Car
my_car = Car("Ford", "Mustang")
my_car.drive()  # Машина начинает движение
print(f"Бренд: {my_car._manufacturer}")  # Доступ к защищенному атрибуту
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Лаб8_4.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Лабораторная работа №5
### Реализуйте полиморфизм создав основной (общий) класс “Shape”, а также еще два класса “Rectangle” и “Circle”. Внутри последних двух классов реализуйте методы для подсчета площади фигуры. После этого создайте массив с фигурами, поместите туда круг и прямоугольник, затем при помощи цикла выведите их площади. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
import math
# Базовый класс Shape
class Shape:
    def area(self):
        pass  # Определим этот метод в дочерних классах
# Класс Rectangle наследует Shape
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    def area(self):
        return self.width * self.height  # Площадь прямоугольника
# Класс Circle наследует Shape
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return math.pi * (self.radius ** 2)  # Площадь круга
# Создаем массив с фигурами
shapes = [Rectangle(4, 5), Circle(3)]
# Выводим площади всех фигур
for shape in shapes:
    print(f"Площадь: {shape.area()}")  # Вызываем метод area для каждой фигуры
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Лаб8_5.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Самостоятельная работа №1
### При создании сайта у вас возникла потребность обрабатывать данные пользователя в странной форме, а потом переводить их в нужные вам форматы. Вы хотите принимать от пользователя последовательность чисел, разделенных пробелом, а после переформатировать эти данные в список и кортеж. Реализуйте вашу задумку.

```python
class Move:
    def __init__(self, title, genre):
        self.title = title
        self.genre = genre
my_move = Move("Властелин колец", "фэнтази")
print(f"Название: {my_move.title}, Жанр: {my_move.genre}")
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Ср8_1.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром. 

## Самостоятельная работа №2
### Самостоятельно создайте атрибуты и методы для ранее созданного класса. Они должны отличаться, от тех, что указаны в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Move:
    def __init__(self, title, genre):
        self.title = title
        self.genre = genre
        self.is_watching = False
    def start_watching(self):
        self.is_watching = True
        print(f"Начать смотреть '{self.title}' жанра {self.genre}.")
    def stop_watching(self):
        self.is_watching = False
        print(f"Прекратить смотреть '{self.title}'.")
my_move = Move("Властелин колец", "фэнтази")
my_move.start_watching()
my_move.stop_watching()
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Ср8_2.png)

## Выводы
Данный код демонстрирует простую реализацию класса Move с методами для отслеживания процесса просмотра фильма.

## Самостоятельная работа №3
### Самостоятельно реализуйте наследование, продолжая работать с ранее созданным классом. Оно должно отличаться, от того, что указано в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Move:
    def __init__(self, title, genre):
        self.title = title
        self.genre = genre

    def start_watching(self):

        print(f"Начать смотреть '{self.title}' жанра {self.genre}.")

class AMove(Move):
    def __init__(self, title, genre, format):
        super().__init__(title, genre)
        self.format = format

    def display_format(self):
        print(f"Формат '{self.title}'  {self.format}.")

my_amove = AMove("Властелин колец", "фэнтази", "mp4")
my_amove.start_watching()
my_amove.display_format()
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Ср8_3.png)

## Выводы
Класс AMove наследует класс Move и добавляет новый атрибут для хранения формата.

## Самостоятельная работа №4
### Самостоятельно реализуйте инкапсуляцию, продолжая работать с ранее созданным классом. Она должна отличаться, от того, что указана в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.
```python
class Move:
    def __init__(self, title, genre):
        self.title = title
        self.__genre = genre
    def get_genre(self):
        return self.__genre
    def set_genre(self, genre):
        self.__genre = genre
my_move = Move("Властелин колец", "фэнтази")
print(f"Жанр: {my_move.get_genre()}")
my_move.set_genre("боевик")
print(f"Новый жанр: {my_move.get_genre()}")
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Ср8_4.png)

## Выводы
Добавляем инкапсуляцию в класс Move, сделав атрибут genre приватным, создаем методы, чтобы получать и изменять значение этого атрибута.

## Самостоятельная работа №5
### Самостоятельно реализуйте полиморфизм. Он должен отличаться, от того, что указан в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.
```python
class Media:
    def get_description(self):
        pass
class Move(Media):
    def __init__(self, title, genre):
        self.title = title
        self.__genre = genre
    def get_description(self):
        return f"Фильм: '{self.title}' жанра {self.__genre}"
class AMove(Media):
    def __init__(self, title, genre, format):
        self.title = title
        self.__genre = genre
        self.format = format
    def get_description(self):
        return f"Видеозапись: '{self.title}' жанр: {self.__genre}, формат: {self.format}"
media_collection = [
    Move("Властелин колец", "фэнтази"),
    AMove("Матрица", "боевик", "mp4")
]
for media in media_collection:
    print(media.get_description())
```
### Результат.
![Меню](https://github.com/SSBelikova/-/blob/Тема_8/Ср8_5.png)

## Выводы
Создадется базовый класс Media, а также два подкласса Move и AMove, добавляется метод get_description, который будет возвращать информацию о том, что это за медиа обьект.

## Общие выводы по теме
1. Изучили основные принципы ООП:
- Инкапсуляция: Этот принцип заключает в себе сокрытие внутренней реализации объекта и предоставление универсальных интерфейсов для взаимодействия с ним. Это помогает защитить данные и снизить сложность кода.
- Наследование: Позволяет создавать новые классы на основе существующих, повторно используя и расширяя функциональность. Это способствует облегчению повторного использования кода и поддержанию иерархии классов.
- Полиморфизм: Обеспечивает возможность использования объектов с одинаковым интерфейсом, независимо от их конкретного типа. Это позволяет создавать общие интерфейсы для различных реализаций, что делает код более гибким и масштабируемым.
2. Изучили структуру классов и объектов, базовые конструкции, переопределение методов
