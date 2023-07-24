# 1814. Count Nice Pairs in an Array

Level: $\color{orange}{Medium}$

[https://leetcode.com/problems/count-nice-pairs-in-an-array/](https://leetcode.com/problems/count-nice-pairs-in-an-array/)

## Description

Masalah ini melibatkan pemeriksaan pasangan indeks dalam array `nums` yang memenuhi syarat tertentu.
Dalam soal ini, kita diberikan sebuah array `nums` yang terdiri dari bilangan bulat non-negatif.
Kemudian, kita diberikan fungsi `rev(x)` yang mengembalikan bilangan bulat `x` yang dibalik,
artinya, angka-angka pada bilangan tersebut dibalik urutannya.

Misalnya, `rev(123)` akan menghasilkan `321`,
dan `rev(120)` akan menghasilkan `21`.

Pasangan indeks (i, j) dianggap `nice` jika memenuhi kondisi berikut:

- `0 <= i < j < nums.length`
- `nums[i] + rev(nums[j]) == nums[j] + rev(nums[i])`

  Artinya, jumlah dari elemen nums[i] dan angka yang dibalik dari nums[j] harus sama dengan jumlah dari elemen nums[j] dan angka yang dibalik dari nums[i].

Tugas kita adalah menghitung berapa banyak pasangan indeks yang `nice` ada dalam array `nums`.
Karena jumlah tersebut dapat terlalu besar, kita diminta untuk mengembalikan hasil modulo `10^9 + 7`.

Contoh 1:

```text
Input: nums = [42, 11, 1, 97]
Output: 2
Penjelasan: Terdapat dua pasangan indeks yang memenuhi syarat "nice":
```

- `(0, 3): 42 + rev(97) = 42 + 79 = 121, 97 + rev(42) = 97 + 24 = 121.`
- `(1, 2): 11 + rev(1) = 11 + 1 = 12, 1 + rev(11) = 1 + 11 = 12.`

Contoh 2:

```text
Input: nums = [13, 10, 35, 24, 76]
Output: 4
Penjelasan: Terdapat empat pasangan indeks yang memenuhi syarat "nice":
```

- `(0, 4): 13 + rev(76) = 13 + 67 = 80, 76 + rev(13) = 76 + 31 = 107.`
- `(0, 3): 13 + rev(24) = 13 + 42 = 55, 24 + rev(13) = 24 + 31 = 55.`
- `(1, 2): 10 + rev(35) = 10 + 53 = 63, 35 + rev(10) = 35 + 1 = 36.`
- `(2, 4): 35 + rev(76) = 35 + 67 = 102, 76 + rev(35) = 76 + 53 = 129.`

**Constraints:**

- `1 <= nums.length <= 105`

  Panjang array `nums` (nums.length) memenuhi syarat 1 <= nums.length <= 10^5.

- `0 <= nums[i] <= 109`

  Setiap elemen dalam `nums` memenuhi syarat 0 <= nums[i] <= 10^9.

## Approach

**Untuk menyelesaikan masalah ini menggunakan Java, kita dapat mengimplementasikan algoritma berikut:**

1. Buat fungsi yang akan menghitung jumlah pasangan indeks yang memenuhi syarat `nice`. Kita dapat menyebut fungsi ini `countNicePairs`.

2. Dalam fungsi `countNicePairs`, kita akan menggunakan HashMap untuk menghitung berapa kali suatu nilai dalam array `nums` berpasangan dengan nilai hasil pembalikan (reverse) dari angka tersebut.

3. Iterasi array `nums` dan untuk setiap elemen `nums[i]`, hitung rev(nums[i]) (angka hasil pembalikan) menggunakan fungsi `reverseNumber` yang akan kita buat.

4. Selanjutnya, hitung jumlah pasangan yang memenuhi syarat `nice` dengan menambahkan frekuensi kemunculan setiap angka hasil penjumlahan pada HashMap.

5. Kembalikan nilai hasil penjumlahan tersebut sebagai hasil dari fungsi `countNicePairs`.

Berikut adalah implementasi dalam Java:

```java
import java.util.HashMap;

public class Solution {
    public int countNicePairs(int[] nums) {
        final int MOD = 1000000007;
        HashMap<Integer, Integer> countMap = new HashMap<>();
        int nicePairsCount = 0;

        for (int num : nums) {
            int reversedNum = reverseNumber(num);
            int diff = num - reversedNum;

            // Update countMap
            countMap.put(diff, countMap.getOrDefault(diff, 0) + 1);
        }

        for (int count : countMap.values()) {
            // Calculate number of nice pairs for each count
            nicePairsCount = (nicePairsCount + ((long) count * (count - 1) / 2)) % MOD;
        }

        return nicePairsCount;
    }

    private int reverseNumber(int num) {
        int reversedNum = 0;
        while (num > 0) {
            reversedNum = (reversedNum * 10) + (num % 10);
            num /= 10;
        }
        return reversedNum;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        int[] nums1 = {42, 11, 1, 97};
        int[] nums2 = {13, 10, 35, 24, 76};

        System.out.println(solution.countNicePairs(nums1)); // Output: 2
        System.out.println(solution.countNicePairs(nums2)); // Output: 4
    }
}
```

Dalam contoh di atas, kita membuat kelas `Solution` dengan metode `countNicePairs` untuk menyelesaikan masalah yang diminta. Fungsi `reverseNumber` digunakan untuk menghitung angka hasil pembalikan (reverse) dari angka yang diberikan.

Kita dapat menguji contoh-contoh yang diberikan dalam masalah dengan menginstansiasi kelas `Solution` dan memanggil metode `countNicePairs` dengan input yang sesuai. Perhatikan bahwa kita menggunakan operasi modulo (MOD) untuk menghindari angka yang terlalu besar dalam perhitungan.

## Complexity

n/a

## Solution

n/a

## Additional

Problem real dari permasalahan di atas adalah mencari jumlah pasangan indeks yang memenuhi syarat "nice" pada array yang panjangnya mencapai maksimal 10^5 (100.000) elemen. Permasalahan ini dapat menjadi sulit karena membutuhkan waktu komputasi yang efisien untuk menyelesaikannya.

Beberapa potensi tantangan atau kendala yang mungkin dihadapi dalam menyelesaikan masalah ini adalah:

1. Efisiensi waktu: Karena panjang array "nums" bisa sangat besar, algoritma harus dirancang untuk berjalan dengan cepat dan efisien. Jika algoritma yang digunakan lambat, maka waktu eksekusi bisa sangat lama dan tidak memungkinkan untuk menyelesaikan masalah dalam waktu yang wajar.

2. Perhitungan jumlah pasangan: Untuk mencari jumlah pasangan indeks yang memenuhi syarat "nice", kita harus menghitung semua kemungkinan pasangan (i, j) yang memenuhi kondisi 0 <= i < j < nums.length dan nums[i] + rev(nums[j]) == nums[j] + rev(nums[i]). Perhitungan ini dapat memakan banyak waktu jika tidak dioptimalkan dengan baik.

3. Penanganan angka besar: Nilai angka dalam array "nums" dapat mencapai 10^9 (1 miliar). Hal ini bisa menyebabkan masalah dalam perhitungan, terutama ketika melakukan operasi matematika seperti pembagian dan perkalian. Jika tidak dikelola dengan baik, hal ini bisa menyebabkan angka overflow atau hasil yang tidak akurat.

4. Penanganan nilai besar: Karena kita diminta untuk mengembalikan hasil modulo 10^9 + 7, kita harus memastikan hasil perhitungan tetap berada dalam batas-batas ini agar menghindari overflow.

Untuk mengatasi tantangan ini, perlu dirancang algoritma yang efisien, menggunakan struktur data yang tepat, dan mengoptimalkan perhitungan matematika untuk menangani kasus dengan ukuran data besar. Juga, penting untuk menghindari operasi yang bisa menyebabkan overflow atau akurasi yang tidak tepat saat melakukan perhitungan.
