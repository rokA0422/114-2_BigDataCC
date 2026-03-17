
# 第 4 週作業：Linux 常用指令與 Bash Shell 基礎

## 作業資訊

| 項目 | 說明 |
|------|------|
| 對應教科書 | 3-1 Linux 常用命令 |
| 繳交方式 | 在 Fork 的 week04/ 資料夾中建立三個檔案，發 PR 繳交 |
| 繳交期限 | 下週上課前 |
| PR 標題格式 | 學號_姓名_week04 |
| 本週另有 | 小考 1、每人提出 1-3 個專題題目構想（放在 my-topics/ 資料夾） |

---

## 繳交步驟

1. 同步老師的最新版本：到你的 Fork 頁面點「**Sync fork**」>「**Update branch**」
2. 本機拉取最新版：`git pull origin main`
3. 建立作業資料夾：`mkdir week04`
4. 完成以下三題，在 week04/ 中建立三個 txt 檔案
5. Push 到你的 Fork：
   ```bash
   git add week04/
   git commit -m "完成第4週作業"
   git push origin main
   ```
6. 到 GitHub 網頁發 PR，標題：`學號_姓名_week04`

---

## 第 1 題：檔案操作與內容檢視（40 分）

SSH 連線到 AWS Linux 環境，依序完成以下操作，將指令和結果存入 `week04/q1_file_commands.txt`：

```
姓名：温鶴翔
學號：C112181120

=== 任務 1：建立目錄結構 ===
請執行以下指令並貼上結果：
mkdir -p ~/week04/dir1/subdir1
mkdir -p ~/week04/dir2
touch ~/week04/dir1/file1.txt
touch ~/week04/dir1/subdir1/file2.txt
touch ~/week04/dir2/file3.txt
tree ~/week04

（貼上 tree 的輸出結果）

/home/student120/week04
|-- dir1
|   |-- file1.txt
|   `-- subdir1
|       `-- file2.txt
`-- dir2
    `-- file3.txt

3 directories, 3 files
student120@linux-server1:~$


=== 任務 2：寫入檔案內容 ===
請執行以下指令：
echo "Hello Linux" > ~/week04/dir1/file1.txt
echo "Bash Shell Practice" > ~/week04/dir1/subdir1/file2.txt
echo "Week 04 Assignment" > ~/week04/dir2/file3.txt

用 cat 查看三個檔案的內容並貼上結果：
（貼上結果）

student120@linux-server1:~$ echo "Hello Linux" > ~/week04/dir1/file1.txt
student120@linux-server1:~$ echo "Bash Shell Practice" > ~/week04/dir1/subdir1/file2.txt
student120@linux-server1:~$ echo "Week 04 Assignment" > ~/week04/dir2/file3.txt
student120@linux-server1:~$ cat ~/week04/dir1/file1.txt
Hello Linux
student120@linux-server1:~$ cat ~/week04/dir1/subdir1/file2.txt
Bash Shell Practice
student120@linux-server1:~$ cat ~/week04/dir2/file3.txt
Week 04 Assignment


=== 任務 3：檔案內容檢視指令 ===
請執行以下指令並貼上結果：
cat /etc/passwd | head -5
cat /etc/passwd | tail -3
wc -l /etc/passwd

（貼上結果）
```

student120@linux-server1:~$ cat /etc/passwd | head -5
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
student120@linux-server1:~$ cat /etc/passwd | tail -3
student228:x:1059:1059::/home/student228:/bin/bash
student229:x:1060:1060::/home/student229:/bin/bash
student230:x:1061:1061::/home/student230:/bin/bash
student120@linux-server1:~$ wc -l /etc/passwd
82 /etc/passwd


### 評分標準

| 項目 | 配分 |
|------|------|
| 檔案存在且格式正確 | 5 分 |
| 任務 1 目錄結構正確 | 15 分 |
| 任務 2 檔案內容正確 | 10 分 |
| 任務 3 檢視指令結果正確 | 10 分 |

---

## 第 2 題：搜尋、過濾與管線操作（40 分）

完成以下搜尋和管線操作，將結果存入 `week04/q2_grep_pipe.txt`：

