# 242. Valid Anagram

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

## Description

Diberikan dua string `s` dan `t`, tugas Anda adalah mengembalikan nilai `true` jika `t` merupakan anagram dari `s`, dan sebaliknya mengembalikan `false`.

Sebuah anagram adalah kata atau frasa yang dibentuk dengan mengatur ulang huruf-huruf dari kata atau frasa lain, umumnya dengan menggunakan seluruh huruf asli dengan jumlah yang sama.

Contoh 1:

```text
Input: s = "anagram", t = "nagaram"
Output: true
```

Contoh 2:

```text
Input: s = "rat", t = "car"
Output: false
```

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

## Approach

Berikut adalah solusi yang dapat diterapkan untuk mengecek apakah `t` adalah anagram dari `s`:

```java
public class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }

        int[] counts = new int[26];

        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        for (char ch : t.toCharArray()) {
            counts[ch - 'a']--;
            if (counts[ch - 'a'] < 0) {
                return false;
            }
        }

        return true;
    }
}
```

Berikut ini adalah langkah-langkah atau penjelasan langkah demi langkah dari pendekatan solusi tersebut:

1. Pertama, kita hitung panjang string `s` dan `t`. Jika panjang keduanya berbeda, kita langsung mengembalikan `false`, karena string dengan panjang yang berbeda tidak bisa menjadi anagram satu sama lain.
2. Kemudian, kita buat sebuah array `counts` dengan panjang 26 (sesuai jumlah huruf dalam alfabet Inggris). Setiap elemen dalam array ini akan mewakili frekuensi kemunculan karakter tertentu dalam string.
3. Selanjutnya, kita iterasi melalui setiap karakter dalam string `s`. Kita ambil nilai ASCII dari karakter tersebut dan kurangkan dengan nilai ASCII dari karakter 'a'. Ini memberikan kita indeks yang sesuai dalam array `counts` untuk merekam frekuensi kemunculan karakter tersebut.
4. Kita tambahkan 1 ke nilai `counts` pada indeks yang sesuai.
5. Setelah selesai menghitung frekuensi kemunculan semua karakter dalam string `s`, kita akan menghitung frekuensi karakter dalam string `t`.
6. Kita melakukan iterasi melalui setiap karakter dalam string `t` dan melakukan langkah-langkah yang mirip dengan langkah-langkah 3 dan 4, tetapi kita mengurangkan 1 dari nilai `counts` pada indeks yang sesuai.
7. Setelah selesai menghitung frekuensi kemunculan semua karakter dalam string `t`, kita akan memeriksa nilai dalam array `counts`. Jika semua nilai dalam array tersebut bernilai nol, artinya semua karakter dalam string `s` dan `t` muncul dengan frekuensi yang sama, sehingga `t` adalah anagram dari `s`.
8. Jika ada setidaknya satu nilai dalam array `counts` yang tidak bernilai nol, maka artinya ada karakter yang muncul lebih banyak dalam salah satu string daripada di string lainnya, sehingga `t` bukanlah anagram dari `s`.

Dengan demikian, pendekatan ini memanfaatkan array `counts` untuk melacak frekuensi kemunculan karakter dalam kedua string dan membandingkan nilai-nilai dalam array tersebut untuk menentukan apakah kedua string tersebut adalah anagram atau tidak.

## Test Scenario

Berikut beberapa skenario pengujian yang dapat digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        assertEquals(true, solution.isAnagram("anagram", "nagaram"));
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        assertEquals(false, solution.isAnagram("rat", "car"));
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(N), di mana "N" adalah panjang dari string `s` atau `t`.
- Space: O(1), karena array `counts` memiliki ukuran tetap (26) yang tidak bergantung pada panjang input.

Kompleksitas waktu untuk mengecek anagram adalah O(N), di mana "N" adalah panjang dari string `s` atau `t`. Ini karena kita hanya melalui setiap karakter dalam string sekali. Kompleksitas ruang adalah O(1) karena ukuran array `counts` tetap konstan dan tidak bergantung pada panjang input.

## Submit Solution

n/a

## Additional

n/a
