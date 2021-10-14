## [两个数组的交集 II](https://leetcode-cn.com/problems/intersection-of-two-arrays-ii/)

题目

```tex
两个数组的交集 II
```

代码

```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) {
            return intersect(nums2,nums1);
        }
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums1.length; i++) {
            int count = map.getOrDefault(nums1[i], 0);
            count++;
            map.put(nums1[i], count);
        }
        int len = 0;
        for (int i = 0; i < nums2.length; i++) {
            int count = map.getOrDefault(nums2[i], 0);
            if (count > 0) {
                nums1[len++] = nums2[i];
                map.put(nums2[i], --count);
            }
        }
        return Arrays.copyOf(nums1, len);
    }
}
```

