## [用两个栈实现队列](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

题目描述

```txt
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
```

代码

```java
class CQueue {
        private Stack<Integer> stackA;
        private Stack<Integer> stackB;
        public CQueue() {
            stackA = new Stack<>();
            stackB = new Stack<>();
        }

        public void appendTail(int value) {
            stackA.push(value);
        }

        public int deleteHead() {
            if (stackB.isEmpty()){
                if (stackA.isEmpty()){
                    return -1;
                }else{
                    while (!stackA.isEmpty()){
                        stackB.push(stackA.pop());
                    }
                }
            }
            return stackB.pop();
        }
    }
```

