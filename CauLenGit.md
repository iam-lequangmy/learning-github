# CÁC CÂU LỆNH GIT

## Kiểm tra và cấu hình Git

```
git --version
(Kiểm tra phiên bản Git đang được cài đặt.)

git config --global user.name "Tên của bạn"
(Thiết lập tên người dùng cho tất cả dự án Git trên máy.)

git config --global user.email "email@example.com"
(Thiết lập email dùng khi tạo commit.)

git config --global --list
(Xem toàn bộ cấu hình Git hiện tại.)

git help "tên lệnh"
(Mở tài liệu hướng dẫn của một lệnh Git.)
```

Ví dụ:

```
git help commit
```

---

# KHỞI TẠO DỰ ÁN GIT

## Khởi tạo kho lưu trữ Git

```
git init
(Khởi tạo Git trong thư mục hiện tại.)
```

Sau khi chạy lệnh, Git sẽ tạo thư mục ẩn `.git` để lưu lịch sử và thông tin của dự án.

## Sao chép dự án có sẵn

```
git clone "đường dẫn repository"
(Sao chép toàn bộ dự án và lịch sử commit từ remote về máy.)
```

Ví dụ:

```
git clone https://github.com/username/project.git

git clone https://github.com/username/project.git "tên thư mục"
(Sao chép dự án và lưu vào thư mục có tên được chỉ định.)
```

---

# THE WORKING DIRECTORY VÀ STAGING AREA

## Kiểm tra trạng thái

```
git status
(Kiểm tra trạng thái của các file trong dự án.)
```

Lệnh này cho biết:

* File nào chưa được Git theo dõi.
* File nào đã được chỉnh sửa.
* File nào đã được đưa vào Staging Area.
* Nhánh hiện tại là nhánh nào.

## Xem trạng thái ngắn gọn

```
git status -s
(Hiển thị trạng thái các file theo dạng ngắn gọn.)
```

Ví dụ kết quả:

```
M app.js
?? test.js
```

Trong đó:

```
M
(File đã bị chỉnh sửa.)

??
(File chưa được Git theo dõi.)
```

## Đưa file vào Staging Area

```
git add "tên file"
(Đưa một file vào Staging Area để chuẩn bị commit.)
```

Ví dụ:

```
git add app.js
```

## Đưa nhiều file vào Staging Area

```
git add "file 1" "file 2"
(Đưa nhiều file được chỉ định vào Staging Area.)
```

Ví dụ:

```
git add app.js index.html
```

## Đưa tất cả thay đổi vào Staging Area

```
git add .
(Đưa tất cả file mới và file đã thay đổi trong thư mục hiện tại vào Staging Area.)

git add -A
(Đưa tất cả file mới, file đã sửa và file đã xóa trong toàn bộ repository vào Staging Area.)
```

## Chọn từng phần thay đổi để đưa vào Staging Area

```
git add -p
(Cho phép chọn từng phần code thay đổi thay vì thêm toàn bộ file.)
```

---

# LƯU LỊCH SỬ CẬP NHẬT CODE

## Tạo commit

```
git commit
(Tạo commit từ các file đang có trong Staging Area và mở trình soạn thảo để nhập nội dung commit.)
```

## Tạo commit kèm nội dung

```
git commit -m "Nội dung commit"
(Tạo commit và ghi nội dung mô tả ngay trong câu lệnh.)
```

Ví dụ:

```
git commit -m "Thêm chức năng đăng nhập"
```

## Đưa file đã được Git theo dõi vào Staging Area và commit

```
git commit -am "Nội dung commit"
(Tự động thêm và commit các file đã được Git theo dõi.)
```

Lưu ý: Lệnh này không thêm các file hoàn toàn mới chưa được Git theo dõi.

## Sửa commit gần nhất

```
git commit --amend
(Sửa nội dung hoặc bổ sung file vào commit gần nhất.)
```

## Sửa tên commit gần nhất

```
git commit --amend -m "Nội dung mới"
(Đổi nội dung của commit gần nhất.)
```

Lưu ý: Không nên dùng `--amend` với commit đã push nếu đang làm việc chung với người khác.

---

# FILE .GITIGNORE

## Bỏ qua file hoặc thư mục

```
.gitignore
(File dùng để liệt kê những file hoặc thư mục Git không cần theo dõi.)
```

Ví dụ nội dung `.gitignore`:

```
node_modules/
.env
*.log
dist/
.vscode/
```

