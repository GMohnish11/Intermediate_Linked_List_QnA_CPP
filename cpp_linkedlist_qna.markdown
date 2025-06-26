# Intermediate Linked List Questions and Solutions in C++

This repository contains intermediate-level linked list problems and their solutions in C++, designed for coding interview preparation and competitive programming. Each problem includes a description, a C++ solution, and an explanation. These are ideal for students, developers, or anyone honing their data structures skills.

## Table of Contents
1. [Reverse a Linked List](#reverse-a-linked-list)
2. [Detect and Remove Cycle in a Linked List](#detect-and-remove-cycle-in-a-linked-list)
3. [Merge Two Sorted Linked Lists](#merge-two-sorted-linked-lists)
4. [Find the Middle of a Linked List](#find-the-middle-of-a-linked-list)
5. [Remove Nth Node from End of List](#remove-nth-node-from-end-of-list)

---

## Reverse a Linked List

### Problem
Given a singly linked list, reverse it and return the new head. For example, if the list is `1 -> 2 -> 3 -> 4`, the result is `4 -> 3 -> 2 -> 1`.

### Solution
```cpp
struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* reverseList(ListNode* head) {
    ListNode *prev = nullptr, *curr = head, *next = nullptr;
    while (curr) {
        next = curr->next; // Store next
        curr->next = prev; // Reverse link
        prev = curr;       // Move prev
        curr = next;       // Move curr
    }
    return prev;
}
```

### Explanation
- **Approach**: Iteratively reverse the list by updating pointers: store the next node, reverse the current node’s link to point to the previous node, and move forward.
- **Time Complexity**: O(n), where `n` is the number of nodes.
- **Space Complexity**: O(1), in-place reversal.
- **Edge Cases**: Handles empty lists or single-node lists.

---

## Detect and Remove Cycle in a Linked List

### Problem
Given a linked list, detect if it has a cycle and, if so, remove it. Return the head of the modified list. For example, if the list is `1 -> 2 -> 3 -> 4 -> 2` (cycle at node `2`), remove the cycle to get `1 -> 2 -> 3 -> 4`.

### Solution
```cpp
ListNode* detectAndRemoveCycle(ListNode* head) {
    if (!head || !head->next) return head;
    
    // Detect cycle using Floyd’s cycle-finding algorithm
    ListNode *slow = head, *fast = head;
    bool hasCycle = false;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) {
            hasCycle = true;
            break;
        }
    }
    
    // Remove cycle
    if (hasCycle) {
        slow = head;
        if (slow != fast) {
            while (slow->next != fast->next) {
                slow = slow->next;
                fast = fast->next;
            }
            fast->next = nullptr; // Remove cycle
        } else {
            // Handle cycle starting at head
            while (fast->next != slow) fast = fast->next;
            fast->next = nullptr;
        }
    }
    return head;
}
```

### Explanation
- **Approach**: Use Floyd’s cycle-finding algorithm (two pointers) to detect a cycle. If a cycle exists, find the entry point by resetting one pointer to the head and moving both pointers one step at a time until they meet, then break the cycle.
- **Time Complexity**: O(n), for cycle detection and removal.
- **Space Complexity**: O(1), constant space.
- **Edge Cases**: Handles no cycle, cycle at head, or single-node lists.

---

## Merge Two Sorted Linked Lists

### Problem
Given two sorted linked lists, merge them into a single sorted linked list. For example, if `list1 = 1 -> 3 -> 5` and `list2 = 2 -> 4 -> 6`, the result is `1 -> 2 -> 3 -> 4 -> 5 -> 6`.

### Solution
```cpp
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
    ListNode dummy(0);
    ListNode* tail = &dummy;
    
    while (list1 && list2) {
        if (list1->val <= list2->val) {
            tail->next = list1;
            list1 = list1->next;
        } else {
            tail->next = list2;
            list2 = list2->next;
        }
        tail = tail->next;
    }
    
    tail->next = list1 ? list1 : list2;
    return dummy.next;
}
```

### Explanation
- **Approach**: Use a dummy node to simplify merging. Compare nodes from both lists, append the smaller one to the result, and advance pointers.
- **Time Complexity**: O(n + m), where `n` and `m` are the lengths of the lists.
- **Space Complexity**: O(1), excluding the output list.
- **Edge Cases**: Handles empty lists or lists of different lengths.

---

## Find the Middle of a Linked List

### Problem
Given a singly linked list, find the middle node. If there are two middle nodes, return the second one. For example, if the list is `1 -> 2 -> 3 -> 4 -> 5`, the middle is `3`.

### Solution
```cpp
ListNode* middleNode(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    return slow;
}
```

### Explanation
- **Approach**: Use the two-pointer technique (slow and fast pointers). The slow pointer moves one step, and the fast pointer moves two steps, so when fast reaches the end, slow is at the middle.
- **Time Complexity**: O(n), single pass through the list.
- **Space Complexity**: O(1), constant space.
- **Edge Cases**: Handles odd and even-length lists, single-node lists.

---

## Remove Nth Node from End of List

### Problem
Given a linked list and an integer `n`, remove the nth node from the end and return the head. For example, if the list is `1 -> 2 -> 3 -> 4 -> 5` and `n = 2`, the result is `1 -> 2 -> 3 -> 5`.

### Solution
```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode dummy(0);
    dummy.next = head;
    ListNode *first = &dummy, *second = &dummy;
    
    // Move first pointer n steps ahead
    for (int i = 0; i < n; i++) {
        first = first->next;
    }
    
    // Move both pointers until first reaches the end
    while (first->next) {
        first = first->next;
        second = second->next;
    }
    
    // Remove the nth node
    second->next = second->next->next;
    return dummy.next;
}
```

### Explanation
- **Approach**: Use two pointers with a gap of `n` nodes. Move both until the first pointer reaches the end, then remove the node after the second pointer.
- **Time Complexity**: O(n), single pass through the list.
- **Space Complexity**: O(1), constant space.
- **Edge Cases**: Handles removal of the head, single-node lists, or `n` equal to list length.

---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/GMohnish11/CPP-LinkedList-Questions.git
   cd CPP-LinkedList-Questions
   ```
2. Compile and run a solution:
   ```bash
   g++ solutions/solution1_reverse_list.cpp -o reverse_list
   ./reverse_list
   ```
3. Use `main.cpp` to test solutions with custom inputs:
   ```cpp
   #include <iostream>
   #include "solutions/solution1_reverse_list.cpp"
   int main() {
       ListNode* head = new ListNode(1);
       head->next = new ListNode(2);
       head->next->next = new ListNode(3);
       head = reverseList(head);
       while (head) {
           std::cout << head->val << " "; // Output: 3 2 1
           head = head->next;
       }
       return 0;
   }
   ```

## Directory Structure
```
├── solutions/
│   ├── solution1_reverse_list.cpp      # Reverse a linked list
│   ├── solution2_detect_cycle.cpp      # Detect and remove cycle
│   ├── solution3_merge_lists.cpp       # Merge two sorted lists
│   ├── solution4_middle_node.cpp       # Find middle of list
│   ├── solution5_remove_nth.cpp        # Remove nth node from end
├── main.cpp                           # Driver code to test solutions
├── cpp_linkedlist_questions.md        # This file
├── README.md                          # Repository overview
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/new-problem`.
3. Add your problem and solution in `solutions/`.
4. Update this Markdown file with the new problem.
5. Commit changes: `git commit -m "Add new linked list problem"`.
6. Push: `git push origin feature/new-problem`.
7. Submit a Pull Request.

Report issues via the [Issues](https://github.com/GMohnish11/CPP-LinkedList-Questions/issues) tab.

## Acknowledgments
- **Author**: Mohnish Gupta
- **Institution**: St. Peter's Engineering College, Hyderabad
- **Inspiration**: Competitive programming platforms like LeetCode, HackerRank, and GeeksforGeeks
- **Resources**: C++ Standard Library and linked list algorithm references