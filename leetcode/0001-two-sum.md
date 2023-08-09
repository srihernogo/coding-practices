# 1. Two Sum

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

## Description

Diberikan sebuah array bilangan bulat `nums` dan sebuah bilangan bulat `target`. Tugasnya adalah mencari dan mengembalikan indeks dari dua bilangan dalam array yang jika dijumlahkan akan menghasilkan nilai `target`.

Dijamin bahwa setiap input akan memiliki tepat satu solusi, dan Anda tidak dapat menggunakan elemen yang sama dua kali untuk membentuk jumlah.

Hasil jawaban dapat dikembalikan dalam urutan mana saja.

Contoh 1:

```text
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Penjelasan: Karena nums[0] + nums[1] == 9, kita mengembalikan [0, 1].
```

Contoh 2:

```text
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

Contoh 3:

```text
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

- 2 <= nums.length <= 10<sup>4</sup>
- -10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>
- -10<sup>9</sup> <= target <= 10<sup>9</sup>
- `Only one valid answer exists.`

Pertanyaan Tambahan (Follow-up): Bisakah Anda menciptakan algoritma dengan kompleksitas waktu kurang dari `O(n2)`?

Pertanyaan tambahan ini menantang Anda untuk menemukan algoritma yang memiliki kompleksitas waktu kurang dari `O(n^2)`, artinya algoritma tersebut harus lebih efisien dibandingkan dengan pendekatan nested loop yang sederhana. Ini mendorong Anda untuk menjelajahi algoritma yang lebih dioptimalkan untuk memecahkan masalah ini.

## Approach

Berikut adalah solusi untuk permasalahan ini menggunakan bahasa pemrograman Java:

```java
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numToIndex = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (numToIndex.containsKey(complement)) {
                return new int[] {numToIndex.get(complement), i};
            }
            numToIndex.put(nums[i], i);
        }

        throw new IllegalArgumentException("No two sum solution");
    }
}
```

Solusi di atas menggunakan pendekatan "One-pass Hash Table". Ide utamanya adalah dengan memanfaatkan struktur data HashMap untuk menyimpan setiap elemen beserta indeksnya saat sedang melewati array. Kemudian, saat melewati array lagi, kita dapat dengan cepat memeriksa apakah elemen yang dibutuhkan untuk mencapai target sudah ada dalam HashMap atau belum.

## Test Scenario

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertArrayEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        int[] result = solution.twoSum(nums, target);
        int[] expected = {0, 1};
        assertArrayEquals(expected, result);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        int[] nums = {3, 2, 4};
        int target = 6;
        int[] result = solution.twoSum(nums, target);
        int[] expected = {1, 2};
        assertArrayEquals(expected, result);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(N)
- Space: O(N)

Solusi yang diberikan dengan menggunakan pendekatan "One-pass Hash Table" telah mengimplementasikan kompleksitas waktu yang kurang dari O(n^2). Kompleksitas waktu dari solusi ini adalah O(n), di mana "n" adalah panjang array nums.

Solusi ini lebih efisien daripada pendekatan brute-force dengan kompleksitas waktu O(n^2), di mana kita akan membandingkan setiap pasangan elemen dalam array untuk mencari jawaban yang cocok dengan target. Dengan pendekatan "One-pass Hash Table," kita hanya melintasi array sekali, dan ketika mencari pasangan yang cocok dengan target, kita dapat dengan cepat memeriksa apakah elemen yang dibutuhkan sudah ada dalam HashMap atau belum, yang dilakukan dengan kompleksitas konstan O(1).

## Submit Solution

n/a

## Additional

n/a