Ý nghĩa:

```
node_modules/
(Bỏ qua toàn bộ thư mục node_modules.)

.env
(Bỏ qua file .env.)

*.log
(Bỏ qua tất cả file có đuôi .log.)
```

## Ngừng theo dõi file đã được commit trước đó

Nếu file đã được Git theo dõi thì thêm vào `.gitignore` chưa đủ. Cần chạy:

```
git rm --cached "tên file"
(Ngừng theo dõi file nhưng vẫn giữ file trên máy.)
```

Ví dụ:

```
git rm --cached .env
```

Đối với thư mục:

```
git rm -r --cached "tên thư mục"
(Ngừng theo dõi toàn bộ thư mục nhưng vẫn giữ thư mục trên máy.)
```

---

# XEM SỰ THAY ĐỔI CỦA CODE

## Xem thay đổi chưa được đưa vào Staging Area

```
git diff
(So sánh code trong Working Directory với code trong Staging Area.)
```

## Xem thay đổi đã được đưa vào Staging Area

```
git diff --staged
(Xem những thay đổi đang chuẩn bị được commit.)
```

Có thể dùng lệnh tương đương:

```
git diff --cached
```

## Xem thay đổi của một file

```
git diff "tên file"
(Xem các dòng đã thay đổi trong một file.)
```

## So sánh hai commit

```
git diff "commit 1" "commit 2"
(So sánh nội dung giữa hai commit.)
```

## So sánh hai nhánh

```
git diff "nhánh 1".."nhánh 2"
(So sánh nội dung giữa hai nhánh.)
```

---

# XEM LỊCH SỬ COMMIT

## Xem lịch sử đầy đủ

```
git log
(Hiển thị lịch sử commit của nhánh hiện tại.)
```

## Xem lịch sử ngắn gọn

```
git log --oneline
(Mỗi commit được hiển thị trên một dòng.)
```

## Xem lịch sử dưới dạng sơ đồ

```
git log --oneline --graph --all
(Hiển thị lịch sử commit của tất cả nhánh dưới dạng sơ đồ.)
```

## Xem thêm tên nhánh và tag

```
git log --oneline --graph --decorate --all
(Hiển thị sơ đồ commit kèm tên nhánh và tag.)
```

## Xem lịch sử của một file

```
git log -- "tên file"
(Xem các commit đã thay đổi file được chỉ định.)
```

## Xem nội dung của một commit

```
git show "ID commit"
(Hiển thị thông tin và phần code thay đổi của một commit.)
```

## Xem commit gần nhất

```
git show HEAD
(Hiển thị nội dung của commit mà HEAD đang trỏ tới.)
```

---

# NHÁNH TRONG GIT

## Xem danh sách nhánh

```
git branch
(Hiển thị các nhánh local.)
```

Dấu `*` nằm trước tên nhánh hiện tại.

## Xem cả nhánh local và remote

```
git branch -a
(Hiển thị tất cả nhánh local và remote-tracking branch.)
```

## Tạo nhánh mới

```
git branch "tên nhánh"
(Tạo một nhánh mới tại commit hiện tại nhưng không chuyển sang nhánh đó.)
```

Ví dụ:

```
git branch feature-login
```

## Chuyển sang nhánh khác

Cách hiện đại:

```
git switch "tên nhánh"
(Chuyển sang nhánh được chỉ định.)
```

Cách cũ nhưng vẫn được sử dụng:

```
git checkout "tên nhánh"
(Chuyển sang nhánh được chỉ định.)
```

## Tạo nhánh mới và chuyển sang nhánh đó

Cách hiện đại:

```
git switch -c "tên nhánh"
(Tạo nhánh mới và chuyển sang nhánh mới.)
```

Cách cũ:

```
git checkout -b "tên nhánh"
(Tạo nhánh mới và chuyển sang nhánh mới.)
```

## Đổi tên nhánh hiện tại

```
git branch -m "tên mới"
(Đổi tên nhánh đang đứng.)
```

## Đổi tên một nhánh khác

```
git branch -m "tên cũ" "tên mới"
(Đổi tên nhánh được chỉ định.)
```

## Xóa nhánh đã được gộp

```
git branch -d "tên nhánh"
(Xóa nhánh local nếu nhánh đó đã được merge.)
```

## Ép xóa nhánh

```
git branch -D "tên nhánh"
(Xóa nhánh local kể cả khi nhánh chưa được merge.)
```

