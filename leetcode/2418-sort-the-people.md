# 2418. Sort the People

## Description

[https://leetcode.com/problems/sort-the-people/](https://leetcode.com/problems/sort-the-people/)

Masalah ini mengharuskan kita untuk mengurutkan sebuah array nama orang (dalam urutan menurun) berdasarkan tinggi badan orang tersebut. Kita diberikan dua array, yaitu array "names" yang berisi nama-nama orang dan array "heights" yang berisi tinggi badan setiap orang.
Kedua array ini memiliki panjang yang sama, dan elemen-elemen di dalamnya berhubungan satu sama lain berdasarkan indeks.

**Contoh:**

```text
Misalkan kita memiliki input berikut:
names = ["John", "Jane", "Mike", "Emily"]
heights = [175, 163, 180, 155]
```

Kita harus mengurutkan array "names" berdasarkan tinggi badan dari yang tertinggi ke yang terendah. Jadi hasil yang diharapkan adalah:
["Mike", "John", "Jane", "Emily"]

## Approach

Proses penyelesaian masalah dapat dilakukan dengan langkah-langkah berikut:

1. Menggabungkan dua array "names" dan "heights" sehingga setiap elemen dari "names" berhubungan dengan elemen yang sesuai dalam "heights" berdasarkan indeks.

2. Mengurutkan array "names" berdasarkan "heights" dalam urutan menurun.
   Artinya, orang dengan tinggi badan tertinggi akan berada di awal array, dan yang paling pendek akan berada di akhir array.

3. Kembalikan array "names" yang sudah diurutkan sebagai output dari masalah ini.

Dalam contoh di atas, proses penyelesaiannya adalah sebagai berikut:

```text
["John", "Jane", "Mike", "Emily"] -> Menggabungkan array "names"
[("John", 175), ("Jane", 163), ("Mike", 180), ("Emily", 155)] -> Menggabungkan dengan array "heights"
[("Mike", 180), ("John", 175), ("Jane", 163), ("Emily", 155)] -> Mengurutkan berdasarkan "heights" dalam urutan menurun
["Mike", "John", "Jane", "Emily"] -> Output akhir setelah diurutkan
```

## Complexity

n/a

## Solution

n/a
