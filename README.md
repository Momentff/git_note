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


