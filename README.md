# C#-lab01 Сергеев Ярослав ИУ8-31
## Цели работы:
  1. Научиться работать с переменными разных типов данных CTS средствами языка C#.
  2. Научиться создавать классы и поля классов, инициализировать свойства классов. Научиться создавать перегруженные конструкторы классов.
  3. Научиться создавать тесты для реализованных методов и классов.

## Задание №1
Выведите на консоль минимальные и максимальные значения для предопределенных типов данных CTS.

## Задание №2
Создайте класс с именем Rectangle.
В теле класса создайте два поля, описывающие длины сторон double sideA, sideB.
Создайте пользовательский конструктор Rectangle(double sideA, double sideB), в теле которого поля sideA и sideB инициализируются значениями аргументов.
Создайте два private метода, вычисляющие площадь прямоугольника - double CalculateArea() и периметр прямоугольника - double CalculatePerimeter ().
Создайте два свойства double Area и double Perimeter с одним методом доступа get, вызывающим созданные ранее методы.
Напишите программу, которая принимает от пользователя длины двух сторон прямоугольника и выводит на экран периметр и площадь. Покройте тестами методы класса Rectangle.

## Задание №3
Создайте классы Point и Figure.
Класс Point должен содержать два целочисленных поля с координатами точки.
Создайте два свойства с одним методом доступа get.
Создайте пользовательский конструктор, в теле которого проинициализируйте поля значениями аргументов.
Класс Figure должен содержать конструкторы, которые принимают от 3-х до 5-ти аргументов типа Point, а также строковое автосвойство для хранения названия фигуры. Используйте ключевое слово this для вызова перегруженных конструкторов, избегайте дублирования кода.
Создайте два метода: double LengthSide(Point A, Point B), который рассчитывает длину стороны многоугольника; double PerimeterCalculator(), который рассчитывает периметр многоугольника.
Напишите программу, которая выводит на экран название и периметр многоугольника. Покройте тестами методы класса Figure.

## Код задания № 1
  
    Console.WriteLine("\t \t Минимальные и максимальные значения предопределенных типов данных CTS:");
    Console.WriteLine("=========================================================");
    
    // Целочисленные типы данных
    Console.WriteLine("Целочисленные типы данных:");
    Console.WriteLine($"byte: min = {byte.MinValue}, max = {byte.MaxValue}");
    Console.WriteLine($"sbyte: min = {sbyte.MinValue}, max = {sbyte.MaxValue}");
    Console.WriteLine($"short: min = {short.MinValue}, max = {short.MaxValue}");
    Console.WriteLine($"ushort: min = {ushort.MinValue}, max = {ushort.MaxValue}");
    Console.WriteLine($"int: min = {int.MinValue}, max = {int.MaxValue}");
    Console.WriteLine($"uint: min = {uint.MinValue}, max = {uint.MaxValue}");
    Console.WriteLine($"long: min = {long.MinValue}, max = {long.MaxValue}");
    Console.WriteLine($"ulong: min = {ulong.MinValue}, max = {ulong.MaxValue}");
    Console.WriteLine("=========================================================");
    
    // Типы данных с плавающей точкой
    Console.WriteLine("Типы данных с плавающей точкой:");
    Console.WriteLine($"float: min = {float.MinValue}, max = {float.MaxValue}");
    Console.WriteLine($"double: min = {double.MinValue}, max = {double.MaxValue}");
    Console.WriteLine($"decimal: min = {decimal.MinValue}, max = {decimal.MaxValue}");
    Console.WriteLine("=========================================================");
    
    // Логический тип данных
    Console.WriteLine("Логический тип данных:");
    Console.WriteLine($"bool: true / false");
    Console.WriteLine("=========================================================");
    
    // Символьный тип данных
    Console.WriteLine("Символьный тип данных:");
    Console.WriteLine($"char: min = {char.MinValue}, max = {char.MaxValue}");
    Console.WriteLine("=========================================================");
    
    // Структуры
    Console.WriteLine("Структуры:");
    Console.WriteLine($"DateTime: min = {DateTime.MinValue}, max = {DateTime.MaxValue}");
    Console.WriteLine($"TimeSpan: min = {TimeSpan.MinValue}, max = {TimeSpan.MaxValue}");
    Console.WriteLine("=========================================================");
    
    // Тип значений null
    Console.WriteLine("Тип значений null:");
    Console.WriteLine($"Nullable<T>: null");
    Console.WriteLine("=========================================================");
    
