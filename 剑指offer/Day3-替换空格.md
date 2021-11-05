## [替换空格](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

题目

```tex
请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。
```

代码

```java
class Solution {
    public String replaceSpace(String s) {
        char[] chars = s.toCharArray();
        int len = chars.length;
        for (int i = 0; i < chars.length; i++) {
            if (chars[i] == ' ')
                len=len+2;
        }
        char[] newChars = new char[len];
        len = 0;
        for (int i = 0; i < chars.length; i++) {
            if (chars[i] != ' ') {
                newChars[len++] = chars[i];
            }else{
                newChars[len++] = '%';
                newChars[len++] = '2';
                newChars[len++] = '0';
            }
        }
        return new String(newChars);
    }
}
```