Lưu ý: Lệnh này có thể làm mất commit chưa được lưu ở nhánh khác.

---

# GỘP NHÁNH TRONG GIT – CÁCH 1: MERGE

## Gộp một nhánh vào nhánh hiện tại

```
git merge "tên nhánh"
(Gộp lịch sử và thay đổi của nhánh được chỉ định vào nhánh đang đứng.)
```

Ví dụ muốn gộp `feature-login` vào `main`:

```
git switch main
git merge feature-login
```

Nhánh đứng sau `git merge` là nhánh được đưa vào nhánh hiện tại.

## Gộp và luôn tạo merge commit

```
git merge --no-ff "tên nhánh"
(Gộp nhánh và tạo một merge commit riêng.)
```

## Hủy quá trình merge đang bị xung đột

```
git merge --abort
(Hủy merge và đưa dự án về trạng thái trước khi bắt đầu merge.)
```

---

# GỘP NHÁNH TRONG GIT – CÁCH 2: REBASE

## Đưa commit của nhánh hiện tại lên trên một nhánh khác

```
git rebase "tên nhánh"
(Lấy các commit riêng của nhánh hiện tại, áp dụng lại chúng lên trên commit mới nhất của nhánh được chỉ định.)
```

Ví dụ đang đứng ở nhánh `feature-login`:

```
git switch feature-login
git rebase main
```

Kết quả:

* Các commit của `feature-login` được đặt lại lên trên commit mới nhất của `main`.
* Lịch sử commit thường thẳng và gọn hơn.
* Git tạo lại các commit nên ID commit sẽ thay đổi.

Lưu ý: Không nên rebase những commit đã push và đang được nhiều người cùng sử dụng.

## Tiếp tục rebase sau khi sửa xung đột

```
git add .
git rebase --continue
```

## Bỏ qua commit đang gây lỗi

```
git rebase --skip
(Bỏ qua commit hiện tại trong quá trình rebase.)
```

## Hủy toàn bộ quá trình rebase

```
git rebase --abort
(Đưa repository về trạng thái trước khi bắt đầu rebase.)
```

---

# GIT REBASE TƯƠNG TÁC

## Chỉnh sửa các commit gần nhất

```
git rebase -i HEAD~"số"
(Mở chế độ rebase tương tác để chỉnh sửa số commit gần nhất tính từ HEAD.)
```

Ví dụ:

```
git rebase -i HEAD~3
```

Lệnh trên cho phép chỉnh sửa ba commit gần nhất.

Một số lựa chọn thường gặp:

```
pick
(Giữ nguyên commit.)

reword
(Giữ nội dung code nhưng sửa nội dung commit.)

edit
(Dừng lại để sửa code hoặc sửa commit.)

squash
(Gộp commit này vào commit phía trước và cho phép sửa nội dung commit.)

fixup
(Gộp commit này vào commit phía trước và bỏ nội dung commit hiện tại.)

drop
(Xóa commit khỏi lịch sử.)
```

Lưu ý: Interactive rebase làm thay đổi lịch sử và ID commit.

---

# DỊCH CHUYỂN TRONG GIT – THAM CHIẾU TUYỆT ĐỐI

## Chuyển đến một commit bằng ID

```
git checkout "ID commit"
(Chuyển HEAD đến một commit bất kỳ bằng ID commit.)
```

Cách hiện đại:

```
git switch --detach "ID commit"
(Chuyển HEAD đến commit được chỉ định ở trạng thái Detached HEAD.)
```

Ví dụ:

```
git switch --detach a1b2c3d
```

Khi ở trạng thái Detached HEAD, HEAD không gắn với một nhánh cụ thể.

Nếu muốn tiếp tục phát triển code từ commit đó, nên tạo nhánh mới:

```
git switch -c "tên nhánh mới"
```

---

# DỊCH CHUYỂN TRONG GIT – TOÁN TỬ DẤU MŨ ^

## Chuyển đến commit cha

```
git checkout "tên nhánh hoặc commit"^
(Chuyển đến commit cha của nhánh hoặc commit được chỉ định.)
```

Ví dụ:

```
git checkout main^

git checkout a1b2c3d^
```

## Lùi về nhiều thế hệ

```
git checkout HEAD^^
(Lùi từ HEAD về hai commit cha.)

git checkout HEAD^^^
(Lùi từ HEAD về ba commit cha.)
```

Mỗi dấu `^` tương ứng với một lần đi đến commit cha.

## Chọn cha của merge commit

