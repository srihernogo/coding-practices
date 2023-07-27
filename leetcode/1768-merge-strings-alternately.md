# 1768. Merge Strings Alternately

Level: $\color{green}{Easy}$

[https://leetcode.com/problems/merge-strings-alternately/](https://leetcode.com/problems/merge-strings-alternately/)

## Description

Dalam masalah ini, Anda diberikan dua string `word1` dan `word2`. Anda harus menggabungkan kedua string tersebut dengan menambahkan huruf-huruf secara bergantian, dimulai dari `word1`. **Jika salah satu string lebih panjang dari yang lain, Anda harus menambahkan huruf-huruf tambahan ke bagian akhir dari string hasil penggabungan.**

Tugas Anda adalah mengembalikan string hasil penggabungan tersebut.

Contoh 1:

```text
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Penjelasan: String hasil penggabungan akan bergantian menambahkan huruf-huruf dari "word1" dan "word2" sebagai berikut:
word1: a b c
word2: p q r
merged: a p b q c r
```

Contoh 2:

```text
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Penjelasan: String hasil penggabungan akan bergantian menambahkan huruf-huruf dari "word1" dan "word2" sebagai berikut:
word1: a b
word2: p q r s
merged: a p b q r s
```

Contoh 3:

```text
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Penjelasan: String hasil penggabungan akan bergantian menambahkan huruf-huruf dari "word1" dan "word2" sebagai berikut:
word1: a b c d
word2: p q
merged: a p b q c d
```

**Constraints:**

- `1 <= word1.length, word2.length <= 100`
- `word1 and word2 consist of lowercase English letters.`

```text
- Panjang "word1" dan "word2" memenuhi syarat 1 <= word1.length, word2.length <= 100.
- "word1" dan "word2" terdiri dari huruf-huruf kecil dalam bahasa Inggris.
```

## Approach

Untuk menyelesaikan masalah ini menggunakan Java, kita dapat mengimplementasikan algoritma berikut:

1. Buat kelas `Solution` dengan metode `mergeAlternately` yang akan melakukan penggabungan string "word1" dan "word2".

2. Dalam metode `mergeAlternately`, kita dapat menggunakan pendekatan sederhana dengan menggunakan dua indeks untuk masing-masing string "word1" dan "word2".

3. Inisialisasi dua variabel indeks, yaitu index1 dan index2, yang awalnya diatur ke 0. Variabel ini akan menunjukkan posisi saat ini pada masing-masing string.

4. Selama salah satu indeks masih berada dalam rentang panjang string "word1" atau "word2", kita akan bergantian menambahkan karakter dari "word1" dan "word2" ke string hasil.

5. Jika index1 kurang dari panjang "word1", tambahkan karakter dari "word1" ke string hasil dan tingkatkan index1 sebanyak 1.

6. Jika index2 kurang dari panjang "word2", tambahkan karakter dari "word2" ke string hasil dan tingkatkan index2 sebanyak 1.

7. Kembalikan string hasil setelah selesai menggabungkan kedua string.

Berikut adalah implementasi dalam Java:

```java
public class Solution {
    public String mergeAlternately(String word1, String word2) {
        StringBuilder merged = new StringBuilder();
        int index1 = 0;
        int index2 = 0;
        int length1 = word1.length();
        int length2 = word2.length();

        while (index1 < length1 || index2 < length2) {
            if (index1 < length1) {
                merged.append(word1.charAt(index1));
                index1++;
            }
            if (index2 < length2) {
                merged.append(word2.charAt(index2));
                index2++;
            }
        }

        return merged.toString();
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        System.out.println(solution.mergeAlternately("abc", "pqr")); // Output: "apbqcr"
        System.out.println(solution.mergeAlternately("ab", "pqrs")); // Output: "apbqrs"
        System.out.println(solution.mergeAlternately("abcd", "pq")); // Output: "apbqcd"
    }
}
```

Dalam contoh di atas, kita membuat kelas `Solution` dengan metode `mergeAlternately` untuk menyelesaikan masalah yang diminta. Pada metode ini, kita menggunakan StringBuilder untuk menggabungkan kedua string "word1" dan "word2" secara bergantian.

Kita dapat menguji contoh-contoh yang diberikan dalam masalah dengan menginstansiasi kelas `Solution` dan memanggil metode `mergeAlternately` dengan input yang sesuai. Metode ini akan mengembalikan string hasil penggabungan "word1" dan "word2".

## Complexity

n/a

## Solution

n/a

## Additional

n/a
