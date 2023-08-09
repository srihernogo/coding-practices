# 70. Climbing Stairs

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)

## Description

Dalam masalah ini, Anda diberikan sebuah tangga yang memiliki n langkah. Setiap kali Anda dapat naik 1 atau 2 langkah. Tugas Anda adalah menghitung berapa banyak cara yang berbeda untuk mencapai puncak tangga.

Contoh 1:

```text
Input: n = 2
Output: 2
Explanation: Ada dua cara untuk mencapai puncak tangga.
1. 1 langkah + 1 langkah
2. 2 langkah
```

Contoh 2:

```text
Input: n = 3
Output: 3
Explanation: Ada tiga cara untuk mencapai puncak tangga.
1. 1 langkah + 1 langkah + 1 langkah
2. 1 langkah + 2 langkah
3. 2 langkah + 1 langkah
```

**Constraints:**

- `1 <= n <= 45`

Anda diminta untuk menghitung berapa banyak cara yang berbeda untuk mencapai puncak tangga dengan n langkah, dengan setiap kali Anda bisa naik 1 atau 2 langkah.

## Approach

Pendekatan yang efisien untuk masalah ini adalah menggunakan teknik **Dynamic Programming**. Kita dapat memanfaatkan sifat dari masalah ini yang dapat direduksi menjadi submasalah yang lebih kecil.

Kita dapat memahami bahwa jumlah cara untuk mencapai langkah ke-i (denoted as `dp[i]`) adalah hasil penjumlahan dari dua langkah sebelumnya, yaitu `dp[i-1]` dan `dp[i-2]`. Ini karena setiap kali kita hanya dapat naik 1 atau 2 langkah.

Berikut adalah implementasi solusi dalam bahasa Java:

```java
public class Solution {
    public int climbStairs(int n) {
        if (n <= 1) {
            return 1;
        }

        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }
}
```

1. Buat array `dp` dengan ukuran `n+1` yang akan menyimpan jumlah cara untuk mencapai setiap langkah.
2. Inisialisasi `dp[0]` dan `dp[1]` dengan nilai 1, karena hanya ada satu cara untuk mencapai langkah 0 dan langkah 1.
3. Loop dari langkah 2 hingga n:
   - Hitung `dp[i]` dengan `dp[i-1] + dp[i-2]`, karena jumlah cara untuk mencapai langkah ke-i adalah jumlah cara untuk mencapai langkah sebelumnya dan langkah dua sebelumnya.
4. Setelah loop selesai, nilai `dp[n]` akan berisi jumlah cara untuk mencapai puncak tangga dengan n langkah.

## Test Scenarios

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        int n = 2;
        int result = solution.climbStairs(n);
        assertEquals(2, result);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        int n = 3;
        int result = solution.climbStairs(n);
        assertEquals(3, result);
    }

    @Test
    public void testAdditionalCase() {
        Solution solution = new Solution();
        int n = 5;
        int result = solution.climbStairs(n);
        assertEquals(8, result);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(n), karena kita melakukan loop dari 2 hingga n untuk menghitung `dp[i]` dengan mengakses nilai sebelumnya.
- Space: O(n), karena kita menggunakan array `dp` dengan ukuran n+1 untuk menyimpan nilai dp[i].

Solusi ini memiliki kompleksitas waktu dan ruang yang efisien, sehingga sangat cocok untuk masalah ini dengan batasan n yang diberikan.

## Submit Solution

n/a

## Additional

n/a
