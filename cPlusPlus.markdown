# Методическое пособие по основам C++

## Введение в C++

### Что такое C++?
C++ — это компилируемый, статически типизированный язык программирования общего назначения, который:
- Поддерживает различные парадигмы программирования (процедурное, ООП, обобщенное, функциональное)
- Предоставляет низкоуровневый доступ к памяти
- Имеет богатую стандартную библиотеку
- Обеспечивает высокую производительность

### История и эволюция
- 1979: Бьёрн Страуструп начинает работу над "C with Classes"
- 1983: Язык переименован в C++
- 1998: Первый международный стандарт C++98
- 2011: C++11 — major update с множеством новых возможностей
- 2020: C++20 — современный стандарт с новыми функциями

### Области применения
- Системное программирование
- Игры и игровые движки
- Высокопроизводительные вычисления
- Встраиваемые системы
- Научные вычисления

## Настройка среды разработки

### Компиляторы
- GCC/G++ (GNU Compiler Collection)
- Clang/LLVM
- Microsoft Visual C++

### Популярные IDE
- Visual Studio
- CLion
- Code::Blocks
- Qt Creator

### Простой пример компиляции
```bash
g++ -o program program.cpp  # Компиляция
./program                   # Запуск
```

## Основы синтаксиса

### Структура программы
```cpp
// Подключение заголовочных файлов
#include <iostream>

// Пространство имен
using namespace std;

// Главная функция программы
int main() {
    // Вывод на экран
    cout << "Hello, World!" << endl;
    
    // Возврат кода успешного выполнения
    return 0;
}
```

### Переменные и типы данных

#### Основные типы данных
```cpp
// Целочисленные типы
int age = 25;           // Целое число
short smallNumber = 10; // Короткое целое
long bigNumber = 1000;  // Длинное целое

// Числа с плавающей точкой
float price = 19.99f;   // Одинарная точность
double pi = 3.14159;    // Двойная точность

// Символьный тип
char grade = 'A';       // Один символ

// Логический тип
bool isActive = true;   // true или false

// Беззнаковые типы
unsigned int positiveOnly = 42;
```

#### Автоматическое определение типа (C++11)
```cpp
auto number = 42;        // int
auto name = "John";      // const char*
auto salary = 2500.50;   // double
```

### Константы
```cpp
const int MAX_USERS = 100;          // Константа времени компиляции
constexpr double PI = 3.14159;      // Константное выражение (C++11)

// Указатели на константу
const int* ptr = &MAX_USERS;
```

### Операторы

#### Арифметические операторы
```cpp
int a = 10, b = 3;
int sum = a + b;        // 13
int diff = a - b;       // 7
int product = a * b;    // 30
int quotient = a / b;   // 3
int remainder = a % b;  // 1
```

#### Операторы сравнения
```cpp
bool isEqual = (a == b);      // false
bool notEqual = (a != b);     // true
bool greater = (a > b);       // true
bool less = (a < b);          // false
```

#### Логические операторы
```cpp
bool andResult = (true && false);  // false
bool orResult = (true || false);   // true
bool notResult = !true;            // false
```

### Управляющие конструкции

#### Условные операторы
```cpp
// if-else
int score = 85;
if (score >= 90) {
    cout << "Отлично!" << endl;
} else if (score >= 75) {
    cout << "Хорошо" << endl;
} else {
    cout << "Удовлетворительно" << endl;
}

// Тернарный оператор
string result = (score >= 60) ? "Сдал" : "Не сдал";
```

#### Циклы
```cpp
// for loop
for (int i = 0; i < 5; i++) {
    cout << i << " ";
}
// Output: 0 1 2 3 4

// while loop
int count = 0;
while (count < 3) {
    cout << count << " ";
    count++;
}
// Output: 0 1 2

// do-while loop
int num = 5;
do {
    cout << num << " ";
    num--;
} while (num > 0);
// Output: 5 4 3 2 1

// Range-based for (C++11)
int numbers[] = {1, 2, 3, 4, 5};
for (int n : numbers) {
    cout << n << " ";
}
// Output: 1 2 3 4 5
```

### Функции

#### Объявление и определение функций
```cpp
// Прототип функции (объявление)
int add(int a, int b);

// Главная функция
int main() {
    int result = add(5, 3);  // Вызов функции
    cout << "Sum: " << result << endl;
    return 0;
}

// Определение функции
int add(int a, int b) {
    return a + b;
}
```

#### Перегрузка функций
```cpp
// Функции с одинаковым именем, но разными параметрами
int multiply(int a, int b) {
    return a * b;
}

double multiply(double a, double b) {
    return a * b;
}

// Вызов
int intResult = multiply(2, 3);       // 6
double doubleResult = multiply(2.5, 4.0); // 10.0
```

#### Параметры по умолчанию
```cpp
void printMessage(string message = "Hello", int times = 1) {
    for (int i = 0; i < times; i++) {
        cout << message << endl;
    }
}

// Вызовы
printMessage();                 // "Hello" 1 раз
printMessage("Hi");            // "Hi" 1 раз
printMessage("Welcome", 3);    // "Welcome" 3 раза
```

