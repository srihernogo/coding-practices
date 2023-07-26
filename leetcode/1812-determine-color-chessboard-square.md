# 1812. Determine Color of a Chessboard Square

Level: $\color{green}{Easy}$

[https://leetcode.com/problems/determine-color-of-a-chessboard-square/](https://leetcode.com/problems/determine-color-of-a-chessboard-square/)

## Description

Dalam masalah ini, Anda diberikan sebuah string bernama `coordinates` yang mewakili koordinat dari sebuah kotak pada papan catur (chessboard). Papan catur adalah sebuah kotak 8x8 yang terdiri dari kotak-kotak berwarna hitam dan putih.

Koordinat pada papan catur terdiri dari dua karakter. Karakter pertama adalah huruf dari `a` hingga `h` yang mewakili kolom pada papan catur, dan karakter kedua adalah angka dari `1` hingga `8` yang mewakili baris pada papan catur.

Tugas Anda adalah mengembalikan nilai boolean true jika kotak dengan koordinat yang diberikan berwarna putih, dan false jika kotak berwarna hitam.

Contoh 1:

```text
Input: coordinates = "a1"
Output: false
Penjelasan: Dari papan catur di atas, kotak dengan koordinat "a1" berwarna hitam, sehingga kembalikan false.
```

Contoh 2:

```text
Input: coordinates = "h3"
Output: true
Penjelasan: Dari papan catur di atas, kotak dengan koordinat "h3" berwarna putih, sehingga kembalikan true.
```

Contoh 3:

```text
Input: coordinates = "c7"
Output: false
Penjelasan: Dari papan catur di atas, kotak dengan koordinat "c7" berwarna hitam, sehingga kembalikan false.
```

**Constraints:**

- `coordinates.length == 2`
- `'a' <= coordinates[0] <= 'h'`
- `'1' <= coordinates[1] <= '8'`

```text
Panjang "coordinates" selalu 2 karakter.
Karakter pertama dari "coordinates" adalah huruf dari 'a' hingga 'h'.
Karakter kedua dari "coordinates" adalah angka dari '1' hingga '8'.
Koordinat yang diberikan selalu mewakili sebuah kotak yang valid pada papan catur.
```

## Approach

Untuk menyelesaikan masalah ini menggunakan Java, kita dapat mengimplementasikan algoritma berikut:

1. Buat kelas Solution dengan metode `isWhiteSquare` yang akan menentukan apakah kotak dengan koordinat yang diberikan berwarna putih atau hitam.

2. Dalam metode `isWhiteSquare`, kita dapat menggunakan konsep dari papan catur yang berwarna bergantian. Jika kita perhatikan, pada papan catur standar, kotak dengan koordinat (baris, kolom) akan berwarna putih jika dan hanya jika jumlah baris dan kolom tersebut ganjil atau genap. Jadi, kita hanya perlu memeriksa apakah baris dan kolom dari koordinat yang diberikan semuanya ganjil atau semuanya genap.

3. Ambil karakter pertama dari "coordinates" untuk mendapatkan kolom (dalam bentuk huruf) dan karakter kedua untuk mendapatkan baris (dalam bentuk angka).

4. Konversi karakter huruf menjadi indeks kolom (0 - 7) dengan mengurangi karakter 'a' dari karakter huruf yang diberikan.

5. Konversi karakter angka menjadi indeks baris (0 - 7) dengan mengurangi karakter '1' dari karakter angka yang diberikan.

6. Periksa apakah baris dan kolom yang dihasilkan semuanya ganjil atau semuanya genap. Jika ya, maka kotak berwarna putih, sehingga kembalikan true. Jika tidak, maka kotak berwarna hitam, sehingga kembalikan false.

Berikut adalah implementasi dalam Java:

```java
public class Solution {
    public boolean isWhiteSquare(String coordinates) {
        char colChar = coordinates.charAt(0);
        char rowChar = coordinates.charAt(1);

        // Konversi karakter huruf menjadi indeks kolom (0 - 7)
        int col = colChar - 'a';
        // Konversi karakter angka menjadi indeks baris (0 - 7)
        int row = rowChar - '1';

        // Periksa apakah baris dan kolom semuanya ganjil atau semuanya genap
        return (row % 2 == 0 && col % 2 == 0) || (row % 2 != 0 && col % 2 != 0);
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        System.out.println(solution.isWhiteSquare("a1")); // Output: false
        System.out.println(solution.isWhiteSquare("h3")); // Output: true
        System.out.println(solution.isWhiteSquare("c7")); // Output: false
    }
}
```

Dalam contoh di atas, kita membuat kelas `Solution` dengan metode `isWhiteSquare` untuk menyelesaikan masalah yang diminta. Pada metode ini, kita mengambil karakter huruf dan angka dari "coordinates", dan kemudian melakukan konversi untuk mendapatkan indeks baris dan kolom.

Kita dapat menguji contoh-contoh yang diberikan dalam masalah dengan menginstansiasi kelas `Solution` dan memanggil metode `isWhiteSquare` dengan input yang sesuai. Metode ini akan mengembalikan nilai boolean true jika kotak berwarna putih dan false jika kotak berwarna hitam.

## Complexity

n/a

## Solution

n/a

## Additional

n/a