Một merge commit có thể có nhiều commit cha:

```
HEAD^1
(Commit cha thứ nhất.)

HEAD^2
(Commit cha thứ hai.)
```

Ví dụ:

```
git checkout HEAD^2
```

---

# DỊCH CHUYỂN TRONG GIT – TOÁN TỬ ~

## Lùi về commit tổ tiên

```
git checkout HEAD~"số"
(Chuyển HEAD đến commit tổ tiên cách commit hiện tại một số bước.)
```

Ví dụ:

```
git checkout HEAD~3
(Lùi về ba commit tính từ HEAD.)
```

Có thể dùng cách hiện đại:

```
git switch --detach HEAD~3
```

## Ép một nhánh trỏ đến commit khác

```
git branch -f "tên nhánh" HEAD~"số"
(Ép nhánh được chỉ định trỏ đến commit tổ tiên cách HEAD một số bước.)
```

Ví dụ:

```
git branch -f main HEAD~3
```

Lệnh trên làm nhánh `main` trỏ đến commit cách HEAD ba bước về trước.

Lưu ý: Lệnh này di chuyển con trỏ nhánh, không tự động chuyển HEAD sang nhánh đó.

---

# HOÀN TÁC VỚI GIT RESTORE

## Đưa file ra khỏi Staging Area

```
git restore --staged "tên file"
(Đưa file ra khỏi Staging Area nhưng vẫn giữ phần code đã chỉnh sửa.)
```

Ví dụ:

```
git restore --staged secret.env
```

## Đưa tất cả file ra khỏi Staging Area

```
git restore --staged .
(Bỏ toàn bộ file khỏi Staging Area nhưng vẫn giữ các thay đổi.)
```

## Hủy thay đổi chưa commit của một file

```
git restore "tên file"
(Hủy toàn bộ thay đổi chưa được commit của file.)
```

Ví dụ:

```
git restore experiment.js
```

Cảnh báo: Phần code chưa commit trong file sẽ bị mất.

## Hủy thay đổi chưa commit của tất cả file

```
git restore .
(Khôi phục tất cả file về trạng thái gần nhất trong Staging Area hoặc commit.)
```

Cảnh báo: Các thay đổi chưa được lưu có thể bị mất.

## Khôi phục file từ một commit

```
git restore --source="ID commit" "tên file"
(Lấy phiên bản của file từ commit được chỉ định.)
```

Ví dụ:

```
git restore --source=HEAD~2 app.js
```

---

# HOÀN TÁC VỚI GIT RESET

## Reset dạng mặc định

```
git reset HEAD~"số"
(Di chuyển nhánh hiện tại lùi về commit tổ tiên và đưa thay đổi của các commit bị loại ra khỏi Staging Area.)
```

Lệnh mặc định tương đương:

```
git reset --mixed HEAD~"số"
```

Ví dụ:

```
git reset HEAD~1
```

Kết quả:

* Nhánh hiện tại lùi lại một commit.
* Commit gần nhất không còn nằm trên nhánh hiện tại.
* Phần code của commit đó vẫn còn trong Working Directory.
* Các thay đổi không còn nằm trong Staging Area.

## Reset mềm

```
git reset --soft HEAD~"số"
(Di chuyển nhánh lùi về commit cũ nhưng giữ các thay đổi trong Staging Area.)
```

Ví dụ:

```
git reset --soft HEAD~1
```

Phù hợp khi muốn tạo lại commit nhưng vẫn giữ nguyên các file đã staged.

## Reset hỗn hợp

```
git reset --mixed HEAD~"số"
(Di chuyển nhánh lùi lại, giữ code nhưng đưa thay đổi ra khỏi Staging Area.)
```

Đây là chế độ mặc định của `git reset`.

## Reset cứng

```
git reset --hard HEAD~"số"
(Di chuyển nhánh lùi lại và xóa toàn bộ thay đổi sau commit được chọn.)
```

Ví dụ:

```
git reset --hard HEAD~1
```

Cảnh báo: Lệnh này có thể làm mất code chưa được lưu.

## Đưa Staging Area về trạng thái của HEAD

```
git reset HEAD
(Đưa tất cả file ra khỏi Staging Area nhưng vẫn giữ phần code đã sửa.)
```

Hiện nay có thể dùng lệnh rõ ràng hơn:

```
git restore --staged .
```

---

# HOÀN TÁC VỚI GIT REVERT

## Đảo ngược một commit

