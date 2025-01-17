# Two Sum II

Problem Link : https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order . Find two numbers such that they add up to a specific target number.<br /> Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.
<br />Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.
<br />You may not use the same element twice.


### Example :

Input: numbers = [2,7,11,15], target = 9 <br />
Output: [1,2] <br />
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].


### Using Two pointers

- In Java

```c
public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        HashMap<Integer,Integer> indexMap = new HashMap<Integer,Integer>();
        for(int i = 0; i < numbers.length; i++){
            Integer requiredNum = (Integer)(target - numbers[i]);
            if(indexMap.containsKey(requiredNum)){
                int toReturn[] = {indexMap.get(requiredNum), i};
                return toReturn;
            }

            indexMap.put(numbers[i], i);
        }
        return null;
    }
}
```
- In C++
```c
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int i = 0;
        int j = numbers.size() - 1;
        
        vector<int> result;
        
        while (i < j) {
            int sum = numbers[i] + numbers[j];
            if (sum < target) {
                i++;
            } else if (sum > target) {
                j--;
            } else {
                result.push_back(i + 1);
                result.push_back(j + 1);
                break;
            }
        }
        
        return result;
    }
};
```
### Time Complexity - O(n)
### Space Complexity - O(1)
