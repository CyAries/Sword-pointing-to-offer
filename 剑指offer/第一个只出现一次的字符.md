## [第一个只出现一次的字符](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

题目

```tex
在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。
```

代码

```java
class Solution {
    public char firstUniqChar(String s) {

        HashMap<Character, Integer> integerHashMap = new LinkedHashMap<>();
        char[] chars = s.toCharArray();
        for (int i = 0; i < chars.length; i++) {
            integerHashMap.put(chars[i], integerHashMap.getOrDefault(chars[i], 0)+1);
        }
        for (Map.Entry<Character, Integer> characterIntegerEntry : integerHashMap.entrySet()) {
            Integer value = characterIntegerEntry.getValue();
            if (value == 1)
                return characterIntegerEntry.getKey();
        }
        //            for (char aChar : chars) {
        //                if (integerHashMap.get(aChar) == 1)
        //                    return aChar;
        //            }
        return ' ';
    }
}
```

