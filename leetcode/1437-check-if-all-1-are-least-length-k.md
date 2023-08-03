# 19. Remove Nth Node From End of List

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/check-if-all-1s-are-at-least-length-k-places-away/](https://leetcode.com/problems/check-if-all-1s-are-at-least-length-k-places-away/)

## Description

Diberikan sebuah array biner `nums` dan sebuah bilangan bulat `k`. Tugasnya adalah untuk menentukan apakah semua kemunculan angka 1 dalam array berjarak paling tidak `k` tempat dari satu sama lain. Jika semua angka 1 memenuhi kondisi ini, kembalikan `true`; jika tidak, kembalikan `false`.

Contoh 1:

![alt text](https://assets.leetcode.com/uploads/2020/04/15/sample_1_1791.png)

```text
Input: nums = [1,0,0,0,1,0,0,1], k = 2
Output: true
Penjelasan: Semua kemunculan angka 1 berjarak paling tidak 2 tempat dari satu sama lain.
```

Contoh 2:
![alt text](https://assets.leetcode.com/uploads/2020/04/15/sample_2_1791.png)

```text
Input: nums = [1,0,0,1,0,1], k = 2
Output: false
Penjelasan: Kemunculan kedua angka 1 dan kemunculan ketiga angka 1 hanya berjarak satu tempat.
```

**Constraints:**

- `1 <= nums.length <= 105`
- `0 <= k <= nums.length`
- `nums[i] is 0 or 1` (setiap elemen dalam nums bernilai 0 atau 1)

## Approach

Berikut adalah solusi untuk permasalahan ini menggunakan bahasa pemrograman Java:

```java
public class Solution {
    public boolean kLengthApart(int[] nums, int k) {
        int count = k; // Inisialisasi count dengan k, sehingga pertama kali ditemukan angka 1, kita sudah melewati minimal k tempat.

        for (int num : nums) {
            if (num == 1) {
                if (count < k) {
                    return false; // Jika count kurang dari k, berarti angka 1 ditemukan terlalu dekat.
                }
                count = 0; // Setelah menemukan angka 1, reset count menjadi 0.
            } else {
                count++; // Jika angka 0, increment count.
            }
        }

        return true; // Jika semua angka 1 memenuhi syarat, kembalikan true.
    }
}
```

Pendekatan di sini adalah dengan menggunakan satu perulangan melalui array `nums`. Saat kita menemukan angka 1, kita periksa nilai `count`. Jika `count` kurang dari `k`, berarti ada angka 1 yang ditemukan terlalu dekat. Jika tidak, kita mengatur `count` menjadi 0 untuk menghitung jarak antara angka 1 selanjutnya. Jika angka 0 ditemukan, kita increment `count`. Jika perulangan selesai dan semua angka 1 memenuhi syarat, kita kembalikan `true`, jika tidak, kita kembalikan `false`.

## Test Scenario

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        int[] nums = {1, 0, 0, 0, 1, 0, 0, 1};
        int k = 2;
        boolean result = solution.kLengthApart(nums, k);
        assertEquals(true, result);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        int[] nums = {1, 0, 0, 1, 0, 1};
        int k = 2;
        boolean result = solution.kLengthApart(nums, k);
        assertEquals(false, result);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(N)
- Space: O(1)

Di sini, "N" adalah panjang array nums. Solusi ini hanya melintasi array satu kali, sehingga memiliki kompleksitas waktu O(N). Penggunaan ruang ekstra konstan O(1) hanya untuk beberapa variabel.

## Submit Solution

n/a

## Additional

n/a
