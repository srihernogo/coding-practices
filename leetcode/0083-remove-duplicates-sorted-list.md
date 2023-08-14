# 83. Remove Duplicates from Sorted List

**Array** $\color{green}{(Easy)}$

[https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

## Description

Diberikan kepala (head) dari sebuah linked list yang terurut, tugas Anda adalah menghapus semua duplikat sehingga setiap elemen muncul hanya sekali. Hasilnya adalah linked list yang tetap terurut.

Contoh 1:

![alt text](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

```text
Input: head = [1,1,2]
Output: [1,2]
```

Contoh 2:

![alt text](https://assets.leetcode.com/uploads/2021/01/04/list2.jpg)

```text
Input: head = [1,1,2,3,3]
Output: [1,2,3]
```

**Constraints:**

- The number of nodes in the list is in the range [0, 300].
- -100 <= Node.val <= 100
- The list is guaranteed to be sorted in ascending order.

Masalah ini meminta Anda untuk menghapus duplikat dari linked list yang terurut dan mengembalikan linked list yang tetap terurut.

## Approach

Berikut adalah pendekatan untuk menghapus duplikat dari linked list terurut:

1. Inisialisasi pointer `current` yang akan digunakan untuk menjelajahi linked list.
2. Selama `current` dan `current.next` tidak bernilai `null`, periksa apakah `current.val` sama dengan `current.next.val`.
3. Jika sama, maka `current.next` adalah duplikat dan perlu dihapus. Anda dapat melakukan ini dengan menggeser `current.next` ke node setelahnya, yaitu `current.next.next`.
4. Jika tidak sama, maka lanjutkan ke node berikutnya dengan `current = current.next`.

Dengan mengikuti pendekatan di atas, Anda akan dapat menghapus semua duplikat dari linked list terurut dan menghasilkan linked list baru yang tetap terurut.

## Java Solution

Berikut adalah solusi dalam bahasa Java:

```java
class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

public class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode current = head;
        while (current != null && current.next != null) {
            if (current.val == current.next.val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        return head;
    }
}
```

## Test Scenario

Berikut adalah beberapa skenario pengujian yang bisa digunakan untuk menguji solusi di atas:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class SolutionTest {

    @Test
    public void testExample1() {
        Solution solution = new Solution();
        ListNode head = new ListNode(1, new ListNode(1, new ListNode(2)));
        ListNode result = solution.deleteDuplicates(head);
        ListNode expected = new ListNode(1, new ListNode(2));
        assertEquals(expected.val, result.val);
        assertEquals(expected.next.val, result.next.val);
        assertEquals(expected.next.next, result.next.next);
    }

    @Test
    public void testExample2() {
        Solution solution = new Solution();
        ListNode head = new ListNode(1, new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(3)))));
        ListNode result = solution.deleteDuplicates(head);
        ListNode expected = new ListNode(1, new ListNode(2, new ListNode(3)));
        assertEquals(expected.val, result.val);
        assertEquals(expected.next.val, result.next.val);
        assertEquals(expected.next.next.val, result.next.next.val);
        assertEquals(expected.next.next.next, result.next.next.next);
    }

    // Test scenarios for edge cases and additional coverage can be added.
}
```

## Complexity

- Time: O(N), di mana "N" adalah jumlah node dalam linked list.
- Space: O(1)

Kompleksitas waktu dari solusi ini adalah O(N), di mana "N" adalah jumlah node dalam linked list. Karena solusi ini hanya melalui linked list sekali dan menghapus node duplikat secara langsung saat ditemukan. Kompleksitas ruang adalah O(1), karena solusi ini tidak menggunakan struktur data tambahan yang berubah seiring dengan ukuran input.

## Submit Solution

n/a

## Additional

n/a