## Работа с памятью и указатели

### Указатели
```cpp
int number = 42;
int* ptr = &number;  // ptr содержит адрес number

cout << number << endl;   // 42
cout << *ptr << endl;     // 42 (разыменование)
cout << ptr << endl;      // адрес памяти

*ptr = 100;               // Изменение значения через указатель
cout << number << endl;   // 100
```

### Ссылки
```cpp
int value = 50;
int& ref = value;        // ref - ссылка на value

cout << value << endl;   // 50
cout << ref << endl;     // 50

ref = 75;                // Изменение через ссылку
cout << value << endl;   // 75
```

### Динамическая память
```cpp
// Выделение памяти
int* dynamicInt = new int(42);
int* array = new int[10];

// Использование
*dynamicInt = 100;
array[0] = 1;
array[1] = 2;

// Освобождение памяти
delete dynamicInt;
delete[] array;
```

### Умные указатели (C++11)
```cpp
#include <memory>

// unique_ptr - эксклюзивное владение
unique_ptr<int> uptr = make_unique<int>(42);

// shared_ptr - разделяемое владение
shared_ptr<int> sptr1 = make_shared<int>(100);
shared_ptr<int> sptr2 = sptr1;  // Оба указывают на один объект

// weak_ptr - слабая ссылка (не увеличивает счетчик ссылок)
weak_ptr<int> wptr = sptr1;
```

## Стандартная библиотека

### Ввод-вывод
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string name;
    int age;
    
    cout << "Введите имя: ";
    getline(cin, name);
    
    cout << "Введите возраст: ";
    cin >> age;
    
    cout << "Привет, " << name << "! Тебе " << age << " лет." << endl;
    
    return 0;
}
```

### Работа со строками
```cpp
#include <string>

string greeting = "Hello";
string name = "World";

// Конкатенация
string message = greeting + " " + name + "!";

// Методы строк
int length = message.length();          // Длина строки
string sub = message.substr(0, 5);      // Подстрока
size_t pos = message.find("World");     // Поиск подстроки

// Преобразования
int number = stoi("123");              // Строка в int
double value = stod("3.14");           // Строка в double
string strNum = to_string(42);         // Число в строку
```

### Контейнеры STL

#### Вектор (динамический массив)
```cpp
#include <vector>

vector<int> numbers = {1, 2, 3, 4, 5};

// Добавление элементов
numbers.push_back(6);
numbers.insert(numbers.begin(), 0);

// Доступ к элементам
int first = numbers[0];         // Быстрый доступ
int second = numbers.at(1);     // С проверкой границ

// Итерация
for (int num : numbers) {
    cout << num << " ";
}

// Размер и емкость
cout << "Size: " << numbers.size() << endl;
cout << "Capacity: " << numbers.capacity() << endl;
```

#### Другие контейнеры
```cpp
#include <array>
#include <list>
#include <map>
#include <set>
#include <unordered_map>

// Статический массив
array<int, 5> fixedArray = {1, 2, 3, 4, 5};

// Двусвязный список
list<string> names = {"Alice", "Bob", "Charlie"};

// Ассоциативный массив (сортированный)
map<string, int> ages = {{"Alice", 25}, {"Bob", 30}};

// Множество
set<int> uniqueNumbers = {1, 2, 3, 2, 1}; // {1, 2, 3}

// Хеш-таблица
unordered_map<string, double> prices = {{"apple", 1.2}, {"banana", 0.8}};
```

### Алгоритмы STL
```cpp
#include <algorithm>
#include <vector>

vector<int> numbers = {5, 2, 8, 1, 9};

// Сортировка
sort(numbers.begin(), numbers.end());

// Поиск
auto it = find(numbers.begin(), numbers.end(), 8);
if (it != numbers.end()) {
    cout << "Found: " << *it << endl;
}

// Преобразование
for_each(numbers.begin(), numbers.end(), [](int n) {
    cout << n * 2 << " ";
});

// Подсчет
int countFives = count(numbers.begin(), numbers.end(), 5);
```

## Объектно-ориентированное программирование

### Классы и объекты
```cpp
class Person {
private:
    string name;
    int age;
    
public:
    // Конструктор
    Person(string n, int a) : name(n), age(a) {}
    
    // Методы
    void introduce() {
        cout << "Меня зовут " << name << ", мне " << age << " лет." << endl;
    }
    
    // Геттеры и сеттеры
    string getName() const { return name; }
    void setAge(int a) { age = a; }
};

// Использование
Person alice("Alice", 25);
alice.introduce();
```

### Наследование
```cpp
class Student : public Person {
private:
    string major;
    
public:
    Student(string n, int a, string m) : Person(n, a), major(m) {}
    
    void study() {
        cout << getName() << " изучает " << major << endl;
    }
};

Student bob("Bob", 20, "Computer Science");
bob.introduce();
bob.study();
```

### Полиморфизм
```cpp
class Animal {
public:
    virtual void makeSound() {
        cout << "Some animal sound" << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Woof!" << endl;
    }
};