```
姓名：温鶴翔
學號：C112181120

=== 任務 1：grep 搜尋 ===
在 /etc/passwd 中搜尋你的帳號名稱：
grep student120 /etc/passwd

（貼上結果）
student120@linux-server1:~$ grep student120 /etc/passwd
student120:x:1019:1019::/home/student120:/bin/bash

搜尋所有包含 "bash" 的行：
grep bash /etc/passwd

（貼上結果）
student120@linux-server1:~$ grep bash /etc/passwd
root:x:0:0:root:/root:/bin/bash
student101:x:1000:1000::/home/student101:/bin/bash
student102:x:1001:1001::/home/student102:/bin/bash
student103:x:1002:1002::/home/student103:/bin/bash
student104:x:1003:1003::/home/student104:/bin/bash
student105:x:1004:1004::/home/student105:/bin/bash
student106:x:1005:1005::/home/student106:/bin/bash
student107:x:1006:1006::/home/student107:/bin/bash
student108:x:1007:1007::/home/student108:/bin/bash
student109:x:1008:1008::/home/student109:/bin/bash
student110:x:1009:1009::/home/student110:/bin/bash
student111:x:1010:1010::/home/student111:/bin/bash
student112:x:1011:1011::/home/student112:/bin/bash
student113:x:1012:1012::/home/student113:/bin/bash
student114:x:1013:1013::/home/student114:/bin/bash
student115:x:1014:1014::/home/student115:/bin/bash
student116:x:1015:1015::/home/student116:/bin/bash
student117:x:1016:1016::/home/student117:/bin/bash
student118:x:1017:1017::/home/student118:/bin/bash
student119:x:1018:1018::/home/student119:/bin/bash
student120:x:1019:1019::/home/student120:/bin/bash
student121:x:1020:1020::/home/student121:/bin/bash
student122:x:1021:1021::/home/student122:/bin/bash
student123:x:1022:1022::/home/student123:/bin/bash
student124:x:1023:1023::/home/student124:/bin/bash
student125:x:1024:1024::/home/student125:/bin/bash
student126:x:1025:1025::/home/student126:/bin/bash
student127:x:1026:1026::/home/student127:/bin/bash
student128:x:1027:1027::/home/student128:/bin/bash
student129:x:1028:1028::/home/student129:/bin/bash
student130:x:1029:1029::/home/student130:/bin/bash
ta01:x:1030:1030::/home/ta01:/bin/bash
ta02:x:1031:1031::/home/ta02:/bin/bash
student201:x:1032:1032::/home/student201:/bin/bash
student202:x:1033:1033::/home/student202:/bin/bash
student203:x:1034:1034::/home/student203:/bin/bash
student204:x:1035:1035::/home/student204:/bin/bash
student205:x:1036:1036::/home/student205:/bin/bash
student206:x:1037:1037::/home/student206:/bin/bash
student207:x:1038:1038::/home/student207:/bin/bash
student208:x:1039:1039::/home/student208:/bin/bash
student209:x:1040:1040::/home/student209:/bin/bash
student210:x:1041:1041::/home/student210:/bin/bash
student211:x:1042:1042::/home/student211:/bin/bash
student212:x:1043:1043::/home/student212:/bin/bash
student213:x:1044:1044::/home/student213:/bin/bash
student214:x:1045:1045::/home/student214:/bin/bash
student215:x:1046:1046::/home/student215:/bin/bash
student216:x:1047:1047::/home/student216:/bin/bash
student217:x:1048:1048::/home/student217:/bin/bash
student218:x:1049:1049::/home/student218:/bin/bash
student219:x:1050:1050::/home/student219:/bin/bash
student220:x:1051:1051::/home/student220:/bin/bash
student221:x:1052:1052::/home/student221:/bin/bash
student222:x:1053:1053::/home/student222:/bin/bash
student223:x:1054:1054::/home/student223:/bin/bash
student224:x:1055:1055::/home/student224:/bin/bash
student225:x:1056:1056::/home/student225:/bin/bash
student226:x:1057:1057::/home/student226:/bin/bash
student227:x:1058:1058::/home/student227:/bin/bash
student228:x:1059:1059::/home/student228:/bin/bash
student229:x:1060:1060::/home/student229:/bin/bash
student230:x:1061:1061::/home/student230:/bin/bash

=== 任務 2：管線操作 ===
列出 /etc 目錄下的檔案數量：
ls /etc | wc -l
student120@linux-server1:~$ ls /etc | wc -l
101

（貼上結果）

列出 /etc 目錄下的前 10 個檔案名稱（按字母排序）：
ls /etc | sort | head -10

（貼上結果）
student120@linux-server1:~$ ls /etc | sort | head -10
adduser.conf
alternatives
apparmor.d
apt
bash.bashrc
bash_completion.d
bindresvport.blacklist
cloud
cron.d
cron.daily

=== 任務 3：重導向 ===
將 ls -la ~ 的結果存入檔案：
ls -la ~ > ~/week04/home_list.txt
cat ~/week04/home_list.txt

（貼上 cat 的結果）
student120@linux-server1:~$ ls -la ~ > ~/week04/home_list.txt
student120@linux-server1:~$ cat ~/week04/home_list.txt
total 52
drwxr-x---. 9 student120 student120 16384 Mar 17 06:52 .
drwxr-xr-x. 1 root       root       16384 Mar 10 03:13 ..
-rw-------. 1 student120 student120   195 Mar 10 08:18 .bash_history
-rw-r--r--. 1 student120 student120   220 Jan  6  2022 .bash_logout
-rw-r--r--. 1 student120 student120  3771 Jan  6  2022 .bashrc
drwx------. 2 student120 student120    34 Mar 10 03:16 .cache
-rw-r--r--. 1 student120 student120   807 Jan  6  2022 .profile
-rw-rw-r--. 1 student120 student120   189 Mar  9 06:50 README.txt
drwxrwxr-x. 2 student120 student120     6 Mar  9 06:50 documents
drwxr-xr-x. 2 student120 student120    83 Mar  9 06:50 exercises
drwxrwxr-x. 2 student120 student120     6 Mar 17 05:58 joe
drwxrwxr-x. 2 student120 student120     6 Mar  9 06:50 projects
drwxrwxr-x. 2 student120 student120     6 Mar  9 06:50 scripts
drwxrwxr-x. 4 student120 student120    51 Mar 17 08:09 week04

將目前日期追加到檔案：
date >> ~/week04/home_list.txt
tail -3 ~/week04/home_list.txt

（貼上 tail 的結果）
```
student120@linux-server1:~$ date >> ~/week04/home_list.txt
student120@linux-server1:~$ tail -3 ~/week04/home_list.txt
drwxrwxr-x. 2 student120 student120     6 Mar  9 06:50 scripts
drwxrwxr-x. 4 student120 student120    51 Mar 17 08:09 week04
Tue Mar 17 08:09:39 UTC 2026

