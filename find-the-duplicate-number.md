# Find the Duplicate Number - Multiple Language Implementations

This repository contains solutions for the "Find the Duplicate Number" problem implemented in **C++**, **Java**, **Python**, and **JavaScript** using Floyd's Tortoise and Hare (Cycle Detection) algorithm.

---

## 📝 Problem Statement

Given an array `nums` containing `n + 1` integers where each integer is between `1` and `n` (inclusive), there is only one repeated number. Return this repeated number.

You must solve the problem without modifying the array and using only constant extra space.

---

## 📌 Implementations

### **C++**
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int slow = nums[0], fast = nums[0];
        // Phase 1
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);
        // Phase 2
        fast = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
};

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;
    vector<int> nums(n);
    cout << "Enter the elements:\n";
    for (int i = 0; i < n; ++i) cin >> nums[i];
    Solution sol;
    cout << "Duplicate Number: " << sol.findDuplicate(nums) << endl;
    return 0;
}
```

---

### **Java**
```java
import java.util.Scanner;

public class Solution {
    public int findDuplicate(int[] nums) {
        int slow = nums[0], fast = nums[0];
        // Phase 1
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);
        // Phase 2
        fast = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        int[] nums = new int[n];
        System.out.println("Enter the elements:");
        for (int i = 0; i < n; ++i) nums[i] = sc.nextInt();
        Solution sol = new Solution();
        System.out.println("Duplicate Number: " + sol.findDuplicate(nums));
    }
}
```

---

### **Python**
```python
class Solution:
    def findDuplicate(self, nums):
        slow, fast = nums[0], nums[0]
        # Phase 1
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
        # Phase 2
        fast = nums[0]
        while slow != fast:
            slow = nums[slow]
            fast = nums[fast]
        return slow

# Driver code
if __name__ == "__main__":
    n = int(input("Enter number of elements: "))
    nums = list(map(int, input("Enter the elements: ").split()))
    sol = Solution()
    print("Duplicate Number:", sol.findDuplicate(nums))
```

---

### **JavaScript**
```javascript
function findDuplicate(nums) {
    let slow = nums[0], fast = nums[0];
    // Phase 1
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow !== fast);
    // Phase 2
    fast = nums[0];
    while (slow !== fast) {
        slow = nums[slow];
        fast = nums[fast];
    }
    return slow;
}

// Driver code
const readline = require("readline").createInterface({
    input: process.stdin,
    output: process.stdout,
});

readline.question("Enter number of elements: ", (n) => {
    readline.question("Enter the elements (space separated): ", (input) => {
        const nums = input.split(" ").map(Number);
        console.log("Duplicate Number:", findDuplicate(nums));
        readline.close();
    });
});
```

---

## 🚀 How to Run

### **C++**
```bash
g++ solution.cpp -o solution
./solution
```

### **Java**
```bash
javac Solution.java
java Solution
```

### **Python**
```bash
python solution.py
```

### **JavaScript**
```bash
node solution.js
```

---

## 📚 Algorithm Used
We use **Floyd's Tortoise and Hare Algorithm**:
1. **Phase 1:** Detect intersection point inside the cycle.
2. **Phase 2:** Find the entrance to the cycle (duplicate number).

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)`

---
