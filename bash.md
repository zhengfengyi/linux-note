## 认识和学习bash

1. 命令别名设置功能(alias)：example: alias lm = 'ls -al'.

2. 查询指令是否为bash内建指令： example: type ls (alias) ; type -a ls 

3. **组合键**： ctrl + u  /ctrl + k (从游标处向前/向后删除指令串)；ctrl + a / ctrl + e (游标移动到指令串最开始/末尾)

4. 取消变量： uset  

5. 提示字元设定：PS1=`[\u@\h \w \A #\#]\$`

6. 特殊变量：**$** 本shell 的 PID； **?** 上一个操作的传回值

7. 变量的键盘读取，阵列，宣告：read，array,  declare

   ````
   a.read 读取键盘  -p (接提示符)    -t (等待时间)
   b. declare 定义变量的类型  -a (array)  -i (int) 
   ````

   