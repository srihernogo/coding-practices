# 21. Merge Two Sorted Lists

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)

## Description

Diberikan dua linked list terurut, `list1` dan `list2`. Tugasnya adalah menggabungkan kedua linked list menjadi satu linked list terurut. Linked list baru ini akan terbentuk dengan menggabungkan simpul-simpul dari kedua linked list pertama.

Contoh 1:

![alt text](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```text
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

Contoh 2:

```text
Input: list1 = [], list2 = []
Output: []
```

Contoh 3:

```text
Input: list1 = [], list2 = [0]
Output: [0]
```

**Constraints:**

- The number of nodes in both lists is in the range [0, 50].
- -100 <= Node.val <= 100
- Both list1 and list2 are sorted in non-decreasing order.

Masalah ini meminta Anda untuk menggabungkan dua linked list terurut menjadi satu linked list terurut baru. Linked list baru ini harus terdiri dari simpul-simpul dari kedua linked list pertama.

## Approach

Berikut adalah solusi untuk menggabungkan dua linked list terurut menjadi satu linked list terurut menggunakan **iterasi**:

1. Buat sebuah simpul baru `dummyHead` yang akan berfungsi sebagai simpul awal dari linked list hasil.
2. Buat dua pointer, `current` dan `prev`, dan inisialisasikan keduanya dengan `dummyHead`.
3. Lakukan loop sampai salah satu dari `list1` atau `list2` habis:
   - Jika nilai simpul saat ini di `list1` lebih kecil atau sama dengan nilai simpul saat ini di `list2`, maka tambahkan simpul dari `list1` ke hasil.
   - Jika nilai simpul saat ini di `list1` lebih besar dari nilai simpul saat ini di `list2`, maka tambahkan simpul dari `list2` ke hasil.
   - Setelah tambahan simpul, geser pointer `current` dan `prev` ke simpul berikutnya.
4. Setelah loop selesai, cek apakah ada sisa simpul dalam `list1` atau `list2`. Jika ada, tambahkan sisa simpul ke hasil.
5. Kembalikan simpul awal dari hasil (`dummyHead.next`).

Berikut adalah implementasi solusi dalam bahasa Java:

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
    }
}

public class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummyHead = new ListNode(0);
        ListNode current = dummyHead;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }

        if (list1 != null) {
            current.next = list1;
        }

        if (list2 != null) {
            current.next = list2;
        }

        return dummyHead.next;
    }
}
```

## Test Scenarios

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        ListNode list1 = new ListNode(1);
        list1.next = new ListNode(2);
        list1.next.next = new ListNode(4);

        ListNode list2 = new ListNode(1);
        list2.next = new ListNode(3);
        list2.next.next = new ListNode(4);

        ListNode result = solution.mergeTwoLists(list1, list2);

        assertEquals(1, result.val);
        assertEquals(1, result.next.val);
        assertEquals(2, result.next.next.val);
        assertEquals(3, result.next.next.next.val);
        assertEquals(4, result.next.next.next.next.val);
        assertEquals(4, result.next.next.next.next.next.val);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        ListNode list1 = null;
        ListNode list2 = null;

        ListNode result = solution.mergeTwoLists(list1, list2);

        assertEquals(null, result);
    }

    @Test
    public void testExample3() {
        Solution solution = new Solution();
        ListNode list1 = null;
        ListNode list2 = new ListNode(0);

        ListNode result = solution.mergeTwoLists(list1, list2);

        assertEquals(0, result.val);
        assertEquals(null, result.next);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(m + n), di mana "m" adalah jumlah simpul dalam `list1` dan "n" adalah jumlah simpul dalam `list2`.
- Space: O(1), karena kita hanya menggunakan konstan jumlah variabel tambahan untuk menyimpan hasil penggabungan.

## Submit Solution

n/a

## Additional

n/a
