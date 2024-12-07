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

### 使用本地Vscode连接InternStudio开发机

![image](https://github.com/user-attachments/assets/2bf804c7-447f-4b50-bd12-ad198b169309)

### 使用vscode连接开发机进行python debug

#### 1、什么是debug

简单来说，“debug”就是能再程序中设置中断点并支持一行一行地运行代码，观测程序中变量的变化，然后找出并修正代码中的错误

#### 2、使用Vscode进行Python debug的流程

创建一个py_debug.py的文件

![image](https://github.com/user-attachments/assets/5454373f-7e59-4fa6-a8eb-df9279fed4ba)

生成的launch.json文件

![image](https://github.com/user-attachments/assets/81386a47-5d87-48bf-88b4-4dd0b6349212)

设置断点

![image](https://github.com/user-attachments/assets/5df1cc00-7a80-48cb-a1ee-5eb2fa493571)

查看变量

![image](https://github.com/user-attachments/assets/a2df8eef-2f61-4d11-adb6-e5a2cb631875)

单步执行

![image](https://github.com/user-attachments/assets/88980130-dd6d-44f3-9d29-ef6a20d2bb20)

表达式断点

![image](https://github.com/user-attachments/assets/5e9c4b61-be91-4694-9956-01a71ef71469)

命中次数断点

![image](https://github.com/user-attachments/assets/9e4323ef-dec8-43a0-97f8-e6f929fd86cd)

日志消息断点

![image](https://github.com/user-attachments/assets/ec863b9f-93c0-4acc-a301-3dfbe8a2b633)
![image](https://github.com/user-attachments/assets/1903895c-8e94-465e-8ac5-fb507194426b)

#### 3、在vscode使用命令行进行debug

![image](https://github.com/user-attachments/assets/a0bc23dc-2549-4927-a5c2-e01097a6b7ad)

#### 4、使用别名简化命令

![image](https://github.com/user-attachments/assets/36f42b45-71c5-47aa-8140-ae29b557045e)
![image](https://github.com/user-attachments/assets/4e00d782-2398-444a-8dfd-da1b62aa11e4)

### Python调用InternLM api

![image](https://github.com/user-attachments/assets/25f739e9-0c3c-4f33-869c-d12cfd972c24)


## 任务三 通过debug功能定位到报错原因

首先增加 os 模块，用环境变量获取 api_key

![image](https://github.com/user-attachments/assets/54d220d6-9f90-4abd-ae4f-be7ca31441ba)
![image](https://github.com/user-attachments/assets/176c798f-876b-4db4-b57a-d7436c9591bd)

在res_json前设置断点，查看返回结果，显示结果发生异常: JSONDecodeError

![image](https://github.com/user-attachments/assets/2e2c36ec-9840-4b04-b7fb-3c1581863e1e)

res返回值不是json格式

修改代码为如下，可正常运行

![image](https://github.com/user-attachments/assets/a3c0fc02-6099-4d16-8d84-3b6910054d60)

![image](https://github.com/user-attachments/assets/d545f2f2-78a8-4c38-93e5-ff789873fca2)

另一种修改代码方式，可能更科学

![image](https://github.com/user-attachments/assets/a63d30df-9244-4d8b-8a2c-45a89373026c)