class Cat : public Animal {
public:
    void makeSound() override {
        cout << "Meow!" << endl;
    }
};

// Использование полиморфизма
Animal* animals[] = {new Dog(), new Cat()};
for (Animal* animal : animals) {
    animal->makeSound();  // Вызовется правильная версия метода
}
```

## Обработка исключений

### Базовый синтаксис
```cpp
#include <stdexcept>
#include <iostream>

double divide(double a, double b) {
    if (b == 0) {
        throw runtime_error("Division by zero!");
    }
    return a / b;
}

int main() {
    try {
        double result = divide(10, 0);
        cout << "Result: " << result << endl;
    }
    catch (const runtime_error& e) {
        cerr << "Error: " << e.what() << endl;
    }
    catch (...) {
        cerr << "Unknown error occurred" << endl;
    }
    
    return 0;
}
```

### Пользовательские исключения
```cpp
class MyException : public exception {
private:
    string message;
    
public:
    MyException(const string& msg) : message(msg) {}
    
    const char* what() const noexcept override {
        return message.c_str();
    }
};

void testFunction() {
    throw MyException("Custom error message");
}
```

## Современный C++ (C++11 и новее)

### Auto и decltype
```cpp
auto x = 5;                 // int
auto y = 3.14;              // double
auto name = "John";         // const char*

vector<int> numbers = {1, 2, 3};
for (auto num : numbers) {  // int
    cout << num << " ";
}

decltype(x) z = x + 1;      // Тип z такой же как у x (int)
```

### Лямбда-выражения
```cpp
// Простая лямбда
auto greet = []() {
    cout << "Hello!" << endl;
};
greet();

// Лямбда с параметрами
auto add = [](int a, int b) {
    return a + b;
};
cout << add(5, 3) << endl;  // 8

// Захват переменных
int multiplier = 2;
auto times = [multiplier](int x) {
    return x * multiplier;
};
cout << times(5) << endl;   // 10
```

### Шаблоны
```cpp
// Шаблон функции
template <typename T>
T max(T a, T b) {
    return (a > b) ? a : b;
}

// Использование
cout << max(5, 10) << endl;        // 10
cout << max(3.14, 2.71) << endl;   // 3.14

// Шаблон класса
template <typename T>
class Box {
private:
    T content;
    
public:
    Box(T c) : content(c) {}
    T getContent() { return content; }
};

// Использование
Box<int> intBox(42);
Box<string> stringBox("Hello");
```

## Практические примеры

### Пример 1: Калькулятор
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

double calculate(double a, double b, char op) {
    switch (op) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': 
            if (b == 0) throw runtime_error("Division by zero!");
            return a / b;
        default: throw runtime_error("Invalid operator!");
    }
}

int main() {
    try {
        double num1, num2;
        char op;
        
        cout << "Введите первое число: ";
        cin >> num1;
        
        cout << "Введите оператор (+, -, *, /): ";
        cin >> op;
        
        cout << "Введите второе число: ";
        cin >> num2;
        
        double result = calculate(num1, num2, op);
        cout << "Результат: " << result << endl;
    }
    catch (const exception& e) {
        cerr << "Ошибка: " << e.what() << endl;
    }
    
    return 0;
}
```

### Пример 2: Управление списком задач
```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

using namespace std;

class Task {
private:
    string description;
    bool completed;
    
public:
    Task(string desc) : description(desc), completed(false) {}
    
    void complete() { completed = true; }
    bool isCompleted() const { return completed; }
    string getDescription() const { return description; }
};

class TaskManager {
private:
    vector<Task> tasks;
    
public:
    void addTask(const string& description) {
        tasks.emplace_back(description);
        cout << "Задача добавлена: " << description << endl;
    }
    
    void completeTask(int index) {
        if (index >= 0 && index < tasks.size()) {
            tasks[index].complete();
            cout << "Задача выполнена: " << tasks[index].getDescription() << endl;
        }
    }
    
    void showTasks() const {
        cout << "\nСписок задач:" << endl;
        for (size_t i = 0; i < tasks.size(); i++) {
            string status = tasks[i].isCompleted() ? "[X]" : "[ ]";
            cout << i + 1 << ". " << status << " " << tasks[i].getDescription() << endl;
        }
    }
};

int main() {
    TaskManager manager;
    
    manager.addTask("Изучить основы C++");
    manager.addTask("Написать первую программу");
    manager.addTask("Изучить ООП в C++");
    
    manager.showTasks();
    
    manager.completeTask(0);
    manager.completeTask(2);
    
    manager.showTasks();
    
    return 0;
}
```

## Заключение и дальнейшие шаги

### Рекомендуемые ресурсы
1. **Книги**:
   - "Язык программирования C++" - Бьёрн Страуструп
   - "Эффективный и современный C++" - Скотт Мейерс
   - "C++ Primer" - Стэнли Липпман

2. **Онлайн-ресурсы**:
   - cppreference.com
   - learncpp.com
   - C++ Core Guidelines

3. **Практика**:
   - LeetCode
   - HackerRank
   - Собственные проекты
