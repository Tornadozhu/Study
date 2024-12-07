# L0G2-Python 基础知识

## 任务一 完成Leetcode 383

题目：给你两个字符串：ransomNote 和 magazine ，判断 ransomNote 能不能由 magazine 里面的字符构成。如果可以，返回 true ；否则返回 false 。magazine 中的每个字符只能在 ransomNote 中使用一次。

```class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        n = list(magazine)
        m = list(ransomNote)
        for i in range(0,len(n)):
            if n[i] in m:
                m.remove(n[i])
        if len(m) == 0:
            return True
        else:
            return False
```
![image](https://github.com/user-attachments/assets/f3b9d9c3-236b-4bd8-b17d-826d9f62ae88)
