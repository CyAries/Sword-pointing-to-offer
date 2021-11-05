## [Day10-最长不含重复字符的子字符串](https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

题目

```tex
请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。
```

代码

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        char[] chars = s.toCharArray();
        Set<Character> set = new HashSet<>();
        int max = 0,right = 0;
        for (int i = 0; i < chars.length; i++) {
            if (i!=0){
                set.remove(chars[i-1]);
            }
            int j = right;
            for (; j < chars.length; j++) {
                if (!set.contains(chars[j])){
                    set.add(chars[j]);
                }else{
                    break;
                }
            }
            right = j;
            max = Math.max(right-i, max);
        }
        return max;
    }
    // 重新寫了一遍
    public int lengthOfLongestSubstring1(String s) {
        if (s == null||s.length() == 0)
            return 0;
        int max = 0,right = 0;
        char[] chars = s.toCharArray();
        Set<Character> set = new HashSet<>();
        for (int i = 0; i < chars.length; i++) {
            if (i!=0)
                set.remove(chars[i-1]);
            while(right<chars.length){
                if (!set.contains(chars[right])){
                    set.add(chars[right]);
                    right++;
                }else{
                    break;
                }
            }
            if (right-i>max)
                max = right-i;
        }
        return max;
    }
}
```