```
git revert "ID commit"
(Tạo một commit mới để đảo ngược những thay đổi của commit được chỉ định.)
```

Ví dụ:

```
git revert a1b2c3d
```

## Đảo ngược commit hiện tại

```
git revert HEAD
(Tạo một commit mới để đảo ngược commit gần nhất.)
```

## Đảo ngược commit cha của HEAD

```
git revert HEAD^
(Tạo một commit mới để đảo ngược thay đổi của commit cha của HEAD.)
```

Lưu ý:

* `git reset` thay đổi vị trí con trỏ nhánh và có thể thay đổi lịch sử.
* `git revert` không xóa commit cũ mà tạo thêm một commit đảo ngược.
* Với commit đã push và đang dùng chung, `git revert` thường an toàn hơn `git reset`.

---

# DỊCH CHUYỂN COMMIT VỚI GIT CHERRY-PICK

## Lấy thay đổi của một commit

```
git cherry-pick "ID commit"
(Lấy phần thay đổi của commit được chỉ định và tạo một commit mới trên nhánh hiện tại.)
```

Ví dụ:

```
git cherry-pick a1b2c3d
```

## Lấy nhiều commit

```
git cherry-pick "commit 1" "commit 2"
(Lấy thay đổi của nhiều commit và áp dụng lần lượt vào nhánh hiện tại.)
```

Ví dụ:

```
git cherry-pick a1b2c3d e4f5g6h
```

## Lấy một khoảng commit

```
git cherry-pick "commit đầu"^.."commit cuối"
(Lấy toàn bộ commit từ commit đầu đến commit cuối, bao gồm cả hai.)
```

## Tiếp tục cherry-pick sau khi sửa xung đột

```
git add .
git cherry-pick --continue
```

## Hủy cherry-pick

```
git cherry-pick --abort
(Hủy quá trình cherry-pick và quay lại trạng thái trước đó.)
```

---

# XÓA VÀ ĐỔI TÊN FILE

## Xóa file bằng Git

```
git rm "tên file"
(Xóa file khỏi máy và đưa thao tác xóa vào Staging Area.)
```

## Xóa thư mục

```
git rm -r "tên thư mục"
(Xóa thư mục và đưa thao tác xóa vào Staging Area.)
```

## Ngừng theo dõi nhưng giữ file trên máy

```
git rm --cached "tên file"
(Xóa file khỏi Staging Area và ngừng theo dõi nhưng không xóa file trên máy.)
```

## Đổi tên hoặc di chuyển file

```
git mv "tên cũ" "tên mới"
(Đổi tên hoặc di chuyển file và đưa thay đổi vào Staging Area.)
```

Ví dụ:

```
git mv old.js new.js
```

---

# XÓA FILE KHÔNG ĐƯỢC GIT THEO DÕI

## Xem trước file sẽ bị xóa

```
git clean -n
(Hiển thị các file untracked sẽ bị xóa nhưng chưa thực sự xóa.)
```

## Xóa file untracked

```
git clean -f
(Xóa các file chưa được Git theo dõi.)
```

## Xóa file và thư mục untracked

```
git clean -fd
(Xóa file và thư mục chưa được Git theo dõi.)
```

Cảnh báo: File bị xóa bằng `git clean` thường rất khó khôi phục.

---

# TẠM CẤT THAY ĐỔI VỚI GIT STASH

## Tạm cất thay đổi

```
git stash
(Tạm lưu các thay đổi chưa commit và đưa Working Directory về trạng thái sạch.)
```

Có thể dùng dạng đầy đủ:

```
git stash push
```

## Tạm cất kèm nội dung mô tả

```
git stash push -m "Nội dung"
(Tạm lưu thay đổi và đặt tên mô tả.)
```

## Tạm cất cả file chưa được theo dõi

```
git stash -u
(Tạm lưu cả file untracked.)
```

## Xem danh sách stash

```
git stash list
(Hiển thị danh sách các lần tạm lưu.)
```

## Xem nội dung stash gần nhất

```
git stash show
(Hiển thị tóm tắt thay đổi trong stash gần nhất.)
```

## Xem chi tiết nội dung stash

```
git stash show -p
(Hiển thị chi tiết các dòng code trong stash gần nhất.)
```

## Khôi phục stash và xóa stash đó khỏi danh sách

```
git stash pop
(Áp dụng stash gần nhất vào Working Directory rồi xóa stash khỏi danh sách.)
```

## Khôi phục nhưng vẫn giữ stash

