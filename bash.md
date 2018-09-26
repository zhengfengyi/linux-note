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


8. 终端的环境设置： stty 

9. 1> ：以覆蓋的方法將『正確的資料』輸出到指定的檔案或裝置上；

10. 1>>：以累加的方法將『正確的資料』輸出到指定的檔案或裝置上；

11. 2> ：以覆蓋的方法將『錯誤的資料』輸出到指定的檔案或裝置上；

12. 2>>：以累加的方法將『錯誤的資料』輸出到指定的檔案或裝置上；

13. ```
     find /home -name .bashrc > list_right 2> list_error
    ```

14. ```
    find /home -name .bashrc > list 2>&1     <==正確
    ```

15. 截取命令： cut; grep ;  example cut : echo ${PATH} | cut -d ":" -f 1  ;     export | cut -c 12-20 ;

16. ```
    grep 
    -a ：將 binary 檔案以 text 檔案的方式搜尋資料
    -c ：計算找到 '搜尋字串' 的次數
    -i ：忽略大小寫的不同，所以大小寫視為相同
    -n ：順便輸出行號
    -v ：反向選擇，亦即顯示出沒有 '搜尋字串' 內容的那一行！
    --color=auto ：可以將找到的關鍵字部分加上顏色的顯示喔！
    ```

1. unlimit ： unlimit -a (列出所有限制)
2. 命令别名设置： alias  example： alias rm="rm -i"   取消别名： unalias rm
3. 历史命令： history ； 执行上一条命令：【 !! 】;  执行最近以“al”开头的命令 【!al】
4. bash的环境设定档：/etc/profile => ~/.bash_profile || => ~/.bash_login => ~/.profile;