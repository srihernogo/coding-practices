# 19. Remove Nth Node From End of List

**Linked List** $\color{orange}{(Medium)}$

[https://leetcode.com/problems/remove-nth-node-from-end-of-list/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

## Description

Dalam masalah ini, Anda diberikan kepala (head) dari sebuah linked list. Tugas Anda adalah menghapus simpul ke-n dari akhir linked list dan mengembalikan kepala baru dari linked list setelah simpul dihapus.

Contoh 1:

![alt text](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)

```text
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
Penjelasan: Pada linked list ini, jika kita menghapus simpul ke-2 dari akhir (yaitu simpul "4"),
maka linked list baru akan menjadi [1,2,3,5].
```

Contoh 2:

```text
Input: head = [1], n = 1
Output: []
Penjelasan: Karena linked list hanya memiliki satu simpul dan kita diminta untuk menghapusnya,
maka linked list baru menjadi kosong.
```

Contoh 3:

```text
Input: head = [1,2], n = 1
Output: [1]
Penjelasan: Jika kita menghapus simpul terakhir pada linked list,
maka linked list baru hanya memiliki satu simpul, yaitu simpul pertama.
```

**Constraints:**

- `The number of nodes in the list is sz.`
- `1 <= sz <= 30`
- `0 <= Node.val <= 100`
- `1 <= n <= sz`

```text
- Jumlah simpul dalam linked list adalah "sz".
- 1 <= sz <= 30 (jumlah simpul terbatas antara 1 hingga 30).
- Nilai setiap simpul berada dalam rentang 0 hingga 100.
- 1 <= n <= sz (nilai n harus berada dalam rentang 1 hingga jumlah simpul dalam linked list).
```

## Approach

Untuk menghapus simpul ke-n dari akhir linked list dan mengembalikan kepala baru dari linked list setelah simpul dihapus, kita dapat menggunakan pendekatan menggunakan dua pointer. Di sini kita akan menggunakan dua pointer, pointer pertama (fast) akan maju sebanyak n + 1 langkah terlebih dahulu, dan kemudian pointer kedua (slow) akan mulai maju. Ketika pointer pertama mencapai akhir linked list, pointer kedua akan berada pada simpul sebelum simpul yang akan dihapus.

Berikut adalah implementasi solusinya menggunakan Java:

```java
public class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
    }
}

public class Solution {

    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode fast = dummy;
        ListNode slow = dummy;

        // Advance the fast pointer by n + 1 steps
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }

        // Move fast to the end, maintaining the gap
        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }

        // Skip the desired node
        slow.next = slow.next.next;

        return dummy.next;
    }
}
```

Dalam implementasi di atas, kita menggunakan dua pointer "fast" dan "slow". Pointer "fast" akan maju sebanyak n + 1 langkah terlebih dahulu, dan kemudian pointer "slow" akan mulai maju. Ketika pointer "fast" mencapai akhir linked list, pointer "slow" akan berada pada simpul sebelum simpul yang akan dihapus.

Kemudian, kita dapat menghapus simpul dengan menghubungkan pointer "slow" langsung ke simpul setelah simpul yang akan dihapus.

Misalnya, jika linked list adalah `[1,2,3,4,5]` dan n adalah 2, maka setelah operasi, linked list akan menjadi `[1,2,3,5]`.

Kita juga menggunakan simpul "dummy" untuk mengatasi kasus khusus saat simpul pertama perlu dihapus.

Pastikan Anda telah memahami logika dari implementasi di atas dan melihat bagaimana pointer "fast" dan "slow" digunakan untuk menghapus simpul dari akhir linked list.

## Test Scenario

Berikut adalah beberapa skenario pengujian menggunakan pendekatan Test-Driven Development (TDD) untuk fungsi `removeNthFromEnd`:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        // Membuat linked list: 1 -> 2 -> 3 -> 4 -> 5
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        Solution solution = new Solution();
        ListNode newHead = solution.removeNthFromEnd(head, 2);

        // Mengecek apakah linked list menjadi: 1 -> 2 -> 3 -> 5
        assertEquals(1, newHead.val);
        assertEquals(2, newHead.next.val);
        assertEquals(3, newHead.next.next.val);
        assertEquals(5, newHead.next.next.next.val);
    }

    @Test
    public void testExample2() {
        // Membuat linked list: 1
        ListNode head = new ListNode(1);

        Solution solution = new Solution();
        ListNode newHead = solution.removeNthFromEnd(head, 1);

        // Mengecek apakah linked list menjadi kosong
        assertEquals(null, newHead);
    }

    @Test
    public void testExample3() {
        // Membuat linked list: 1 -> 2
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);

        Solution solution = new Solution();
        ListNode newHead = solution.removeNthFromEnd(head, 1);

        // Mengecek apakah linked list menjadi: 1
        assertEquals(1, newHead.val);
        assertEquals(null, newHead.next);
    }

    // Tambahkan lebih banyak metode test untuk menguji kasus-kasus lain sesuai kebutuhan.
}
```

Pada contoh di atas, kita telah membuat beberapa metode test yang mencakup contoh-contoh yang diberikan dan beberapa kasus lainnya. Setiap metode test membuat linked list sesuai dengan skenario yang diberikan, kemudian memanggil fungsi `removeNthFromEnd` untuk menghapus simpul sesuai dengan nilai n yang diberikan, dan akhirnya memeriksa apakah hasilnya sesuai dengan yang diharapkan.

Pastikan Anda mengganti ListNode dengan kelas atau struktur yang Anda gunakan untuk merepresentasikan linked list. Juga, pastikan Anda telah memastikan bahwa implementasi fungsi `removeNthFromEnd` telah sesuai dengan logika yang telah dijelaskan sebelumnya.

## Complexity

Kompleksitas waktu dan ruang dari solusi ini adalah:

- Kompleksitas Waktu: O(N)
- Kompleksitas Ruang: O(1)

Di sini, "N" adalah jumlah simpul dalam linked list.

_Kompleksitas Waktu:_

Pendekatan dengan dua pointer memungkinkan kita untuk melintasi linked list hanya satu kali, sehingga kompleksitas waktu adalah O(N), di mana "N" adalah jumlah simpul dalam linked list.

_Kompleksitas Ruang:_

Solusi ini menggunakan konstan ruang tambahan, terutama untuk dua pointer "fast" dan "slow", serta beberapa variabel sederhana yang digunakan untuk pelacakan. Karena kita tidak menggunakan struktur data tambahan yang berukuran sebanding dengan jumlah simpul dalam linked list, kompleksitas ruangnya adalah O(1), atau konstan.

## Submit Solution

n/a

## Additional

n/a