## Код задания № 2
    
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Xml.Linq;
    
    // Объявление пространства имен для проекта
    namespace lab01_2
    {
        public class Rectangle
        {
            // Поля для сторон прямоугольника
            private double sideA;
            private double sideB;
    
            // Конструктор
            public Rectangle(double sideA, double sideB)
            {
                this.sideA = sideA;
                this.sideB = sideB;
            }
    
            // Свойства для получения сторон
            public double SideA
            {
                get { return sideA; }
            }
    
            public double SideB
            {
                get { return sideB; }
            }
    
            // Свойство для площади
            public double Area
            {
                get { return sideA * sideB; }
            }
    
            // Свойство для периметра
            public double Perimeter
            {
                get { return 2 * (sideA + sideB); }
            }
        }
    
        // Основной класс программы
        class MyProgram
        {
            // Точка входа в программу
            static void Main()
            {
                // Запрос у пользователя длины первой стороны прямоугольника
                Console.Write("Первая сторона прямоугольника: ");
                double sideA = Convert.ToDouble(Console.ReadLine());
    
                // Запрос у пользователя длины второй стороны прямоугольника
                Console.Write("Вторая сторона прямоугольника: ");
                double sideB = Convert.ToDouble(Console.ReadLine());
    
                // Создание экземпляра класса Rectangle с введенными сторонами
                Rectangle rectangle = new Rectangle(sideA, sideB);
    
                // Вывод информации о прямоугольнике
                Console.WriteLine($"Введён прямоугольник со сторонами: {rectangle.SideA} и {rectangle.SideB}");
                Console.WriteLine($"Площадь прямоугольника: {rectangle.Area}");
                Console.WriteLine($"Периметр прямоугольника: {rectangle.Perimeter}");
            }
        }
    }
    
## Тесты для задания № 2
    
    using lab01_2;
    
    namespace Lab01_2nd_tests
    {
        [Parallelizable(ParallelScope.Self)]
        [TestFixture]
        public class Tests
        {
            [Test]
            public void RectangleConstructor_CorrectInitialization()
            {
                int sideA = 3, sideB = 4;
                Rectangle rectangle = new Rectangle(sideA, sideB);
                Assert.AreEqual(sideA, rectangle.SideA);
                Assert.AreEqual(sideB, rectangle.SideB);
            }
            [Test]
            public void CalculateArea_Correct()
            {
                Rectangle test = new Rectangle(3, 3);
                Assert.AreEqual(9, test.Area);
            }
            [Test]
            public void CalculatePerimeter_Correct()
            {
                Rectangle test = new Rectangle(3, 3);
                Assert.AreEqual(12, test.Perimeter);
            }
    
        }
    }
    
