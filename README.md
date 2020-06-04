# git_note
A repository for learning GIT
# **VCS (Version Control System)**

**Định nghĩa:**
 + Hệ thống quản lý phiên bản là hệ thống ghi nhận và lưu lại sự thay đổi của các file theo thời gian. Nhờ đó 1 file có thể quay về trạng thái của nó tại một thời điểm trước đó.

**Phân loại**:
+ Cục bộ (Local Computer):

  ![alt text](https://git-scm.com/figures/18333fig0101-tn.png)

+ Trung tâm:

  ![alt text](https://git-scm.com/book/en/v2/images/centralized.png)

+ Phân tán:

  ![alt text](https://git-scm.com/book/en/v2/images/distributed.png)

# **GIT**

GIT là hệ thống quản lý phiên bản phân tán (DVCS) với ưu điểm: tốc độ, đơn giản, phân tán, phù hợp với dự án lớn và nhỏ.

Cách lưu dữ liệu của GIT :

  + GIT lưu dũ liệu dưới dạng một loạt ảnh chụp (snapshot) của một tập hợp các file. Mỗi lần *commit* GIT sẽ tiến hành chụp lại hệ thống các file tại thời điểm đó và lưu lại một tham chiếu đến ảnh chụp đó.

***Note***: 
  - Các file không có thay đổi thì GIT sẽ không lưu lại file đó lần nữa mà chỉ có một liên kết đến file đã lưu ở lần trước.

  - Hầu hết mọi thao tác với GIT diễn ra ở Local trừ commit lên Server hoắc lấy một file do người khác đã commit.

  - Mọi thứ khi lưu trữ vào GIT dều được kiểm tra bởi mã băm (hash, checksum). Nên bất kỳ sự thay nổi nào diễn ra trên file đều được GIT phát hiện.

# **GIT STATUS**

Với GIT file sẽ nằm ở 3 trạng thái *commited, modidied, staged*:

  + committed: Dữ liệu đã được lưu trữ an toàn trong Local Database.

  +  modified: Có sự thay đổi trên dữ liệu(file) tuy nhiên chưa được lưu trong Local Database.

  + staged: Các file có sự thay đổi được đưa vào Staging Area để chuẩn bị cho commit tiếp theo.

**GIT sẽ tổ chức dự án ra ba khu vực:**

![alt text](https://git-scm.com/book/en/v2/images/areas.png)

1. Thư mục làm việc(Working Directory) - Chứa bản sao phiên bản cụ thể của dự án.

2. Khu vực sắp xếp(Staging Area) - Là một file nằm trong thư mục GIT chứa thông tin về file sẽ commit.

3. Thư mục .git (.git directory(Repository) - Nơi GIT lưu Database các file Metadata


# **SETTING BAN ĐẦU**

Một số lệnh căn bản:

```
      git --version //kiểm tra phiên bản
      git config --list // hiển thị tham số thiết lập git
      git --help
```

Cài đặt user:


```
      git config --global user.name "cobb"
      git config --global user.email "cobb@gmail.com"
```

# **CÁC THAO TÁC VỚI GIT**

**TẠO MỘT REPOSITORY MỚI**

![alt text](https://git-scm.com/book/en/v2/images/lifecycle.png)

Vòng đời của các file trong GIT.

```
git status // Kiểm tra trạng thái của các file trong dự án
```
  + Một file mới tạo thì sẽ ở trạng thái *untracked*.

  + Từ trạng thái *untracked* dùng lệnh GIT(git add) để đưa nó vào trạng thái *staged*. Một file ở trạng thái *staged* có nghĩa là file đó được đưa vào kế hoạch để lưu (mới hoặc cập nhật) vào CSDL của GIT) - và bắt đầu theo dõi.

  + Từ trạng thái *staged* dùng lệnh GIT(git commit) để cập nhật vào CSDL. Sau khi cập nhật đầy đủ thông tin về file ở phiên làm việc cuối thì thông tin đó sẽ tồn tại trong CSDL GIT và file đó sẽ ở trạng thái *unmodified*.

  + Ở trạng thái *unmodified*, nếu File bị sửa đổi nội dung thì lập tức nó chuyển snag trạng thái *modified*. Và nếu muốn cập nhật sự thay đổi vào CSDL của GIT thì phải đưa nó vào kế hoach cập nhật(trạng thái *staged*) rồi commit để đưa vào CSDL lúc này file sẽ có trạng thái *unmodified*.




**1. Tạo Local Repo**

```
cd path/to/project/cobb_project
git init
```
Cobb_project hiện tại đã trở thành một Local Repo sẵn sàng để chứa các file code và một thư mục .git chứa toàn bộ dữ liệu GIT về Repo này.

```
/cobb_project
--/index.html
--/anout.html
```
**2. Thêm file vào Staging Area**
```
git status          //Xem trạng thái hiện tại của các file trong thư mục.
git add index.html  //Đưa file mới vào staging area
git add .           //Thêm tất cả sự thay đổi, trừ xóa file.
git add *.c         //Thêm tất sự thay đổi trên các file có đuôi mở rộng .c
git add -A          //Thêm tất các sự thay đổi
git add -u          //Thêm mọi thứ trừ file mới
```

Bỏ qua một số file không giám sát.

Thêm file đó vào nội dung file .gitignore.

**3. Thực hiện commit**

```
git commit -m "comment example:C0 - add new function"

git log --oneline // Xem lại lịch sủ commit

25e48755 (HEAD -> master) C0 - add new function
```

![alt text](https://xuanthulab.net/photo/gitrepo-4336.png)


## **LÀM VIỆC CƠ BẢN VỚI GIT**

1. Tạo một file text sau đó tiến hành add và commit.
```
touch project.txt
git add project.txt
git commit -m "C0: Khoi tao du an"
```
2. Tạo một file mới và add vào staging area
```
touch functionA.txt
git add functionA.txt
```

3. Đưa file ra khỏi stagging are.
Khi cần thay đổi nội dung của file trước khi commit nếu file đang ở stagging area thì dùng lệnh reset để đưa file ra khỏi stagging area và tiến hành sửa đổi và cập nhật sau.

```
git reset HEAD functionA.txt
```
4. Tiến hành thay đổi nội dung file functionA.

```
functionA.txt
  ---add fA new code 1---

git add functionA.txt
git commit -m "C1: Them code vao functionA"
```

![alt text](https://xuanthulab.net/photo/gitrepo-4337.png)

5. Tiếp tục thay đổi nội dung file functionA.
```
functionA.txt
  ---add fA new code 2---
git status
  On branch master
  Changes not staged for commit:
          modified:   functionA.txt
```

Bây giờ code mới gặp vấn đề và muốn quay lại trạng thái khi chưa add code2 thì sử dụng lệnh checkout.

```
git checkout --functionA.txt

Open functionA.txt
functionA.txt
  ---add fA new code 1---
```

6. Tiếp tục thay đổi nội dung file functionA và tiến hành commit.

```
functionA.txt
  ---add fA new code 3---

git add functionA.txt
git commit -m "C2: Update functionA"
```
![alt text](https://xuanthulab.net/photo/gitrepo-4341.png)


7. Tiếp tục thay đổi nội dung file functionA và tạo thêm một file mới functionB.

```
functionA.txt
  ---add fA new code 4---

functionB.txt
  --add fB new code 1---

git status
Changes not staged for commit:
        modified:   functionA.txt

Untracked files:
        functionB.tx


git add functionA.txt
git add functionB.txt
git commit -m "C3: Update fA and Create fB"
```
untracked file là file chưa hề được đưa vào lịch sử commit.

![alt text](https://xuanthulab.net/photo/gitrepo-4342.png)

8. Lệnh diff

Dùng để so sánh sự khác nhau trong thư mục làm việc.
```
Add new code into functionA:
  ---add fA new code 5---

git diff // so sánh sự khác nhau giữa thư mục đang làm việc và bản commit cuối
  diff --git a/functionA.txt b/functionA.txt
  index 54b79eb..db05085 100644
  --- a/functionA.txt
  +++ b/functionA.txt
  @@ -1 +1 @@
  -  ---add fA new code 4---
  \ No newline at end of file
  +  ---add fA new code 5---
  \ No newline at end of file

git add functionA.txt
git diff // so sánh sự khác nhau của functionA.txt ở thư mục làm việc và bản ở trong staged. Ngay thời điểm này sẽ có thông báo vì 2 bản hoàn toàn giống nhau.

Add new code into functionA:
  ---add fA new code 6---

git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   functionA.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   functionA.txt

file function có một bản ở staged và một bản mới sửa đổi ở working directory khác với bản kế hoạch.

git diff //so sánh sự khác nhau giữa bản đang ở thư mục làm việc và bản kế hoạch commit
  diff --git a/4.txt b/4.txt
  index db05085..1773e9b 100644
  --- a/4.txt
  +++ b/4.txt
  @@ -1 +1 @@
  -  ---add fA new code 5---
  \ No newline at end of file
  +  ---add fA new code 6---
  \ No newline at end of file
```



Thời điểm này functionA.txt có 3 bản khác nhau:
  + Bản ở thư mục làm việc.
  + Bản trong kế hoạch commit staged
  + Bản trong dữ liệu GIT trong commit cuối.

Để so sánh sự khác nhau giữa bản staged và bản commit dùng lệnh:

```
git diff --staged
  diff --git a/4.txt b/4.txt
  index 54b79eb..db05085 100644
  --- a/4.txt
  +++ b/4.txt
  @@ -1 +1 @@
  -  ---add fA new code 4---
  \ No newline at end of file
  +  ---add fA new code 5---
  \ No newline at end of file
```

Tóm lại lệnh git diff so sánh sự khác nhau giữa bản trong thư mục làm việc và bản trong staged nếu có, nếu không thì so sánh với bản commit cuối cùng. Để so sánh giữa bản staged và bản commit cuối dùng git diff --staged.

9. Khi trong staged đang tồn tại một bản chưa commit của functionA.txt nếu bản ở WD có sửa đổi và gõ lệnh git add thì bản trong staged sẽ được thay mới từ WD.

```
$ git status
On branch master
Changes to be committed: 
        modified:   functionA.txt //staged

Changes not staged for commit:
        modified:   functionA.txt //WD

$ git add .
$ git status
Changes to be committed: 
        modified:   test.html //staged

$ git commit -m "C4"
```

![alt text](https://xuanthulab.net/photo/gitrepo-4343.png)

10. Dùng git rm để xóa file ra khỏi GIT

```
$ git rm functionB.txt
$ git status
Changes to be committed:
        deleted:    functionB.html
Việc xóa functionB.txt đã được đưa vào satged. Nếu tiến hành commit thì một snapshot phiên bản mà trong đó file functionB.txt đã bị xóa.
Tuy nhiên nếu chưa commit và muốn phục hồi lại file bị xóa do git rm ta sẽ đưa nó ra khỏi staged và tiến hành phục hồi.

$ git reset HEAD functionB.txt
$ git checkout -- functionB.txt

```
**Note:** Nếu file được xóa thủ công thì nó sẽ không nằm trong staged và phải tiến hành add để đưa vào staged.

```
$ git checkout -- filename //Khôi phục thay đổi nội dung của file có thể là khôi phục từ staged(nếu có) hoặc khôi phục từ commit cuối. Nếu muốn khôi phục file từ commit cũ có hash thì:
$ git checkout [hash] filename 
$ git checkout [hash] . //khôi phục tất cả các file
```

```
Tiến hành xóa file functionB.txt bằng File explore
$ git status
Changes not staged for commit:
    deleted:    functionB.txt
$ git add functionB.txt
$ git status
Changes to be committed:
    deleted:    functionB.txt
$ git commit -m "C5: Delete functionB"
```
![alt text](https://xuanthulab.net/photo/gitrepo-4344.png)

11. Dùng git commit --amend để thêm vào commit cuối cùng tránh tạo commit mới.

```
Open functionA.txt
---add fA new code 7---

$ git add fucntionA.txt
$ git commit --amend -m "Update fA and Del fB"
```

Khi tiến hành commit thì hệ thống sẽ một snapshot mới. Để không tạo ra snapshot mới mà thay thế snapshot cuối cùng dùng lệnh git commit --amend.




## **GIT REMOTE**
GIT SERVER là máy chủ có cài đặt dịch vụ GIT, cho phép tạo ra các Repository.
GITHUB là một máy chủ GIT, có thể tạo ra một Repository trên nó được gọi là Remote Repository. Người dùng có thể sao chép (clone) Remote Repo về máy (Local Repo) để làm việc và cập nhật lại Remote. 

![alt text](https://xuanthulab.net/photo/basic-remote-workflow.png)


Thiết lập để làm việc với Remote Repository.


```
$ git remote //Kiểm tra các remote hiện tại
$ git remote add name_remote addr_remote // name_remote: Tên người dùng đặt
// addr_remote địa chỉ remote repo
$ git remote add origin https://github.com/Momentff/git_note.git

$ git remote -v // Kiểm tra địa chỉ của remote
$ git remote show origin // Xem thông tin chi tiết về một Remote có tên origin
$ git remote rename //Đổi tên một Remote trong Local VD:
$ git remote rename src dst 

```
Một số lệnh cơ bản làm việc với Remote
```
$ git push origin master // cập nhật dữ liệu từ Local lên Remote.
$ git clone https://github.com/Momentff/git_note.git // Clone một Remote Repo
$ git fetch origin // Lấy dữ liệu mới từ Remote Repo ( dữ liệu này trên local chưa có (ví dụ do người khác đưa lên)). Không làm ảnh hưởng đến code đang có của dự án trên Local
$ git pull origin master //Lấy toàn bộ dữ liệu mới theo Remote. Nếu Local chưa commit và push thì code cũ có thể sẽ bị mất.

```
**Note:** Cần đảm bảo Local là clean khi pull, nên cần commit trước hoặc bỏ tất cả các file untracked.

```
$ git clean -d -fx
```


# **Sự khác nhau của git fetch và git pull**
![alt text](https://xuanthulab.net/photo/remotegit-4300.png)

Khi git fecth nó cập nhật thông tin từ Remote Repo vào Local Repo nhưng không ảnh hưởng đến các file code trong WD, còn git pull sẽ cập nhật cả WD của Local làm các file code sẽ cập nhật theo Remote.

# **TAG TRONG GIT**
Tag là một cái tên dùng để đánh dấu một điểm nào đó trong lịch sử quá trình commit khi cho rằng điểm đó làm quan trọng, cần chú ý.

Một số lệnh về Tag

Liệt kê các tag

```
$ git tag
```
Tạo một tag mới và đánh dấu vào commit cuối.
```
$ git tag -a beta -m "Phien ban beta" // tag có tên beta chú thích là Phiên bản beta
```
Tạo một Tag mới và đánh dấu vào commit cũ
```
$ git tag -a gamma -m "Phien ban gamma" 95dsad //95dsad là mã hash của commit.
```
Xem thông tin về commit được gắn tag
```
$ git show tag_name
```
Cập nhật tag lên remote:
```
//Mặc định lệnh git push sẽ không push tag lên Remote. Để cập nhật tag dùng tag_name cụ thể:
$ git push origin tagname
// Cập nhật tất cả các tag
$ git push origin --tags
```
Quay về một phiên bản bằng Tag
```
// Có thể quay về phiên bản cũ bằng mã hash việc dùng tag sẽ mang tính gợi nhớ.
$ git checkout tagname 
// Lệnh git checkout làm cho con trỏ HEAD bị tách ra, để giữ lại các commit sau thời điểm checkout thì phải tạo nhánh branch mới bắt đầu từ tag này:
$ git checkout -b newbranchname tagname
```
Xóa một tag
```
// Cần xóa tag ở cả local lẫn remote
$ git push --delete origin tagname
$ git tag -d tagname
```

## **BRANCH TRONG GIT**
Nhánh và con trỏ HEAD.

Trong GIT nhánh(branch) là hướng rẽ phát triển code, với mục đích không làm rối hướng phát triển chính. Sau đó nhánh có thể tích hợp (merge) vào nhánh chính.

1. Nhánh chính master:

Khởi tạo một Repo mới nhánh master sẽ mặc định là nhánh chính và làm việc. Tiến hành 3 commit.
```
$ git init
$ touch 0.txt
$ git add 0.txt
$ git commit -m "C0"

$ touch 0.txt
$ git add 0.txt
$ git commit -m "C1"

$ touch 0.txt
$ git add 0.txt
$ git commit -m "C2"
```
![alt text](https://xuanthulab.net/photo/1-4301.png)


2. Lịch sử commit

```
$ git log --pretty=oneline
0d7ae45f93922e40c2c8dfdd14721e77476f6d01 (HEAD -> master) C2
927163bd31669a7651621e91982afbdf6f30cc1f C1
efab635085727cefd2b0271e7b72b9fd37a62614 C0
```
Output của lệnh git log cho biết hiện tại đang làm việc trên nhánh master và đang ở vị trí commit cuối với mã hash là 0d7ae45 (C2).

  **Note**: Con trỏ **HEAD** thể hiện vị trí hiện tại đang làm việc thuộc nhánh nào và ở commit cuối nào.

3. Xem danh sách các nhánh.

```
$ git branch
*master
```
4. Tạo một nhánh mới.

Dùng lệnh:

```
$ git branch branch_name
// VD: Khởi tạo nhánh branch từ nhánh master và khởi đầu từ commit C2(kế thừa master từ C2 trở về trước)
$ git branch alpha
```
![alt text](https://xuanthulab.net/photo/gitbranch-4307.png)

5. Chuyển sang nhánh làm việc mới.

```
// Chuyển sang làm việc trên nhánh alpha
$ git checkout alpha
```
![alt text](https://xuanthulab.net/photo/gitbranch-4308.png)

Cả master và alpha hiện đang trỏ đến commit C2 nhưng con trỏ HEAD cho biết đang làm việc với nhánh alpha.

6. Commit trên nhánh mới.

```
$ touch 3.txt
$ git add 3.txt
$ git commit -m "C3"

// Check lịch sử commit
$ git log ---pretty=oneline
c7d81e3771b61c97c1b6e661acdb9b25ec9cb199 (HEAD -> alpha) C3
0d7ae45f93922e40c2c8dfdd14721e77476f6d01 (master) C2
927163bd31669a7651621e91982afbdf6f30cc1f C1
efab635085727cefd2b0271e7b72b9fd37a62614 C0
```
![alt text](https://xuanthulab.net/photo/gitbranch-4309.png)

7. Tiếp tục thay đổi và commit trên nhánh alpha.

```
$ echo "update new content" > funcA.txt
$ git add funcA.txt
$ git commit -m "C4"
```

![alt text](https://xuanthulab.net/photo/gitbranch-4310.png)

Ở commit cuối, nhánh alpha WD có các file 0.txt, funcA.txt. So với nhánh master nó có thêm file 4.txt, và file funcA.txt mới thay đổi nội dung.

8. Chuyển về làm việc với nhánh master

```
$ git checkout master
```
![alt text](https://xuanthulab.net/photo/gitbranch-4311.png)
Lúc này WD đã quay về trạng thái commit ở cuối nhánh master: funcA.txt, 0.txt. File funcA.txt chưa cập nhật nội dung gì. Con trỏ HEAD trỏ vào nhánh master.

9. Tạo sự thay đổi và commit cho nhánh master.

```
$ touch 4.txt
$ echo "update code" > 0.txt
$ git add 4.txt
$ git commit -m "C5"
```
![alt text](https://xuanthulab.net/photo/gitbranch-4319.png)

10. Tạo nhánh mới từ master

Gỉa sử có sự cố xảy ra và cần sửa lỗi gấp

```
$ git branch hotfix
$ git checkout hotfix
```
![alt text](https://xuanthulab.net/photo/gitbranch-4320.png)

Lúc này đang làm việc trên nhánh hotfix. Cả master và hotfix đều chỉ đến commit C5.

11. Tạo thay đổi và commit trên hotfix.

```
$ echo "Sua loi tren 2.txt" > 2.txt
$ git add 2.txt
$ git commit -m "C6"

$ git log --pretty=oneline
$ eda207ba7b5a02f3687eb0c71f08b627ce98a7ca (HEAD -> sualoigap) C6
2c3fa4d3fe0035844314c232324afca9ffc1a288 (master) C5
0d7ae45f93922e40c2c8dfdd14721e77476f6d01 C2
927163bd31669a7651621e91982afbdf6f30cc1f C1
efab635085727cefd2b0271e7b72b9fd37a62614 C0
```

![alt text](https://xuanthulab.net/photo/gitbranch-4321.png)

```
// Add thêm 1 commit
$ echo "Sua loi tren 1.txt" > 1.txt
$ git add 1.txt
$ git commit -m "C7"
```
![alt text](https://xuanthulab.net/photo/gitbranch-4322.png)


## **BRANCH MERGE**

12. Trộn nhánh hotfix vào master

Để có thể merge nhánh hotfix vào nhánh master phải chuyển về làm việc trên nhanh master rồi cho nhánh hotfix gộp vào master bằng lệnh merge.

```
$ git checkout master
$ git merge hotfix
```
![alt text](https://xuanthulab.net/photo/gitbranch-4323.png)

Sau khi gộp cả 2 nhánh master và hotfix đều chỉ vào commit C7. Mũi tên nối từ C7 đến C5 là đánh dấu hotfix được tách ra tử commit C5.

13. Xóa nhánh

Khi fix lỗi xong, nếu k có mục đích khác thì nhánh này có thể được xóa bằng lệnh.

```
$ git branch -d hotfix
$ git log --pretty=oneline
89b19cb2a226bf609bb8330dc1e2312f76bffd0e (HEAD -> master) C7
eda207ba7b5a02f3687eb0c71f08b627ce98a7ca C6
2c3fa4d3fe0035844314c232324afca9ffc1a288 C5
0d7ae45f93922e40c2c8dfdd14721e77476f6d01 C2
927163bd31669a7651621e91982afbdf6f30cc1f C1
efab635085727cefd2b0271e7b72b9fd37a62614 C0
```
![alt text](https://xuanthulab.net/photo/gitbranch-4330.png)

Mũi tên từ C7 đến C5 đã xóa bỏ. Con trỏ head bây giờ trỏ vào hotfix và master trỏ vào C5.



## **MERGE CONFLICT**

Nếu chức năng ở nhóm alpha đã hoàn thiện sẽ cần được merge vào nhánh master. Tuy nhiên do 2 nhánh có nhiều commit kể từ thời điểm rẽ nhánh nên khi gộp sẽ xem xét sự thay đổi trên cả 2 nhánh tại 3 điểm, thời điểm commit cuối của các nhánh và thời điểm rẽ nhánh. Đó là C2, C4, C7.

![alt text](https://xuanthulab.net/photo/gitbranch-4331.png)

Hiện tạ Repo có 2 nhánh, điểm rẽ là ở snapshot C2 (hash:0d7ae45) nghĩa là thời điểm đó master và alpha giống nhau. Trở về snapshot C2:

```
$ git checkout 0d7ae45
HEAD is now at 0d7ae45 C2
```

Khi mở thư mục làm việc lúc này file 0,1,2 txt đều có nội dung trống bên trong.


Kiểm tra nhánh alpha ở commit cuối với snapshot C4:

```
$ git checkout alpha
```
Mở WD hiện tại sẽ có file 0,1,2,3 txt và nội dung file 1.txt đã bị thay đổi "Update new content".

Kiểm tra nhánh master ở commit cuối với snapshot C7.

```
$ git checkout master
```

Mở WD hiện tại sẽ có các file 0,1,2,4 txt file 0.txt có nội dung "Update code", file 1.txt có nội dung "Sua lỗi trên 1.txt", file 2.txt có nội dung "Sua lỗi trên 2.txt" còn file 4.txt rỗng.

Ta có bảng sau:

|file |master  |alpha   |Khi merge alpha vào master   |
|---|---|---|---|
|0.txt   |có sữa đổi: Update code   |Không sửa đổi   |Không xung đột: lấy theo bản tại master(vì sửa đổi tại đây)   |
|1.txt   |có sữa đổi: Sua loi tren 1.txt   |có sữa đổi: Update new content    |Xung đột phải chọn master or alpha   |
|2.txt   |có sữa đổi: Sua loi tren 2.txt   |Không sửa đổi   |Không xung đột: lấy theo bản tại master   |
|3.txt   |shông sửa đổi   |Có sữa đổi: Tạo file mới   |Không xung đột: lấy bản alpha   |
|4.txt   |có sữa đổi: tạo mới file    |Không sửa đổi   |Không xung đột: lấy bản master   |

Cần phải xử lý xung đột tại file 1.txt

```
$ git checkout master
$ git merge alpha
Auto-merging 1.txt
CONFLICT (content): Merge conflict in 1.txt
Automatic merge failed; fix conflicts and then commit the result.
//Check status
git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:

        new file:   3.txt

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   1.txt

```
Mở file 1.txt để xử lý xung đột

```
<<<<<<< HEAD
Sua loi tren 1.txt
=======
Update new content to file
>>>>>>> alpha
```

Nội dung trong master sẽ nằm giữa <<<<<<< HEAD và =======, còn nội dung trong alpha sẽ nằm giữa ======= và >>>>>>> alpha.

```
// VD giữ lại nội dung trên alpha.
Update new content to file
```

Sau khi đã giải quyết hết xung đột tiến hành add và commit.

```
$ git add .
$ git commit -m "C8"
$ git log --oneline
a252058 (HEAD -> master) C8
89b19cb C7
eda207b C6
2c3fa4d C5
bbc3757 (alpha) C4
c7d81e3 C3
0d7ae45 C2
927163b C1
efab635 C0
```

![alt text](https://xuanthulab.net/photo/gitbranch-4332.png)

## **REBASE**

**Ở nhánh master lấy bản sao tại thời điểm snapshot C5 (Hash: 2c3fa4d).**

```
$ git checkout 2c3fa4d
You are in 'detached HEAD' ...
HEAD is now at 2c3fa4d C5 
```

Dòng thông báo HEAD is now at 2c3fa4d C5 cho biết con trỏ HEAD bị tách ra khỏi tất cả các nhánh hiện có và nó ở vị trí một nhánh tạm thời sinh ra có tên 2c3fa4d từ thời điểm này ta sẽ làm việc trên nhanh tạm thời đó. Nếu không tạo nhánh mới tại đây thì nhánh tạm thời và các commit trên nó sẽ mất khi chuyển nhánh.

```
$ git checkout -b beta
$ git branch
  alpha
* beta
  master
// WD sẽ có nội dung như commit cuối C5.
```

**Tạo sự thay đổi thực hiện 2 commit trên beta**

```
$ touch 5.txt
$ git add .
$ git commit -m "C9"
$ echo "Modify from beta" > 2.txt
$ git add .
$ git commit -m "C10"

// Xem lịch sử commit
$ git log --oneline
9e101b7 (HEAD -> beta) C10
d391bde C9
2c3fa4d C5
0d7ae45 C2
927163b C1
efab635 C0
```

![alt text](https://xuanthulab.net/photo/gitbranch-4333.png)

**Gộp nhánh với rebase.**

Có thể gộp beta vào master bằng merge, khi đó GIT tạo một commit như là điểm gộp nhánh bằng cách kết hợp C10, C8 có so sánh với C5 (three-way). Tuy nhiên khi ta muốn việc gộp đó lại thực hiện theo cách cập nhật những gì thay đổi trên C10 của beta vào C8 của master mà không phải tạo ra một commit - snapshot nối tiếp => rebase sẽ giải quyết việc này.

Với Rebase mọi commit trên nhánh này sẽ có trong một nhánh khác.

```
// Chạy rebase để mọi thứ trong master áp dụng vào beta
$ git checkout beta
$ git rebase master
```
Trong quá trình rebase, mở file xung đột sửa lại nội dung và gõ lệnh:

```
$ git add .
$ git rebase --continue
// Nếu rebase đang tạm dừng để xử lý xung đột, dùng abort để hủy rebase, phục hồi trạng thái khi chưa gõ lệnh rebase.
$ git rebase --abort
// Xem lại lịch sử commit sau khi rebase
$ git checkout beta
$ git log --oneline
544511a (HEAD -> beta) C10
be103d9 C9
1a90428 (master) C8
89b19cb C7
eda207b C6
2c3fa4d C5
bbc3757 (alpha) C4
c7d81e3 C3
0d7ae45 C2
927163b C1
efab635 C0
```

![alt text](https://xuanthulab.net/photo/gitbranch-4334.png)

Nhánh beta đã gồm tất cả các commit từ C8 về trước của master, tuy nhiên master vẫn dừng lại ở C8. Quay về master và merge nó với beta để có được phiên bản hợp nhất, có trỏ HEAD dịch về cuối tới snapshot C10.

```
$ git checkout master
$ git merge beta
$ git log --oneline

544511a (HEAD -> master, beta) C10
be103d9 C9
1a90428 C8
89b19cb C7
eda207b C6
2c3fa4d C5
bbc3757 (alpha) C4
c7d81e3 C3
0d7ae45 C2
927163b C1
efab635 C0
```
![alt text](https://xuanthulab.net/photo/gitbranch-4335.png)

**Note**: Khi sử dụng rebase thì rebase sẽ viết lại lịch sử commit trên nhánh, nên tuyệt đối không bao giờ thực hiện rebase khi các commit của nhánh đã đẩy lên Repo công khai, nếu không mọi việc sẽ rối tung.

**Một vài lệnh quản lý nhánh**

```
$ git branch                   //Liệt kê các nhánh
$ git branch -v                //Liệt kê nhánh + commit cuối   
$ git branch --mergerd         //Các nhánh merge với nhánh hiện tại
$ git branch --no-merged       //Các nhánh không merge với nhánh hiện tại 
$ git branch -d branchname     //Xóa nhánh
```

**Xóa commit cũ, viết lại lịch sử commit**

Nếu cần thay đổi N commit cuối cùng, xóa, ghi đè:

```
$ git rebase -i HEAD~N
```

Trong danh sách commit có thể lựa chọn các thiết lập như sau:

  + p(pick)   : giữ lại commit
  + s(squash) : sử dụng nội dung commit này nhưng đè vào commit phía trước.
  + r(rework) : giữ lại commit nhưng cho phép viết lại nội dung thông điệp.

Cập nhật lên remote:

```
$ git push origin +master
```

Remote đã xóa một commit cũ và muốn local cập nhật theo:

```
$ git pull --rebase
or
$ git fetch
$ git rebase origin/master
```

