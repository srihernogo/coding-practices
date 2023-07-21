# 1806. Minimum Number of Operations to Reinitialize a Permutation

## Description

[https://leetcode.com/problems/minimum-number-of-operations-to-reinitialize-a-permutation/](https://leetcode.com/problems/minimum-number-of-operations-to-reinitialize-a-permutation/)

Masalah ini berkaitan dengan permutasi array dan operasi pada array tersebut.

Anda diberikan sebuah bilangan bulat genap n dan awalnya sebuah permutasi perm dari ukuran n, di mana setiap elemen perm[i] == i (indeks dimulai dari 0).

Dalam setiap operasi, Anda akan membuat array baru bernama arr, dan untuk setiap i:

- Jika i % 2 == 0, maka arr[i] = perm[i / 2]
- Jika i % 2 == 1, maka arr[i] = perm[n / 2 + (i - 1) / 2]

Kemudian Anda akan mengganti perm dengan arr.

Tugas Anda adalah mencari jumlah minimum operasi non-nol yang perlu Anda lakukan pada perm agar kembali ke nilai permutasi awal.

Contoh 1:

```
Input: n = 2
Output: 1
Penjelasan: perm = [0, 1] pada awalnya.
Setelah operasi pertama, perm = [0, 1].
Jadi hanya diperlukan 1 operasi.
```

Contoh 2:

```text
Input: n = 4
Output: 2
Penjelasan: perm = [0, 1, 2, 3] pada awalnya.
Setelah operasi pertama, perm = [0, 2, 1, 3].
Setelah operasi kedua, perm = [0, 1, 2, 3].
Jadi hanya diperlukan 2 operasi.
```

Contoh 3:

```text
Input: n = 6
Output: 4
Penjelasan: perm = [0, 1, 2, 3, 4, 5] pada awalnya.
Setelah operasi pertama, perm = [0, 3, 1, 4, 2, 5].
Setelah operasi kedua, perm = [0, 4, 3, 1, 2, 5].
Setelah operasi ketiga, perm = [0, 1, 4, 3, 2, 5].
Setelah operasi keempat, perm = [0, 1, 2, 4, 3, 5].
Jadi hanya diperlukan 4 operasi.
```

Constraints:

- 2 <= n <= 1000
- n adalah bilangan bulat genap.

## Approach

Untuk menyelesaikan masalah ini menggunakan Java, kita dapat mengimplementasikan algoritma berikut:

1. Buat fungsi untuk mencari jumlah minimum operasi non-nol yang diperlukan untuk mengembalikan permutasi ke nilai awalnya. Kita bisa menyebut fungsi ini `minOperations`

2. Dalam fungsi `minOperations`, kita dapat menggunakan pendekatan berikut:

   - Pertama, inisialisasi variabel `count` sebagai 0 untuk menghitung jumlah operasi.
   - Selanjutnya, buat perulangan while untuk melakukan operasi pada permutasi sampai permutasi kembali ke nilai awalnya. Di dalam perulangan:
     - Periksa apakah permutasi telah kembali ke nilai awalnya. Jika ya, keluar dari perulangan.
     - Buat array baru `arr` dengan ukuran yang sama dengan `n`.
     - Lakukan operasi sesuai dengan keterangan dalam soal untuk setiap indeks i dan isi `arr` dengan nilai baru.
     - Setelah itu, tandai permutasi `perm` dengan array `arr`.
     - Tambahkan 1 ke variabel `count` untuk menghitung operasi yang telah dilakukan.

3. Kembalikan nilai variabel `count` sebagai hasil dari fungsi `minOperations`.

Berikut adalah contoh implementasi dalam Java:

```java
public class Solution {
    public int minOperations(int n) {
        int[] perm = new int[n];
        for (int i = 0; i < n; i++) {
            perm[i] = i;
        }

        int count = 0;
        while (!isInitialPermutation(perm)) {
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) {
                if (i % 2 == 0) {
                    arr[i] = perm[i / 2];
                } else {
                    arr[i] = perm[n / 2 + (i - 1) / 2];
                }
            }
            perm = arr;
            count++;
        }

        return count;
    }

    private boolean isInitialPermutation(int[] perm) {
        for (int i = 0; i < perm.length; i++) {
            if (perm[i] != i) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        int n1 = 2;
        int n2 = 4;
        int n3 = 6;

        System.out.println(solution.minOperations(n1)); // Output: 1
        System.out.println(solution.minOperations(n2)); // Output: 2
        System.out.println(solution.minOperations(n3)); // Output: 4
    }
}
```

Dalam contoh ini, kita membuat kelas `Solution` dengan metode `minOperations` untuk menyelesaikan masalah yang diminta. Fungsi `isInitialPermutation` digunakan untuk memeriksa apakah permutasi telah kembali ke nilai awalnya atau belum.

Kita dapat menguji contoh-contoh yang diberikan dalam masalah dengan menginstansiasi kelas `Solution` dan memanggil metode `minOperations` dengan input yang sesuai.

## Complexity

n/a

## Solution

n/a

## Additional

_Apa itu permutasi?_

`Permutasi` adalah pengaturan atau susunan dari elemen-elemen dalam suatu himpunan atau urutan tertentu. Dalam matematika, permutasi mengacu pada setiap pengaturan yang berbeda dari elemen-elemen suatu himpunan tanpa mengulang elemen yang sama dan mengubah urutan elemen tersebut. Artinya, permutasi berbeda memiliki urutan elemen yang berbeda pula.

Misalnya, jika kita memiliki himpunan {1, 2, 3}, ada enam permutasi berbeda yang dapat kita bentuk dengan elemen-elemen ini:

```text
{1, 2, 3}
{1, 3, 2}
{2, 1, 3}
{2, 3, 1}
{3, 1, 2}
{3, 2, 1}
```

Seperti yang terlihat di atas, setiap permutasi adalah pengaturan unik dari elemen-elemen tersebut. Setiap elemen hanya muncul sekali dalam setiap permutasi, dan urutan elemen berbeda di setiap permutasi.

Jumlah total permutasi dari himpunan dengan n elemen dapat dihitung dengan rumus n! (faktorial n).
Faktorial dari sebuah bilangan n (dinotasikan dengan n!) adalah hasil perkalian dari semua bilangan bulat positif dari 1 hingga n.
Sebagai contoh, 3! = 3 x 2 x 1 = 6, yang sesuai dengan jumlah permutasi yang dapat dibentuk dari himpunan {1, 2, 3}.

Permutasi memiliki berbagai aplikasi di berbagai bidang matematika dan ilmu komputer,
seperti kombinatorik, algoritma, analisis algoritma, dan pemrosesan string.