### 評分標準

| 項目 | 配分 |
|------|------|
| 檔案存在且格式正確 | 5 分 |
| 任務 1 grep 搜尋結果正確 | 15 分 |
| 任務 2 管線操作結果正確 | 10 分 |
| 任務 3 重導向操作正確 | 10 分 |

---

## 第 3 題：管線與重導向觀念題（20 分）

回答以下問題，存入 `week04/q3_concepts.txt`：

```
姓名：温鶴翔
學號：C112181120

Q1：請說明管線符號 | 的功能，並舉一個實際使用的例子。
A1：
功能： 管線符號用於將前一個指令的標準輸出（Standard Output），直接串接到下一個指令的標準輸入（Standard Input）。它讓資料在程序之間流動處理，而不需要產生中間暫存檔。

實際例子： ls -l | grep ".py"

說明： 先用 ls -l 列出詳細檔案清單，再透過管線交給 grep 篩選出所有副檔名為 .py 的檔案。

Q2：請說明 > 和 >> 的差異，各舉一個使用情境。
A2：
差異：

> (重導向輸出)：會覆蓋目標檔案的內容。如果檔案不存在則建立新檔；若已存在則先清空再寫入。

>> (附加輸出)：會將內容**新增（Append）**到目標檔案的末尾。不會刪除原有的資料。

使用情境：

使用 >： 每天產生一份「最新的」伺服器狀態報告，例如 top -b -n 1 > daily_report.txt。

使用 >>： 持續記錄系統的錯誤日誌（Log），例如 echo "Error at 12:00" >> system.log，確保之前的紀錄不會消失。

Q3：請寫出一行指令，找出 /etc/passwd 中有多少個使用者的 shell 是 /bin/bash。
A3：
Bash
grep "/bin/bash" /etc/passwd | wc -l
指令解析：

grep "/bin/bash" /etc/passwd：從使用者帳號檔案中找出所有包含 /bin/bash 的行。

|：將這些行傳送給下一個指令。

wc -l：統計收到的總行數，即為符合條件的使用者數量。

Bash
grep "/bin/bash" /etc/passwd | wc -l

### 評分標準

| 項目 | 配分 |
|------|------|
| Q1 正確說明管線功能並舉例 | 7 分 |
| Q2 正確說明 > 和 >> 差異 | 7 分 |
| Q3 指令正確 | 6 分 |

---

## 繳交 Checklist

- [ ] week04/q1_file_commands.txt 包含三個任務的完整結果
- [ ] week04/q2_grep_pipe.txt 包含搜尋、管線、重導向的結果
- [ ] week04/q3_concepts.txt 包含三題觀念回答
- [ ] 已 push 到自己的 Fork
- [ ] 已發 PR，標題格式：學號_姓名_week04

---

## 專題題目構想（本週另外繳交）

請在你的 Fork 中建立 `my-topics/` 資料夾，提出 1-3 個你有興趣的海事海洋相關題目。每個題目建立一個 markdown 檔案：

```
my-topics/
├── topic1_你的題目名稱.md
├── topic2_你的題目名稱.md
└── topic3_你的題目名稱.md
```

每個檔案需包含：
- 題目名稱
- 為什麼對這個題目有興趣（50 字以上）
- 可能使用的資料來源
- 預計使用的技術

題目構想可以跟 week04 作業一起 push，也可以分開發 PR。

---

## 常見問題

**Q：tree 指令找不到？**
先安裝：`sudo apt install -y tree`

**Q：grep 搜尋時沒有結果？**
確認搜尋的關鍵字拼寫正確。grep 區分大小寫，如需忽略大小寫可加 -i 參數：`grep -i keyword file`

**Q：重導向 > 寫入後檔案是空的？**
確認指令語法正確，> 前面要有輸出結果的指令。例如 `ls > file.txt` 而非 `> file.txt ls`

**Q：專題題目構想不知道寫什麼？**
參考課程 Repo README 中的「專題題目參考」清單，從海洋資料分析、海事 AI 應用、海事整合應用三個方向選擇或延伸。
