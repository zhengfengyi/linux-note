## 学习Shell Script

#### 1.必须要以[ #!/bin/bash ] 开头，表示使用的语法为 bash 的语法；

#### 2.一般来说建议在开始写上 ：1.内容与功能； 2.版本资讯； 3.作者和联络方式  4. 建档案日期； 5. 历史记录

#### 3.test 指令的测试功能

| 測試的標誌                                                   | 代表意義                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. 關於某個檔名的『檔案類型』判斷，如 test -e filename 表示存在否 |                                                              |
| -e                                                           | 該『檔名』是否存在？(常用)                                   |
| -f                                                           | 該『檔名』是否存在且為檔案(file)？(常用)                     |
| -d                                                           | 該『檔名』是否存在且為目錄(directory)？(常用)                |
| -b                                                           | 該『檔名』是否存在且為一個 block device 裝置？               |
| -c                                                           | 該『檔名』是否存在且為一個 character device 裝置？           |
| -S                                                           | 該『檔名』是否存在且為一個 Socket 檔案？                     |
| -p                                                           | 該『檔名』是否存在且為一個 FIFO (pipe) 檔案？                |
| -L                                                           | 該『檔名』是否存在且為一個連結檔？                           |
| 2. 關於檔案的權限偵測，如 test -r filename 表示可讀否 (但 root 權限常有例外) |                                                              |
| -r                                                           | 偵測該檔名是否存在且具有『可讀』的權限？                     |
| -w                                                           | 偵測該檔名是否存在且具有『可寫』的權限？                     |
| -x                                                           | 偵測該檔名是否存在且具有『可執行』的權限？                   |
| -u                                                           | 偵測該檔名是否存在且具有『SUID』的屬性？                     |
| -g                                                           | 偵測該檔名是否存在且具有『SGID』的屬性？                     |
| -k                                                           | 偵測該檔名是否存在且具有『Sticky bit』的屬性？               |
| -s                                                           | 偵測該檔名是否存在且為『非空白檔案』？                       |
| 3. 兩個檔案之間的比較，如： test file1 -nt file2             |                                                              |
| -nt                                                          | (newer than)判斷 file1 是否比 file2 新                       |
| -ot                                                          | (older than)判斷 file1 是否比 file2 舊                       |
| -ef                                                          | 判斷 file1 與 file2 是否為同一檔案，可用在判斷 hard link 的判定上。 主要意義在判定，兩個檔案是否均指向同一個 inode 哩！ |
| 4. 關於兩個整數之間的判定，例如 test n1 -eq n2               |                                                              |
| -eq                                                          | 兩數值相等 (equal)                                           |
| -ne                                                          | 兩數值不等 (not equal)                                       |
| -gt                                                          | n1 大於 n2 (greater than)                                    |
| -lt                                                          | n1 小於 n2 (less than)                                       |
| -ge                                                          | n1 大於等於 n2 (greater than or equal)                       |
| -le                                                          | n1 小於等於 n2 (less than or equal)                          |
| 5. 判定字串的資料                                            |                                                              |
| test -z string                                               | 判定字串是否為 0 ？若 string 為空字串，則為 true             |
| test -n string                                               | 判定字串是否非為 0 ？若 string 為空字串，則為 false。 註： -n 亦可省略 |
| test str1 == str2                                            | 判定 str1 是否等於 str2 ，若相等，則回傳 true                |
| test str1 != str2                                            | 判定 str1 是否不等於 str2 ，若相等，則回傳 false             |
| 6. 多重條件判定，例如： test -r filename -a -x filename      |                                                              |
| -a                                                           | (and)兩狀況同時成立！例如 test -r file -a -x file，則 file 同時具有 r 與 x 權限時，才回傳 true。 |
| -o                                                           | (or)兩狀況任何一個成立！例如 test -r file -o -x file，則 file 具有 r 或 x 權限時，就可回傳 true。 |
| !                                                            | 反相狀態，如 test ! -x file ，當 file 不具有 x 時，回傳 true |

#### 4. **判断符号 [ ] 符号两边必须有空格**

#### 5. $#(参数总数)  $@(每个参数列出)  $*（每个参数列出） $1 第一个参数  shift 接数字 （跳脱几个参数）

#### 6. if [判断条件];  then  fi      if [  ]; then  elif; then  else fi              

#### 7.

```
case  $變數名稱 in   <==關鍵字為 case ，還有變數前有錢字號
  "第一個變數內容")   <==每個變數內容建議用雙引號括起來，關鍵字則為小括號 )
	程式段
	;;            <==每個類別結尾使用兩個連續的分號來處理！
  "第二個變數內容")
	程式段
	;;
  *)                  <==最後一個變數內容都會用 * 來代表所有其他值
	不包含第一個變數內容與第二個變數內容的其他程式執行段
	exit 1
	;;
esac              
```

#### 8.

```
`function fname() { 	程式段 }`
```

#### 9.循环

```
`while [ condition ]  <==中括號內的狀態就是判斷式 do            <==do 是迴圈的開始！ 	程式段落 done          <==done 是迴圈的結束`
```

#### 10.随机

```
`[dmtsai@study bin]$ vim what_to_eat.sh #!/bin/bash # Program: # 	Try do tell you what you may eat. # History: # 2015/07/17	VBird	First release PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin export PATH  eat[1]="賣噹噹漢堡"       # 寫下你所收集到的店家！ eat[2]="肯爺爺炸雞" eat[3]="彩虹日式便當" eat[4]="越油越好吃大雅" eat[5]="想不出吃啥學餐" eat[6]="太師父便當" eat[7]="池上便當" eat[8]="懷念火車便當" eat[9]="一起吃泡麵" eatnum=9                  # 需要輸入有幾個可用的餐廳數！  check=$(( ${RANDOM} * ${eatnum} / 32767 + 1 )) echo "your may eat ${eat[${check}]}"`
```

#### 11.shell script 追踪 debug

```
 sh [-nvx] scripts.sh
```