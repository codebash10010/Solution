⚙️ 
�� Find the Duplicate Number 
Given an array of integers`nums`containing n + 1 integers where each integer is in the range [1, n] inclusive. There is only one repeated number in`nums`, return this repeated number. You must solve the problem without modifying the array nums and using only constant extra space. 
�� Input and Output Explained: 
Input (`nums`): An array of integers where its length is`n+1`and all integers are within the range`[1, n]`. There is exactly one number that appears more than once. 
Output: The single integer that is repeated in the array. The solution must not modify the input array and must use only constant extra space. 
✅ Examples: 
Example 1: 
Input: nums = [1, 3, 4, 2, 2] 
Output: 2 
Explanation: You are given numbers from 1 to 4 (because length is 5). But here, you see that 2 is written two times. All other numbers (1, 3, 4) appear only once. So, the duplicate number is 2. 
Example 2: 
Input: nums = [3, 1, 3, 4, 2] 
Output: 3 
Explanation: Again, numbers should be from 1 to 4 (length is 5). But 3 is coming two times — once at the start, once at index 2. Thats the only number repeating, so the answer is 3. 
Example 3: 
Input: nums = [3, 3, 3, 3, 3] 
Output: 3 
Explanation: All numbers are 3 — so 3 is clearly repeated multiple times. Even though other numbers (1, 2, 4) are missing, the only duplicate here is 3. So, the answer is 3. 
Constraints: 
The array`nums`contains`n + 1` integers. 
Each integer in`nums` is in the range`[1, n]` inclusive. 
There is only one repeated number in`nums`. 
You must solve the problem without modifying the array`nums`. 
You must use only constant extra space. 
�� Approach: Floyd's Cycle Detection (Tortoise and Hare) 
This problem can be cleverly solved using Floyd's Cycle Detection Algorithm, also known as the Tortoise and Hare algorithm. The array can be thought of as a linked list where each number`i`points to`nums[i]`. Since there is a duplicate number and the numbers are within a specific range, this forms a cycle in the "linked list". 
Phase 1 (Finding the Intersection Point): Initialize two pointers,`slow`and `fast`, both starting at `nums[0]`. In each step,`slow`moves one step (`slow = nums[slow]`) and `fast`moves two steps (`fast = nums[nums[fast]]`). They are guaranteed to meet at some point if a cycle exists. 
Phase 2 (Finding the Cycle Entry Point): Once`slow`and `fast`meet, reset `fast` to `nums[0]`. Move both `slow`and `fast`one step at a time until they meet again. The point where they meet is the entry point of the cycle, which is the duplicate number. 

Time Complexity: 
$O(n)$ 
�� Code Solutions: 
C++ Code: 
#include <iostream> 
#include <vector> 
using namespace std; 
class Solution { 
public: 
 int findDuplicate(vector<int>& nums) {  int slow = nums[0]; 
 int fast = nums[0]; 
  
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
 cout << "Enter number of elements: ";  cin >> n; 
 vector<int> nums(n); 
 cout << "Enter the elements:\\n"; 
 for (int i = 0; i < n; ++i) cin >> nums[i];  Solution sol; 
Space Complexity: $O(1)$ extra space 

 cout << "Duplicate Number: " << sol.findDuplicate(nums) << endl; 
 return 0; 
} 
Java Code: 
import java.util.Scanner; 
public class Solution { 
 public int findDuplicate(int[] nums) { 
 int slow = nums[0]; 
 int fast = nums[0]; 
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
 System.out.println("Duplicate Number: " + sol.findDuplicate(nums));  } 
} 
``` 
  
Python Code: 
class Solution: 
 def findDuplicate(self, nums): 
 slow = nums[0] 
 fast = nums[0] 
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
# Driver Code 
if __name__ == "__main__": 
 n = int(input("Enter number of elements: ")) 
 nums = list(map(int, input("Enter the elements: ").split()))  sol = Solution() 
 print("Duplicate Number:", sol.findDuplicate(nums)) 
``` 
  
JavaScript Code: 
function findDuplicate(nums) { 
 let slow = nums[0]; 
 let fast = nums[0]; 
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
// Driver Code 
const readline = require("readline").createInterface({ 
 input: process.stdin, 
 output: process.stdout, 
}); 
readline.question("Enter number of elements: ", (n) => { 
 readline.question("Enter the elements (space separated): ", (input) => {  const nums = input.split(" ").map(Number); 
 console.log("Duplicate Number:", findDuplicate(nums));  readline.close(); 
 }); 
}); 
```
