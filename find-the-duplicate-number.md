# 🧩 Find the Duplicate Number

**Problem Statement:**  
Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only one repeated number in `nums`. Return this repeated number.  
You must solve the problem **without modifying the array** and using **only constant extra space**.

---

## 📝 Input & Output

**Input:**  
- `nums`: An array of integers of length `n + 1` where all integers are within `[1, n]`.
- Exactly one integer appears more than once.

**Output:**  
- The single repeated integer.

---

## ✅ Examples

**Example 1:**
Input: nums = [1, 3, 4, 2, 2]
Output: 2

Explanation: Numbers are from 1 to 4. `2` appears twice.

**Example 2:**
Input: nums = [3, 1, 3, 4, 2]
Output: 3

Explanation: `3` appears twice.

**Example 3:**
Input: nums = [3, 3, 3, 3, 3]
Output: 3

Explanation: All elements are `3`.

---


---

## ⚙ Constraints
- Array length: `n + 1`
- Elements: `[1, n]`
- Only **one** repeated number
- No array modification
- **O(1)** extra space

---

## 💡 Approach – Floyd's Cycle Detection (Tortoise and Hare)
- Treat the array as a linked list where `nums[i]` points to `nums[nums[i]]`.
- Phase 1: Use two pointers (`slow`, `fast`) moving at different speeds to find an intersection.
- Phase 2: Reset `fast` to `nums[0]` and move both one step at a time until they meet again — the meeting point is the duplicate number.

**Time Complexity:** O(n)  
**Space Complexity:** O(1)

---

## 💻 Code Implementations with Driver Code

### C++

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

### Java
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

### Pyhton 
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

### JavaScript

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


📎 Related
Category: DSA → Arrays → Cycle Detection

Difficulty: Medium


⭐ If you find this project useful, don’t forget to star it!

---

If you want, I can also make this README **more visual with badges, table of contents, and clickable category links** so it looks like a polished open-source project on GitHub.  
Do you want me to upgrade it with that professional touch?
