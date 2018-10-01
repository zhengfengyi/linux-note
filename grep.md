## 正则表达和文件格式化处理

#### 1.grep：

````
a:设置颜色    grep -n --color=auto
b: -A ：後面可加數字，為 after 的意思，除了列出該行外，後續的 n 行也列出來；
   -B ：後面可加數字，為 befer 的意思，除了列出該行外，前面的 n 行也列出來；
c:反向选择：grep -vn 'the' 
d:无论大小写：grep -in 'the'
e:利用中括號 [] 來搜尋集合字元   grep -n 't[ae]st
f:如果我不想要 oo 前面有 g 的話呢  grep -n '[^g]oo' 
g:行首與行尾字元 ^ $: grep -n '^the' regular_express.txt; 
h:grep -v '^$' /etc/rsyslog.conf | grep -v '^#'
# 結果僅有 14 行，其中第一個『 -v '^$' 』代表『不要空白行』，
# 第二個『 -v '^#' 』代表『不要開頭是 # 的那行』喔！
i: . (小數點)：代表『一定有一個任意字元』的意思
j: * (星星號)：代表『重複前一個字元， 0 到無窮多次』的意思，為組合形態
h: {} 限定范围 ：grep -n 'o\{2\}' regular_express.txt
````

#### 2.正则表达

| 符号      | 意思                                         |
| --------- | -------------------------------------------- |
| [:alnum:] | 代表英文大小寫字元及數字，亦即 0-9, A-Z, a-z |
| [:alpha:] | 代表任何英文大小寫字元，亦即 A-Z, a-z        |
| [:upper:] | 代表大寫字元，亦即 A-Z                       |
| [:lower:] | 代表小寫字元，亦即 a-z                       |
| [:digit:] | 代表數字而已，亦即 0-9                       |

#### 3.sed工具

````
a: sed "2,5d" 删除要输出的2 到 5 行
b: sed "2a hello world" 在输出的第二行后面一行 加上 hello world
c: sed "2,5c No 2-5 number" 在输出的第二行和第五行 变为 No 2-5 number
d: sed -n(安静模式) '2,6p' 指输出2-6行
````

#### 4.awk

```
 last -n 5 | awk '{print $1 "\t" $3}'
 
last -n 5 | awk '{print $1 "\t lines:" NR "\t columns:" NF}'

比较大下计算功能
```

| 變數名稱 | 代表意義                          |
| -------- | --------------------------------- |
| NF       | 每一行 ($0) 擁有的欄位總數        |
| NR       | 目前 awk 所處理的是『第幾行』資料 |
| FS       | 目前的分隔字元，預設是空白鍵      |

#### 5.diff

用法：  diff [-bBi] from-file to-file

```
-b  ：忽略一行當中，僅有多個空白的差異(例如 "about me" 與 "about     me" 視為相同
-B  ：忽略空白行的差異。
-i  ：忽略大小寫的不同。
```

#### 6.cmp

```
cmp [-l] file1 file2
```

#### 7.patch 更新

```go
 diff -Naur passwd.old passwd.new > passwd.patch
```

#### 8.檔案列印準備： pr

```
pr /etc/man_db.conf
```