## Код задания № 3
    
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Reflection.Metadata;
    using System.Text;
    using System.Threading.Tasks;
    using System.Xml.Linq;
    
    // Пространство имен, в котором определены классы для программы
    namespace lab01_3
    {
        // Класс Point представляет точку на плоскости с координатами x и y
        public class Point
        {
            private int x, y;  // Поля для хранения координат точки
    
            // Конструктор, который принимает координаты x и y и сохраняет их в полях класса
            public Point(int x, int y)
            {
                this.x = x;
                this.y = y;
            }
    
            // Свойство только для чтения для доступа к координате x
            public int X
            {
                get
                {
                    return x;
                }
            }
    
            // Свойство только для чтения для доступа к координате y
            public int Y
            {
                get
                {
                    return y;
                }
            }
        }
    
        // Класс Figure представляет геометрическую фигуру, состоящую из набора точек
        public class Figure
        {
            private Point[] points;
    
            public string Name { get; private set; }
    
            // Универсальный конструктор, который принимает от 3 до 5 точек
            public Figure(params Point[] inputPoints)
            {
                points = inputPoints;
    
                // Назначение имени в зависимости от числа точек
                switch (points.Length)
                {
                    case 3:
                        Name = "Треугольник";
                        break;
                    case 4:
                        Name = "Четырехугольник";
                        break;
                    case 5:
                        Name = "Пятиугольник";
                        break;
                }
            }
    
            // Метод для расчета длины стороны между двумя точками
            public double LengthSide(Point A, Point B)
            {
                int dx = A.X - B.X;  // Разница по координате x
                int dy = A.Y - B.Y;  // Разница по координате y
                return Math.Sqrt(dx * dx + dy * dy);  // Вычисление длины через теорему Пифагора
            }
    
            // Метод для расчета периметра фигуры, суммируя длины всех сторон
            public double PerimeterCalculator()
            {
                double perimeter = 0;
                // Перебор всех точек фигуры для расчета периметра
                for (int i = 0; i < points.Length; i++)
                {
                    // Суммирование длин сторон между каждой точкой и следующей (с замыканием на первую точку)
                    perimeter += LengthSide(points[i], points[(i + 1) % points.Length]);
                }
                return perimeter;  // Возвращение периметра
            }
        }
    
        // Главный класс программы
        class Program
        {
            // Метод Main — точка входа в программу
            static void Main(string[] args)
            {
                // Флаг для параметров ввода 
                bool flg = false;
    
                // Количество вершин многоугольника
                int numberVertices = 0;
    
                // Создание списка для хранения точек-вершин фигуры
                List<Point> vertices = new List<Point>(numberVertices);
    
                // Цикл для параметров ввода
                while (!flg)
                {
                    Console.Write("Введите количество вершин многоугольника: ");
                    numberVertices = Convert.ToInt32(Console.ReadLine());
                    if (numberVertices < 3 || numberVertices > 5)
                    {
                        Console.WriteLine("Введено неверное число вершин!");
                    }
                    else flg = true;
                }
    
                // Цикл для ввода координат каждой точки
                for (int i = 0; i < numberVertices; i++)
                {
                    Console.Write($"Введите координаты {i + 1}-й точки через пробел (например, 1 2): ");
                    string[] input = Console.ReadLine().Split();
                    if (input.Length == 2 && int.TryParse(input[0], out int pointX) && int.TryParse(input[1], out int pointY))
                    {
                        vertices.Add(new Point(pointX, pointY));  // Добавляем новую точку в список
                    }
                    else
                    {
                        Console.WriteLine("Некорректный ввод. Введите 2 целых числа через пробел.");
                        i--;  // Повторяем текущую итерацию, если ввод неверный
                    }
                }
    
                // Создаем фигуру с переменным числом точек
                Figure figure = new Figure(vertices.ToArray());
    
                // Выводим результат
                Console.WriteLine($"Фигура: {figure.Name} имеет периметр: {figure.PerimeterCalculator()}");
            }
        }
    }
    
## Тесты для задания № 3
    
    using NUnit.Framework;
    using lab01_3;
    
    namespace Lab01_cs_3rd
    {
        [Parallelizable(ParallelScope.Self)]
        [TestFixture]
        public class Tests
        {
            [Test]
            public void PointConstructor_CorrectInitialization()
            {
                int x = 3;
                int y = 4;
                Point point = new Point(x, y);
                Assert.AreEqual(x, point.X);
                Assert.AreEqual(y, point.Y);
            }
    
            [Test]
            public void FigureConstructor_ThreePoints()
            {
                Point p1 = new Point(1, 2);
                Point p2 = new Point(2, 3);
                Point p3 = new Point(3, 4);
    
                Figure triangle = new Figure(p1, p2, p3);
    
                Assert.AreEqual("Треугольник", triangle.Name);
            }
    
            [Test]
            public void FigureConstructor_FourPoints()
            {
                Point p1 = new Point(1, 2);
                Point p2 = new Point(2, 3);
                Point p3 = new Point(3, 4);
                Point p4 = new Point(4, 5);
    
                Figure quadrilateral = new Figure(p1, p2, p3, p4);
    
                Assert.AreEqual("Четырехугольник", quadrilateral.Name);
            }
    
            [Test]
            public void FigureConstructor_FivePoints()
            {
                Point p1 = new Point(1, 2);
                Point p2 = new Point(2, 3);
                Point p3 = new Point(3, 4);
                Point p4 = new Point(4, 5);
                Point p5 = new Point(5, 6);
    
                Figure pentagon = new Figure(p1, p2, p3, p4, p5);
    
                Assert.AreEqual("Пятиугольник", pentagon.Name);
            }
    
            [Test]
            public void LengthSide_CorrectDistance()
            {
                Point p1 = new Point(0, 0);
                Point p2 = new Point(1, 1);
                Point p3 = new Point(1, 0);
                Figure figure = new Figure(p1, p2, p3);
    
                double length = figure.LengthSide(p1, p2);
    
                Assert.AreEqual(Math.Sqrt(2), length, 0.001);
            }
    
            [Test]
            public void PerimeterCalculator_CorrectPerimeter()
            {
                Point p1 = new Point(0, 0);
                Point p2 = new Point(0, 4);
                Point p3 = new Point(3, 0);
                Figure triangle = new Figure(p1, p2, p3);
    
                double perimeter = triangle.PerimeterCalculator();
    
                Assert.AreEqual(12.0, perimeter, 0.001);
            }
        }
    }
    
C# lab01