```
git stash apply
(Áp dụng stash gần nhất nhưng không xóa nó khỏi danh sách.)
```

## Khôi phục một stash cụ thể

```
git stash apply stash@{1}
(Áp dụng stash được chỉ định.)
```

## Xóa một stash

```
git stash drop stash@{0}
(Xóa stash được chỉ định.)
```

## Xóa toàn bộ stash

```
git stash clear
(Xóa toàn bộ danh sách stash.)
```

---

# BÀI HỌC VỀ THAO TÁC TỪ XA

## Git Remotes – Kho lưu trữ từ xa

Remote là địa chỉ liên kết repository trên máy với repository trên GitHub, GitLab hoặc máy chủ khác.

## Xem danh sách remote

```
git remote
(Hiển thị tên các remote.)
```

## Xem chi tiết remote

```
git remote -v
(Hiển thị tên và địa chỉ tải lên, tải xuống của các remote.)
```

Remote mặc định thường có tên:

```
origin
```

## Thêm remote

```
git remote add "tên remote" "đường dẫn repository"
(Kết nối repository local với repository từ xa.)
```

Ví dụ:

```
git remote add origin https://github.com/username/project.git
```

## Xem thông tin một remote

```
git remote show "tên remote"
(Hiển thị thông tin chi tiết của remote.)
```

Ví dụ:

```
git remote show origin
```

## Thay đổi đường dẫn remote

```
git remote set-url "tên remote" "đường dẫn mới"
(Thay đổi địa chỉ repository từ xa.)
```

Ví dụ:

```
git remote set-url origin https://github.com/username/new-project.git
```

## Đổi tên remote

```
git remote rename "tên cũ" "tên mới"
(Đổi tên remote.)
```

## Xóa remote

```
git remote remove "tên remote"
(Xóa kết nối remote khỏi repository local.)
```

Lệnh này không xóa repository trên GitHub.

---

# GIT FETCH

## Tải dữ liệu từ remote

```
git fetch
(Tải commit, nhánh và thông tin mới từ remote về máy nhưng không tự động gộp vào nhánh hiện tại.)
```

## Fetch từ một remote cụ thể

```
git fetch "tên remote"
(Tải dữ liệu từ remote được chỉ định.)
```

Ví dụ:

```
git fetch origin
```

## Fetch một nhánh cụ thể

```
git fetch origin "tên nhánh"
(Tải dữ liệu của một nhánh từ remote origin.)
```

## Fetch tất cả remote

```
git fetch --all
(Tải dữ liệu từ tất cả remote.)
```

## Xóa thông tin nhánh remote không còn tồn tại

```
git fetch --prune
(Cập nhật và xóa các remote-tracking branch đã bị xóa trên remote.)
```

Sau khi chạy `git fetch`, code trên nhánh hiện tại chưa thay đổi. Bạn có thể kiểm tra dữ liệu vừa tải bằng:

```
git log HEAD..origin/main --oneline
```

---

# GIT PULL

## Tải và gộp dữ liệu

```
git pull
(Tải dữ liệu mới từ remote rồi tích hợp vào nhánh hiện tại.)
```

Thông thường, lệnh này thực hiện:

```
git fetch
git merge
```

## Pull từ remote và nhánh cụ thể

```
git pull "tên remote" "tên nhánh"
(Tải và gộp nhánh remote được chỉ định vào nhánh hiện tại.)
```

Ví dụ:

```
git pull origin main
```

## Pull bằng rebase

```
git pull --rebase
(Tải dữ liệu mới rồi rebase các commit local lên trên dữ liệu remote.)
```

Lệnh này giúp lịch sử commit thẳng hơn nhưng cần xử lý cẩn thận nếu có xung đột.

## Chỉ cho phép fast-forward

```
git pull --ff-only
(Chỉ pull nếu Git có thể di chuyển nhánh thẳng tới commit mới mà không tạo merge commit.)
```

---

# GIT PUSH

## Đẩy commit lên remote

```
git push
(Đẩy các commit của nhánh hiện tại lên remote đã được thiết lập.)
```

## Đẩy một nhánh lên remote

```
git push "tên remote" "tên nhánh"
(Đẩy nhánh local được chỉ định lên remote.)
```

Ví dụ:

```
git push origin main
```

## Đẩy nhánh lần đầu và thiết lập upstream

```
git push -u origin "tên nhánh"
(Đẩy nhánh lên remote và thiết lập nhánh remote tương ứng làm upstream.)
```

