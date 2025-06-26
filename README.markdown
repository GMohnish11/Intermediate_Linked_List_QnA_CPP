# CPP-LinkedList-Questions

## Overview
This repository, `CPP-LinkedList-Questions`, contains a collection of intermediate-level linked list problems and their solutions in C++, developed by Mohnish Gupta. Designed for coding interview preparation and competitive programming, it includes problems like reversing a linked list, detecting cycles, and merging sorted lists, with detailed explanations and efficient C++ code. Ideal for mastering linked list operations.

## Description
A collection of intermediate C++ linked list problems with solutions, including reversal, cycle detection, and merging lists. Ideal for coding practice and interviews, by Mohnish Gupta.

## Features
- **Intermediate Problems**: Covers linked list techniques like reversal, cycle detection, merging, and node manipulation.
- **C++ Solutions**: Efficient, well-commented code using modern C++ (e.g., pointer operations, `struct ListNode`).
- **Explanations**: Each problem includes a description, solution, time/space complexity, and edge case analysis in `cpp_linkedlist_questions.md`.
- **Testable Code**: Includes a `main.cpp` driver file to test solutions with custom inputs.
- **Modular Design**: Solutions are organized in `solutions/` for easy integration and testing.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/GMohnish11/CPP-LinkedList-Questions.git
   cd CPP-LinkedList-Questions
   ```
2. **Ensure C++ Compiler**:
   - Install a C++ compiler (e.g., `g++` via GCC) if not already present.
   - Verify: `g++ --version`.
3. **Compile and Run**:
   - Compile a specific solution:
     ```bash
     g++ solutions/solution1_reverse_list.cpp -o reverse_list
     ./reverse_list
     ```
   - Or use `main.cpp` to test all solutions:
     ```bash
     g++ main.cpp -o test
     ./test
     ```

## Usage
### Exploring Problems
- Read `cpp_linkedlist_questions.md` for problem descriptions, solutions, and explanations.
- Problems include:
  1. Reverse a Linked List
  2. Detect and Remove Cycle in a Linked List
  3. Merge Two Sorted Linked Lists
  4. Find the Middle of a Linked List
  5. Remove Nth Node from End of List

### Running Solutions
- Each solution is in the `solutions/` directory (e.g., `solution1_reverse_list.cpp`).
- Modify `main.cpp` to test different inputs:
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
- Compile and run as shown in the Installation section.

## Directory Structure
```
├── solutions/
│   ├── solution1_reverse_list.cpp      # Reverse a linked list
│   ├── solution2_detect_cycle.cpp      # Detect and remove cycle
│   ├── solution3_merge_lists.cpp       # Merge two sorted lists
│   ├── solution4_middle_node.cpp       # Find middle of list
│   ├── solution5_remove_nth.cpp        # Remove nth node from end
├── main.cpp                           # Driver code to test solutions
├── cpp_linkedlist_questions.md        # Problem descriptions and solutions
├── README.md                          # This file
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/new-problem`.
3. Add your problem and solution in `solutions/` and update `cpp_linkedlist_questions.md`.
4. Commit changes: `git commit -m "Add new linked list problem"`.
5. Push: `git push origin feature/new-problem`.
6. Submit a Pull Request.

Report issues via the [Issues](https://github.com/GMohnish11/CPP-LinkedList-Questions/issues) tab.

## Acknowledgments
- **Author**: Mohnish Gupta
- **Institution**: St. Peter's Engineering College, Hyderabad
- **Inspiration**: Competitive programming platforms like LeetCode, HackerRank, and GeeksforGeeks
- **Resources**: C++ Standard Library and linked list algorithm references