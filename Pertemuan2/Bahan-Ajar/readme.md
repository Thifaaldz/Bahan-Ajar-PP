# PERTEMUAN 2: DART FUNDAMENTALS
## DASAR-DASAR PEMROGRAMAN DART

---

## 📋 DAFTAR ISI
- Membuat Project Dart
- Getting Started with Dart
- Variables & Constants
- Basic Types
- Control Flow
- Collections
- Functions
- Latihan Praktikum
- Troubleshooting

---

# 🚀 MEMBUAT PROJECT DART

Sebelum memulai belajar Dart, pastikan Dart SDK sudah terinstall.

---

## ✅ Metode 1: Membuat Project Secara Manual

### 1. Buat Folder Project
```bash
mkdir belajar_dart
cd belajar_dart
```

### 2. Buat File Dart
Buat file bernama `main.dart`

### 3. Tulis Kode
```dart
void main() {
  print('Hello, Selamat Belajar Dart!');
  print('Ini adalah project Dart pertama saya');
}
```

### 4. Jalankan Program
```bash
dart main.dart
```

Output:
```
Hello, Selamat Belajar Dart!
Ini adalah project Dart pertama saya
```

---

## ✅ Metode 2: Menggunakan dart create

### 1. Buat Project
```bash
dart create -t console belajar_dart_lengkap
cd belajar_dart_lengkap
```

### 2. Struktur Folder
```
belajar_dart_lengkap/
├── bin/
├── lib/
├── test/
├── pubspec.yaml
└── README.md
```

### 3. Jalankan Project
```bash
dart run
```

---

# 🎯 GETTING STARTED WITH DART

## Hello World
```dart
void main() {
  print('Hello, World!');
}
```

Penjelasan:
- `main()` adalah entry point
- `print()` untuk output
- Setiap statement diakhiri `;`

---

# 📦 VARIABLES & CONSTANTS

## Variabel dengan Tipe
```dart
String nama = 'John Doe';
int umur = 25;
double tinggi = 175.5;
bool isMenikah = false;
```

## Menggunakan var
```dart
var nama = 'John';
var umur = 25;
```

## dynamic
```dart
dynamic data = 'Hello';
data = 123;
data = true;
```

## final
```dart
final waktu = DateTime.now();
```

## const
```dart
const pi = 3.14159;
```

---

# 📊 BASIC TYPES

## String
```dart
String nama = 'John';
String alamat = '''
Jl. Sudirman
Jakarta
''';

String fullName = '$nama Doe';
```

## int
```dart
int a = 10;
int b = 3;

print(a + b);
print(a ~/ b);
print(a % b);
```

## double
```dart
double nilai = 3.14159;
print(nilai.toStringAsFixed(2));
```

## bool
```dart
bool isActive = true;
print(isActive && false);
```

---

# 🔄 CONTROL FLOW

## If Else
```dart
int nilai = 85;

if (nilai >= 75) {
  print('Lulus');
} else {
  print('Tidak Lulus');
}
```

## Switch
```dart
String grade = 'B';

switch (grade) {
  case 'A':
    print('Excellent');
    break;
  case 'B':
    print('Good');
    break;
  default:
    print('Invalid');
}
```

## For Loop
```dart
for (int i = 0; i < 5; i++) {
  print(i);
}
```

## While Loop
```dart
int i = 0;
while (i < 5) {
  print(i);
  i++;
}
```

---

# 📚 COLLECTIONS

## List
```dart
List<String> buah = ['Apel', 'Mangga', 'Jeruk'];
buah.add('Pisang');

for (var item in buah) {
  print(item);
}
```

## Set
```dart
Set<int> angka = {1, 2, 3};
angka.add(4);
```

## Map
```dart
Map<String, int> umur = {
  'John': 25,
  'Jane': 30,
};

print(umur['John']);
```

---

# 🔧 FUNCTIONS

## Fungsi Dasar
```dart
int tambah(int a, int b) {
  return a + b;
}
```

## Arrow Function
```dart
int kali(int a, int b) => a * b;
```

## Parameter Optional
```dart
void sapa(String nama, [String sapaan = 'Halo']) {
  print('$sapaan, $nama');
}
```

---

# 💻 LATIHAN PRAKTIKUM

1. Buat project `praktikum_dart`
2. Buat program data diri (String, int, double, bool)
3. Buat kalkulator sederhana
4. Program penentuan grade
5. Daftar belanja dengan List & Map
6. Challenge: Todo List CLI

---

# 🔍 TROUBLESHOOTING

| Error | Penyebab | Solusi |
|--------|----------|--------|
| dart: command not found | SDK belum terinstall | Install Dart SDK |
| Undefined name | Variabel belum dibuat | Deklarasikan variabel |

---

## Perintah Penting
```bash
dart --version
dart create nama_project
dart run
dart pub get
dart format .
```

---

# 🎉 Selamat Belajar!

Dengan menguasai dasar Dart, Anda siap melanjutkan ke Flutter 🚀