Ví dụ:

```
git push -u origin feature-login
```

Sau lần đầu, có thể chỉ cần:

```
git push
```

## Đẩy tất cả nhánh

```
git push --all origin
(Đẩy tất cả nhánh local lên remote origin.)
```

## Xóa một nhánh trên remote

```
git push origin --delete "tên nhánh"
(Xóa nhánh được chỉ định trên remote.)
```

Ví dụ:

```
git push origin --delete feature-login
```

## Đẩy tag lên remote

```
git push origin "tên tag"
(Đẩy một tag lên remote.)
```

## Đẩy tất cả tag

```
git push origin --tags
(Đẩy toàn bộ tag lên remote.)
```

## Force push an toàn hơn

```
git push --force-with-lease
(Ép cập nhật nhánh remote nhưng kiểm tra xem remote có thay đổi mới của người khác hay không.)
```

Cảnh báo: Chỉ dùng khi hiểu rõ lịch sử nhánh đã bị viết lại, chẳng hạn sau khi rebase.

## Force push

```
git push --force
(Ép remote nhận lịch sử local và có thể ghi đè commit trên remote.)
```

Cảnh báo: Lệnh này có thể làm mất commit của người khác. Ưu tiên `--force-with-lease`.

---

# NHÁNH REMOTE VÀ UPSTREAM

## Xem nhánh nào đang theo dõi remote nào

```
git branch -vv
(Hiển thị nhánh local và upstream tương ứng.)
```

## Thiết lập upstream cho nhánh hiện tại

```
git branch --set-upstream-to=origin/"tên nhánh"
(Thiết lập nhánh remote mà nhánh hiện tại sẽ theo dõi.)
```

Ví dụ:

```
git branch --set-upstream-to=origin/main
```

## Tạo nhánh local từ nhánh remote

Cách hiện đại:

```
git switch -c "tên nhánh" --track origin/"tên nhánh"
(Tạo nhánh local và theo dõi nhánh remote.)
```

Cách thường dùng khi tên giống nhau:

```
git switch "tên nhánh"
(Git có thể tự tạo nhánh local nếu chỉ có một remote có nhánh cùng tên.)
```

Cách cũ:

```
git checkout -b "tên nhánh" origin/"tên nhánh"
```

---

# GIT TAG

Tag thường được dùng để đánh dấu một phiên bản quan trọng, ví dụ `v1.0.0`.

## Xem danh sách tag

```
git tag
(Hiển thị tất cả tag.)
```

## Tạo tag đơn giản

```
git tag "tên tag"
(Tạo tag tại commit hiện tại.)
```

Ví dụ:

```
git tag v1.0.0
```

## Tạo tag có nội dung mô tả

```
git tag -a "tên tag" -m "Nội dung"
(Tạo annotated tag có thông tin mô tả.)
```

Ví dụ:

```
git tag -a v1.0.0 -m "Phiên bản đầu tiên"
```

## Tạo tag tại một commit cụ thể

```
git tag "tên tag" "ID commit"
(Tạo tag tại commit được chỉ định.)
```

## Xem thông tin tag

```
git show "tên tag"
(Hiển thị thông tin của tag.)
```

## Xóa tag local

```
git tag -d "tên tag"
(Xóa tag trên máy.)
```

## Xóa tag trên remote

```
git push origin --delete "tên tag"
(Xóa tag trên remote.)
```

---

# XỬ LÝ XUNG ĐỘT

Xung đột có thể xảy ra khi merge, rebase, pull hoặc cherry-pick.

## Kiểm tra file bị xung đột

```
git status
(Hiển thị các file đang bị xung đột.)
```

Trong file bị xung đột, Git thường đánh dấu:

```
<<<<<<< HEAD
Code của nhánh hiện tại
=======
Code của nhánh được gộp
>>>>>>> tên nhánh
```

Các bước xử lý:

```
1. Mở file bị xung đột.
2. Chọn hoặc chỉnh sửa phần code cần giữ.
3. Xóa các dấu <<<<<<<, ======= và >>>>>>>.
4. Đưa file đã sửa vào Staging Area.
5. Tiếp tục thao tác Git.
```

Sau khi sửa xung đột merge:

```
git add .
git commit
```

Sau khi sửa xung đột rebase:

```
git add .
git rebase --continue
```

Sau khi sửa xung đột cherry-pick:

```
git add .
git cherry-pick --continue
```

