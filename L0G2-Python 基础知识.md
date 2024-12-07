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



## 任务二 Vscode连接InternStudio debug笔记

### Conda虚拟环境
#### 1、创建新环境

![image](https://github.com/user-attachments/assets/fabf82e6-8b95-4c02-8f5b-ffe9219754d8)

#### 2、管理环境

激活环境：
![image](https://github.com/user-attachments/assets/e8deb583-d6b8-443e-9cc6-dab274fbdc56)

退出环境：
conda deactivate

其他环境命令：

#查看当前设备上所有的虚拟环境
conda env list

#查看当前环境中安装了的所有包
conda list

#删除环境（比如要删除myenv）
conda env remove myenv

#### 3、安装虚拟环境到指定目录

如想在/root/envs/路径下创建刚刚我们创建过得myenv

conda create --prefix /root/envs/myenv python=3.9

激活保存在制定目录下的conda虚拟环境

conda activate /root/envs/myenv

### 使用pip安装Python三方依赖包

#### 1、使用pip安装包

pip install <somepackage> # 安装单个包，<somepackage>替换成你要安装的包名

pip install pandas numpy # 安装多个包，如panda和numpy

pip install numpy==2.0 # 指定版本安装

pip install numpy>=1.19,<2.0 # 使用版本范围安装


#### 2、安装requirement.txt

如果你有一个包含所有依赖信息的requirements.txt文件，可以使用-r一次性安装所有依赖。

pip install -r requirements.txt

#### 3、安装到指定目录

![image](https://github.com/user-attachments/assets/24c8bceb-1c77-4f9c-ab9a-9f0598fb00f2)

首先激活环境

conda activate /root/share/pre_envs/pytorch2.1.2cu12.1

创建一个目录/root/myenvs，并将包安装到这个目录下

mkdir -p /root/myenvs

pip install (somepackage) --target /root/myenvs

注意这里也可以使用-r来安装requirements.txt

pip install -r requirements.txt --target /root/myenvs

