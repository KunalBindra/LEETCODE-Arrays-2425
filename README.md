# LEETCODE-Arrays-2425
**Code:**

```java
class Solution {
    public int xorAllNums(int[] nums1, int[] nums2) {
        int n=nums1.length;
        int m=nums2.length;
        int ans=0;
        HashMap<Integer,Integer> mp=new HashMap<>();
        for(int x:nums1) {
            mp.put(x, mp.getOrDefault(x,0)+m);
        } 
        for(int x:nums2) {
            mp.put(x, mp.getOrDefault(x,0)+n);
        }
        for(int num:mp.keySet()) {
            if(mp.get(num)%2!=0) {
                ans^=num;
            }
        }
        return ans;
    }
}
```

**Explanation:**

1. **Initialization:**
   - `n`: Stores the length of the `nums1` array.
   - `m`: Stores the length of the `nums2` array.
   - `ans`: Stores the final XOR result, initialized to 0.
   - `mp`: A HashMap to store the count of occurrences of each number in both arrays.

2. **Count Occurrences in nums1:**
   - Iterate through each number `x` in `nums1`.
   - If `x` exists in the `mp`, increment its count by `m` (length of `nums2`).
   - If `x` doesn't exist in `mp`, add `x` to the map with a count of `m`.

3. **Count Occurrences in nums2:**
   - Iterate through each number `x` in `nums2`.
   - If `x` exists in the `mp`, increment its count by `n` (length of `nums1`).
   - If `x` doesn't exist in `mp`, add `x` to the map with a count of `n`.

4. **Calculate XOR:**
   - Iterate through the keys (numbers) in the `mp`.
   - If the count of a number is odd, XOR the number with the current `ans`.

5. **Return Result:**
   - Return the final `ans` which represents the XOR of all possible pairs.

**Key Idea:**

- The code leverages the property of XOR: 
    - XOR of a number with itself is 0. 
    - XOR is commutative and associative.

- By tracking the count of each number in both arrays, the code efficiently determines which numbers appear an odd number of times in the combined set of all possible pairs.

- XORing only those numbers with odd occurrences results in the final XOR of all possible pairs.

**Example:**

Let's consider:

- `nums1 = [1, 2]`
- `nums2 = [2, 3]`

1. **After processing `nums1`:**
   - `mp = {1: 2, 2: 2}` (1 occurs 2 times, 2 occurs 2 times)

2. **After processing `nums2`:**
   - `mp = {1: 2, 2: 4, 3: 2}` (1 occurs 2 times, 2 occurs 4 times, 3 occurs 2 times)

3. **Calculating XOR:**
   - Only 3 has an odd count (2).
   - `ans = 0 ^ 3 = 3`

Therefore, the XOR of all possible pairs is 3.