---

# KHÔI PHỤC COMMIT BẰNG GIT REFLOG

## Xem lịch sử di chuyển của HEAD

```
git reflog
(Hiển thị lịch sử các vị trí mà HEAD từng trỏ tới.)
```

Lệnh này có thể giúp tìm lại commit sau khi dùng nhầm:

* `git reset --hard`
* `git rebase`
* `git commit --amend`
* Xóa hoặc di chuyển nhánh

Ví dụ kết quả:

```
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
e4f5g6h HEAD@{1}: commit: Thêm chức năng đăng nhập
```

Có thể khôi phục bằng cách tạo nhánh mới:

```
git branch "tên nhánh khôi phục" "ID commit"
```

Ví dụ:

```
git branch recover e4f5g6h
```

Hoặc reset về commit đó:

```
git reset --hard e4f5g6h
```

Cảnh báo: Kiểm tra kỹ trước khi dùng `--hard`.

---

# QUY TRÌNH GIT CƠ BẢN

## Lần đầu tạo dự án và đẩy lên GitHub

```
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin "link GitHub"
git push -u origin main
```

## Cập nhật code hằng ngày

```
git status
git add .
git commit -m "Mô tả thay đổi"
git pull --rebase
git push
```

## Làm chức năng mới trên nhánh riêng

```
git switch main
git pull
git switch -c feature-login
```

Sau khi viết code:

```
git add .
git commit -m "Thêm chức năng đăng nhập"
git push -u origin feature-login
```

Sau khi hoàn thành và muốn gộp vào `main`:

```
git switch main
git pull
git merge feature-login
git push
```

Sau khi gộp thành công:

```
git branch -d feature-login
git push origin --delete feature-login
```

---

# CÁC LỆNH GIT NGUY HIỂM CẦN CẨN THẬN

## Xóa toàn bộ thay đổi chưa commit

```
git reset --hard HEAD
```

## Xóa file chưa được Git theo dõi

```
git clean -fd
```

## Ép ghi đè lịch sử remote

```
git push --force
```

## Xóa nhánh chưa được merge

```
git branch -D "tên nhánh"
```

## Xóa toàn bộ stash

```
git stash clear
```

Trước khi sử dụng các lệnh trên, nên chạy:

```
git status
git log --oneline --graph --all
git reflog
```

---

# PHÂN BIỆT NHANH CÁC LỆNH DỄ NHẦM

## git fetch và git pull

```
git fetch
(Chỉ tải thông tin mới từ remote, chưa thay đổi code trên nhánh hiện tại.)

git pull
(Tải thông tin mới và tích hợp vào nhánh hiện tại.)
```

## git merge và git rebase

```
git merge
(Gộp hai lịch sử và có thể tạo merge commit.)

git rebase
(Tạo lại các commit của nhánh hiện tại trên một nền mới để lịch sử thẳng hơn.)
```

## git reset và git revert

```
git reset
(Di chuyển con trỏ nhánh và có thể thay đổi lịch sử.)

git revert
(Tạo commit mới để đảo ngược một commit cũ, không xóa lịch sử.)
```

## git restore và git reset

```
git restore
(Chủ yếu dùng để khôi phục file hoặc đưa file ra khỏi Staging Area.)

git reset
(Dùng để thay đổi HEAD, nhánh hoặc trạng thái của Staging Area.)
```

## git checkout và git switch

```
git checkout
(Lệnh cũ có nhiều chức năng: chuyển nhánh, chuyển commit và khôi phục file.)

git switch
(Lệnh mới, chủ yếu dùng để chuyển hoặc tạo nhánh.)
```

## git restore và git checkout file

```
git restore "tên file"
(Cách hiện đại để hủy thay đổi của file.)

git checkout -- "tên file"
(Cách cũ để hủy thay đổi của file.)
```

---

# CÂU LỆNH KIỂM TRA NHANH THƯỜNG DÙNG

```
git status
(Kiểm tra trạng thái dự án.)

git log --oneline --graph --decorate --all
(Xem toàn bộ lịch sử dưới dạng sơ đồ.)

git branch -a
(Xem tất cả nhánh local và remote.)

git remote -v
(Xem các remote và địa chỉ của chúng.)

git diff
(Xem code chưa được staged.)

git diff --staged
(Xem code đã được staged.)

git stash list
(Xem danh sách thay đổi đang tạm cất.)

git reflog
(Xem lịch sử di chuyển của HEAD.)
```
