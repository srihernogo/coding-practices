# 1814. Count Nice Pairs in an Array

Level: $\color{green}{Easy}$

[https://leetcode.com/problems/maximum-population-year/](https://leetcode.com/problems/maximum-population-year/)

## Description

Dalam masalah ini, Anda diberikan sebuah array 2D bernama `logs` di mana setiap elemen `logs[i] = [birth`<sub>`i`</sub>`, death`<sub>`i`</sub>`]` menunjukkan tahun kelahiran dan tahun kematian dari orang `ke-i`.

Populasi suatu tahun `x` adalah jumlah orang yang hidup selama tahun tersebut. Orang `ke-i` dihitung dalam populasi tahun `x` jika `x` berada dalam rentang inklusif `[birth`<sub>`i`</sub>`, death`<sub>`i`</sub>` - 1]`.

Perlu dicatat bahwa orang tersebut tidak dihitung dalam populasi tahun kematian mereka.

Tugas Anda adalah mengembalikan tahun paling awal dengan populasi maksimum.

Contoh 1:

```text
Input: logs = [[1993, 1999], [2000, 2010]]
Output: 1993
Penjelasan: Populasi maksimum adalah 1, dan tahun paling awal dengan populasi tersebut adalah 1993.
```

Contoh 2:

```text
Input: logs = [[1950, 1961], [1960, 1971], [1970, 1981]]
Output: 1960
Penjelasan: Populasi maksimum adalah 2, dan terjadi pada tahun 1960 dan 1970. Tahun paling awal di antara keduanya adalah 1960.
```

**Constraints:**

- `1 <= logs.length <= 100`
- `1950 <= birth`<sub>`i`</sub>` < death`<sub>`i`</sub>` <= 2050`

## Approach

**Untuk menyelesaikan masalah ini menggunakan Java, kita dapat mengimplementasikan algoritma berikut:**

1. Buat kelas Solution dengan metode maximumPopulationYear yang akan mencari tahun dengan populasi maksimum.

2. Dalam metode maximumPopulationYear, kita akan menggunakan pendekatan berikut:
   - Buat array `population` yang akan berfungsi untuk menghitung populasi pada setiap tahun.
   - Iterasi `logs` dan untuk setiap elemen "logs[i]", tambahkan 1 ke `population[birth`<sub>`i`</sub>` - 1950]` dan kurangi 1 dari `population[death`<sub>`i`</sub>` - 1950]`
   - Selanjutnya, lakukan iterasi pada array `population` dan hitung populasi kumulatif untuk setiap tahun berdasarkan perubahan populasinya.
   - Tentukan tahun dengan populasi maksimum dan kembalikan tahun tersebut.

Berikut adalah implementasi dalam Java:

```java
public class Solution {
    public int maximumPopulationYear(int[][] logs) {
        // Array untuk menyimpan populasi pada setiap tahun (1950 - 2050)
        int[] population = new int[101];

        for (int[] log : logs) {
            int birthYear = log[0];
            int deathYear = log[1];

            // Tambahkan 1 ke populasi pada tahun kelahiran
            population[birthYear - 1950]++;
            // Kurangi 1 dari populasi pada tahun kematian (dikurangi karena orang tersebut tidak dihitung pada tahun kematian)
            population[deathYear - 1950]--;
        }

        // Hitung populasi kumulatif untuk setiap tahun
        int maxPopulation = 0;
        int maxPopulationYear = 1950;
        int currentPopulation = 0;
        for (int i = 0; i < population.length; i++) {
            currentPopulation += population[i];
            if (currentPopulation > maxPopulation) {
                maxPopulation = currentPopulation;
                maxPopulationYear = 1950 + i;
            }
        }

        return maxPopulationYear;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        int[][] logs1 = {{1993, 1999}, {2000, 2010}};
        int[][] logs2 = {{1950, 1961}, {1960, 1971}, {1970, 1981}};

        System.out.println(solution.maximumPopulationYear(logs1)); // Output: 1993
        System.out.println(solution.maximumPopulationYear(logs2)); // Output: 1960
    }
}
```

## Complexity

n/a

## Solution

n/a

## Additional

Problem real dari permasalahan ini adalah mencari tahun dengan populasi maksimum berdasarkan data sejarah kelahiran dan kematian orang-orang dalam suatu periode waktu. Dalam kasus dunia nyata, masalah ini dapat menjadi relevan dalam beberapa situasi berikut:

1. **Studi sejarah demografi**: Permasalahan ini dapat diaplikasikan dalam studi sejarah demografi untuk mengetahui periode waktu di mana populasi manusia mencapai puncaknya. Hal ini dapat membantu untuk memahami tren pertumbuhan populasi, mengidentifikasi peristiwa historis yang mempengaruhi pertumbuhan penduduk, dan mendapatkan wawasan tentang perubahan sosial dan ekonomi dalam masyarakat.

2. **Perencanaan sumber daya dan infrastruktur**: Mengetahui tahun dengan populasi maksimum dalam suatu wilayah dapat membantu dalam perencanaan sumber daya dan infrastruktur. Dengan informasi ini, pemerintah atau organisasi dapat mengantisipasi permintaan dan kebutuhan masyarakat, termasuk perumahan, fasilitas kesehatan, pendidikan, transportasi, dan lainnya.

3. **Analisis tren ekonomi**: Informasi tentang populasi maksimum dalam suatu periode waktu dapat berkontribusi pada analisis tren ekonomi. Pertumbuhan populasi yang signifikan dapat berdampak pada pasar tenaga kerja, tingkat konsumsi, dan permintaan atas berbagai produk dan layanan.

4. **Perencanaan kebijakan sosial**: Pengetahuan tentang tahun dengan populasi maksimum dapat membantu dalam perencanaan kebijakan sosial, seperti program kesejahteraan sosial dan kesehatan masyarakat. Informasi ini dapat digunakan untuk mengalokasikan dana dan sumber daya dengan lebih efektif untuk memenuhi kebutuhan penduduk.

Dalam kehidupan nyata, masalah ini mungkin melibatkan data besar dari catatan kelahiran dan kematian, dan memerlukan analisis statistik yang cermat untuk mengidentifikasi tahun dengan populasi maksimum dengan akurat. Oleh karena itu, algoritma dan metode yang efisien dan tepat perlu digunakan untuk menyelesaikan permasalahan ini.
