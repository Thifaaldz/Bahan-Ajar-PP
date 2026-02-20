# README.md - PERTEMUAN 3: DART OOP LANJUTAN

## PEMROGRAMAN BERORIENTASI OBJEK DAN FITUR LANJUTAN DART

---

## 📋 DAFTAR ISI
- [CLASSES & OBJECTS](#-classes--objects)
- [INHERITANCE](#-inheritance)
- [ABSTRACT CLASS & INTERFACE](#-abstract-class--interface)
- [MIXIN](#-mixin)
- [NULL SAFETY](#-null-safety)
- [ADVANCED CONCEPTS](#-advanced-concepts)
- [EXCEPTIONS](#-exceptions)
- [ITERABLES & FUNCTIONAL PROGRAMMING](#-iterables--functional-programming)
- [ASYNCHRONOUS PROGRAMMING](#-asynchronous-programming)
- [LIBRARIES & PACKAGES](#-libraries--packages)
- [LATIHAN PRAKTIKUM](#-latihan-praktikum)
- [TROUBLESHOOTING](#-troubleshooting)

---

## 🎯 CLASSES & OBJECTS

### **Definisi Class dan Pembuatan Object**

**Pengertian:** Class adalah blueprint atau cetakan untuk membuat object. Class mendefinisikan properti (data) dan method (perilaku) yang akan dimiliki oleh object. Object adalah instance konkret dari class yang memiliki nilai properti yang spesifik.

```dart
// Definisi class - blueprint untuk membuat object
class Person {
  // Properti/fields - data yang dimiliki object
  String name = '';
  int age = 0;
  
  // Method - perilaku yang bisa dilakukan object
  void introduce() {
    print('Hi, I am $name, $age years old');
  }
}

// Membuat object - instance dari class Person
void main() {
  // Membuat object person1
  var person1 = Person();
  person1.name = 'John';  // Mengisi properti
  person1.age = 25;
  person1.introduce();     // Memanggil method
  
  // Membuat object person2
  var person2 = Person();
  person2.name = 'Jane';
  person2.age = 30;
  person2.introduce();
  
  // Cascade notation (..) - memanggil multiple method pada object yang sama
  var person3 = Person()
    ..name = 'Bob'
    ..age = 35
    ..introduce();
}
```

### **Keyword this**

**Pengertian:** Keyword `this` merujuk pada instance object saat ini. Digunakan untuk membedakan antara parameter constructor dengan properti class yang memiliki nama sama, atau untuk merujuk ke object itu sendiri dalam method.

```dart
class Person {
  String name;
  int age;
  
  // Constructor dengan parameter nama yang sama dengan properti
  Person(String name, int age) {
    // this.name merujuk ke properti class
    // name (tanpa this) merujuk ke parameter
    this.name = name;
    this.age = age;
  }
  
  // Constructor dengan parameter (shortcut - this implisit)
  // Person(this.name, this.age); // Cara singkat
  
  void introduce() {
    // this bisa digunakan meskipun tidak ambigu
    print('Hi, I am ${this.name}, ${this.age} years old');
  }
  
  void compareAge(Person other) {
    // this merujuk ke object saat ini
    // other adalah object lain
    if (this.age > other.age) {
      print('${this.name} lebih tua dari ${other.name}');
    } else if (this.age < other.age) {
      print('${this.name} lebih muda dari ${other.name}');
    } else {
      print('${this.name} sama umur dengan ${other.name}');
    }
  }
}

void main() {
  var person1 = Person('John', 25);
  var person2 = Person('Jane', 30);
  
  person1.compareAge(person2);
}
```

### **Constructor**

**Pengertian:** Constructor adalah method khusus yang dipanggil secara otomatis saat object dibuat. Constructor digunakan untuk menginisialisasi properti object. Dart memiliki beberapa jenis constructor.

#### Default Constructor
```dart
class Person {
  String name;
  int age;
  
  // Default constructor - dipanggil saat object dibuat
  // Jika tidak didefinisikan, Dart akan membuat default constructor tanpa parameter
  Person(String name, int age) {
    this.name = name;
    this.age = age;
    print('Constructor dipanggil untuk $name');
  }
  
  // Constructor dengan parameter (shortcut)
  // Person(this.name, this.age); // Cara singkat dan lebih umum
}

void main() {
  var person = Person('John', 25); // Constructor otomatis dipanggil
}
```

#### Named Constructor
**Pengertian:** Named constructor adalah constructor yang memiliki nama spesifik, digunakan untuk memberikan cara berbeda dalam membuat object.

```dart
class Person {
  String name;
  int age;
  String? email;
  
  // Main constructor
  Person(this.name, this.age);
  
  // Named constructor - untuk membuat object dengan default values
  Person.guest() {
    name = 'Guest';
    age = 0;
    print('Guest account created');
  }
  
  // Named constructor dengan parameter
  Person.withEmail(this.name, this.age, this.email);
  
  // Named constructor untuk data dari JSON
  Person.fromJson(Map<String, dynamic> json) {
    name = json['name'];
    age = json['age'];
    email = json['email'];
  }
  
  // Redirecting constructor - memanggil constructor lain
  Person.anonymous() : this('Anonymous', 0);
  
  void introduce() {
    print('Name: $name, Age: $age, Email: $email');
  }
}

void main() {
  var p1 = Person('John', 25);
  var p2 = Person.guest();
  var p3 = Person.withEmail('Jane', 30, 'jane@email.com');
  
  var jsonData = {'name': 'Bob', 'age': 35, 'email': 'bob@email.com'};
  var p4 = Person.fromJson(jsonData);
  var p5 = Person.anonymous();
  
  p1.introduce();
  p2.introduce();
  p3.introduce();
  p4.introduce();
  p5.introduce();
}
```

---

---

## 🔄 INHERITANCE

### **Pengertian Inheritance**
Inheritance (pewarisan) adalah konsep OOP di mana sebuah class dapat mewarisi properti dan method dari class lain. Class yang mewarisi disebut **subclass/child class**, dan class yang diwarisi disebut **superclass/parent class**.

```dart
// Parent class
class Animal {
  String name;
  
  Animal(this.name);
  
  void eat() {
    print('$name sedang makan');
  }
  
  void sleep() {
    print('$name sedang tidur');
  }
}

// Child class
class Dog extends Animal {
  Dog(String name) : super(name); // Memanggil constructor parent
  
  void bark() {
    print('$name menggonggong');
  }
}

void main() {
  var dog = Dog('Buddy');
  
  dog.eat();   // Dari parent
  dog.sleep(); // Dari parent
  dog.bark();  // Dari child
}
```

---

### **super Keyword & Override**

**Pengertian:**  
- `super` digunakan untuk mengakses method atau constructor dari parent class.  
- `@override` digunakan untuk menandakan bahwa method tersebut menimpa (override) method dari parent class.

```dart
class Vehicle {
  void start() {
    print('Vehicle started');
  }
}

class Car extends Vehicle {
  @override
  void start() {
    super.start(); // Memanggil method parent
    print('Car engine running');
  }
}

void main() {
  var car = Car();
  car.start();
}
```

---

## 📐 ABSTRACT CLASS & INTERFACE

### **Abstract Class**

**Pengertian:**  
Abstract class adalah class yang tidak bisa dibuat object-nya secara langsung. Biasanya digunakan sebagai blueprint untuk subclass.

```dart
abstract class Animal {
  String name;
  
  Animal(this.name);
  
  void makeSound(); // Abstract method (tanpa body)
  
  void sleep() {
    print('$name tidur');
  }
}

class Dog extends Animal {
  Dog(String name) : super(name);
  
  @override
  void makeSound() {
    print('Woof!');
  }
}

void main() {
  var dog = Dog('Buddy');
  dog.makeSound();
  dog.sleep();
}
```

---

### **Implements (Interface)**

Di Dart, semua class bisa menjadi interface menggunakan `implements`.

```dart
class Flyable {
  void fly() {}
}

class Bird implements Flyable {
  @override
  void fly() {
    print('Bird flying');
  }
}
```

Perbedaan:
- `extends` → mewarisi implementasi.
- `implements` → tidak mewarisi implementasi, wajib override semua method.

---

## 🧩 MIXIN

**Pengertian:**  
Mixin memungkinkan kita menggunakan kembali kode dari beberapa class tanpa menggunakan inheritance langsung.

```dart
mixin CanRun {
  void run() {
    print('Running...');
  }
}

mixin CanSwim {
  void swim() {
    print('Swimming...');
  }
}

class Athlete with CanRun {}

class Duck with CanRun, CanSwim {}

void main() {
  var athlete = Athlete();
  athlete.run();
  
  var duck = Duck();
  duck.run();
  duck.swim();
}
```

---

## 🔒 NULL SAFETY

Dart mendukung null safety untuk mencegah error null.

```dart
String? name; // Bisa null

void main() {
  name = 'John';
  
  print(name?.length); // Safe access
  
  String username = name ?? 'Guest'; // Default value
  print(username);
}
```

---

## 🚀 ADVANCED CONCEPTS

### Late Keyword

Digunakan untuk menunda inisialisasi variabel non-nullable.

```dart
late String description;

void main() {
  description = 'Belajar Dart OOP';
  print(description);
}
```

---

## ⚠ EXCEPTIONS

```dart
void main() {
  try {
    int result = 10 ~/ 0;
    print(result);
  } catch (e) {
    print('Terjadi error: $e');
  } finally {
    print('Program selesai');
  }
}
```

Custom Exception:

```dart
class NegativeValueException implements Exception {
  String message;
  NegativeValueException(this.message);
}

void checkValue(int value) {
  if (value < 0) {
    throw NegativeValueException('Nilai tidak boleh negatif');
  }
}
```

---

## 🔁 ITERABLES & FUNCTIONAL PROGRAMMING

```dart
void main() {
  var numbers = [1, 2, 3, 4, 5];
  
  var evenNumbers = numbers.where((n) => n % 2 == 0);
  var squared = numbers.map((n) => n * n);
  var total = numbers.reduce((a, b) => a + b);
  
  print(evenNumbers);
  print(squared);
  print(total);
}
```

---

## ⏳ ASYNCHRONOUS PROGRAMMING

### Future & async/await

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Data Loaded';
}

void main() async {
  print('Loading...');
  var data = await fetchData();
  print(data);
}
```

---

## 📦 LIBRARIES & PACKAGES

Import library bawaan:

```dart
import 'dart:math';
```

Import file sendiri:

```dart
import 'utils.dart';
```

---

## 💻 LATIHAN PRAKTIKUM

1. Buat class `Mahasiswa` dengan constructor dan method `tampilData()`.
2. Buat class `Kendaraan` lalu turunkan menjadi `Mobil` dan `Motor`.
3. Buat abstract class `BangunDatar` lalu implementasikan `Persegi` dan `Lingkaran`.
4. Buat contoh penggunaan mixin.
5. Buat program async sederhana menggunakan Future.

---

## 🔍 TROUBLESHOOTING

| Error | Penyebab | Solusi |
|-------|----------|--------|
| Missing override | Method belum diimplementasikan | Tambahkan @override |
| Null check operator used on null | Variabel null dipaksa | Gunakan ? atau validasi null |
| The method isn't defined | Salah penulisan method | Periksa kembali nama method |

---

# 🎉 SELESAI

Dengan memahami OOP lanjutan ini, Anda siap membangun arsitektur aplikasi yang lebih kompleks menggunakan Dart dan Flutter 🚀
