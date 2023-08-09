# 46. Permutations

**Array** $\color{orange}{(Medium)}$

[https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)

## Description

Diberikan sebuah array `nums` berisi bilangan bulat yang berbeda-beda, tugasnya adalah menghasilkan semua kemungkinan permutasi elemen-elemen dalam array tersebut. Hasil permutasi dapat dikembalikan dalam urutan apa pun.

Contoh 1:

```text
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

Contoh 2:

```text
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

Contoh 3:

```text
Input: nums = [1]
Output: [[1]]
```

**Constraints:**

- `1 <= nums.length <= 6`
- `-10 <= nums[i] <= 10`
- `All the integers of nums are unique.`

Masalah ini meminta Anda untuk menghasilkan semua permutasi mungkin dari elemen-elemen dalam array `nums` yang diberikan. Setiap permutasi harus terdiri dari seluruh elemen dari array masukan, dan urutan elemen dapat bervariasi. Batasan mengatur panjang array masukan dan rentang nilai bilangan bulat di dalamnya. Tujuan Anda adalah memberikan solusi yang menghasilkan semua permutasi mungkin dari elemen-elemen secara efisien.

## Approach

Berikut adalah solusi untuk menghasilkan semua permutasi mungkin dari array `nums` menggunakan **rekursi**:

```java
import java.util.ArrayList;
import java.util.List;

public class Solution {
    // Approach:
    // The problem can be solved using a backtracking approach. We can generate
    // all possible permutations of the distinct integers in the input array.

    // Function to generate all possible permutations of nums
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, new ArrayList<>(), result);
        return result;
    }

    // Backtracking function to generate permutations
    private void backtrack(int[] nums, List<Integer> current, List<List<Integer>> result) {
        // If current list has all elements, add it to the result
        if (current.size() == nums.length) {
            result.add(new ArrayList<>(current));
            return;
        }

        // Iterate through each element in nums
        for (int num : nums) {
            // If num is not already in the current list
            if (!current.contains(num)) {
                // Add num to the current list
                current.add(num);

                // Recursively backtrack to generate permutations
                backtrack(nums, current, result);

                // Remove the last element for backtracking
                current.remove(current.size() - 1);
            }
        }
    }

}
```

Berikut adalah pendekatan dan langkah-langkah solusi dari potongan kode di atas:

1. Pertama, kita mendefinisikan fungsi `permute` yang menerima array `nums` sebagai input dan mengembalikan daftar dari semua permutasi mungkin.
2. Di dalam fungsi `permute`, kita membuat variabel `result` yang akan menampung hasil akhir berupa daftar dari semua permutasi.
3. Selanjutnya, kita memanggil fungsi `backtrack` dengan parameter `nums`, daftar `current`, dan `result`. Ini adalah titik awal rekursi untuk menghasilkan semua permutasi.
4. Di dalam fungsi `backtrack`, kita memeriksa apakah panjang daftar `current` sama dengan panjang array `nums`. Jika iya, artinya kita telah menghasilkan satu permutasi lengkap, jadi kita menambahkannya ke dalam `result`.
5. Jika panjang `current` belum sama dengan panjang `nums`, kita akan melakukan iterasi melalui setiap elemen `nums`.
6. Dalam setiap iterasi, kita periksa apakah elemen tersebut sudah ada dalam `current` dengan menggunakan `current.contains(num)`. Jika belum, kita tambahkan elemen tersebut ke `current`.
7. Setelah menambahkan elemen, kita panggil kembali fungsi `backtrack` secara rekursif untuk melanjutkan proses pembentukan permutasi.
8. Setelah pemanggilan rekursif selesai, kita perlu menghapus elemen terakhir dari `current` menggunakan `current.remove(current.size() - 1)`. Ini adalah langkah backtracking yang memungkinkan kita untuk mencoba elemen-elemen lain dalam iterasi berikutnya.
9. Keseluruhan proses akan berlanjut sampai kita menghasilkan semua permutasi mungkin dengan elemen-elemen unik dari `nums`.

Solusi ini menggunakan teknik backtracking untuk menghasilkan semua permutasi. Namun, perlu diingat bahwa pendekatan ini memiliki kompleksitas waktu yang tinggi karena jumlah permutasi yang harus dihasilkan adalah N!, di mana N adalah panjang array `nums`.

## Test Scenario

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        int[] nums = {1, 2, 3};
        List<List<Integer>> result = solution.permute(nums);
        List<List<Integer>> expected = new ArrayList<>();
        expected.add(Arrays.asList(1, 2, 3));
        expected.add(Arrays.asList(1, 3, 2));
        expected.add(Arrays.asList(2, 1, 3));
        expected.add(Arrays.asList(2, 3, 1));
        expected.add(Arrays.asList(3, 1, 2));
        expected.add(Arrays.asList(3, 2, 1));
        assertEquals(expected, result);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        int[] nums = {0, 1};
        List<List<Integer>> result = solution.permute(nums);
        List<List<Integer>> expected = new ArrayList<>();
        expected.add(Arrays.asList(0, 1));
        expected.add(Arrays.asList(1, 0));
        assertEquals(expected, result);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(N \* N!), di mana "N" adalah panjang array nums.
- Space: O(N), di mana "N" adalah panjang array nums.

Kompleksitas waktu untuk menghasilkan semua permutasi mungkin adalah O(N \* N!), di mana "N" adalah panjang array `nums`. Ini karena ada N! permutasi yang mungkin, dan setiap permutasi memerlukan O(N) waktu untuk diproses. Kompleksitas ruang adalah O(N) karena rekursi menggunakan stack untuk menyimpan urutan elemen saat melakukan backtracking.

**Apakah kompleksitas tersebut adalah yang terbaik?**
Tidak, kompleksitas waktu O(N _ N!) pada solusi yang dijelaskan di atas sebenarnya tidaklah yang terbaik untuk menghasilkan semua permutasi. Ini karena kompleksitas faktorial (N!) tumbuh sangat cepat seiring dengan pertambahan nilai N, dan kompleksitas N _ N! dapat menjadi sangat besar bahkan untuk nilai N yang relatif kecil.

Untuk permasalahan ini, tidak ada solusi yang berjalan dalam waktu polinomial terhadap panjang array `nums`. Namun, ada algoritma yang lebih efisien dalam hal kompleksitas waktu dibandingkan dengan O(N \* N!). Salah satu pendekatan yang lebih efisien adalah menggunakan algoritma Heap's Permutation atau algoritma Johnson-Trotter.

Namun, mengingat bahwa batasan panjang array nums dalam soal ini adalah 6, kompleksitas waktu O(N \* N!) masih dapat diterima. Jika Anda mencari solusi yang lebih efisien untuk permasalahan ini dalam kasus umum (tanpa batasan panjang array), maka akan diperlukan pendekatan yang lebih canggih.

## Submit Solution

n/a

## Additional

n/a
