## [II. 队列的最大值](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/)

题目

```tex
请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1
```

代码

```java
class MaxQueue {
        Deque<Integer> deque;
        Queue<Integer> queue;
        public MaxQueue() {
            deque = new LinkedList<>();
            queue = new LinkedList<>();
        }

        public int max_value() {
            if (deque.peekFirst()==null)
                return -1;
            return deque.peekFirst();
        }

        public void push_back(int value) {
            while(!deque.isEmpty()&&deque.peekLast()<value){
                deque.pollLast();
            }
            deque.offerLast(value);
            queue.offer(value);
        }

        public int pop_front() {
            if (queue.isEmpty()){
                return -1;
            }
            int ans = queue.poll();
            if (deque.peekFirst() == ans)
                deque.pollFirst();
            return ans;
        }
    }
```



