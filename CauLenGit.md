# CÁC CÂU LỆNH GIT.

## Lưu lịch sử cập nhật code.
    git commit

## Nhánh trong git.
    git branch "Tên nhánh" (Tạo một nhánh mới)
    git checkout "Tên nhánh" (Chuyển sang nhánh mới)
    git checkout -b "Tên nhánh" (Tạo một nhánh mới và chuyển sang nhánh mới)

## Gộp nhánh trong git (C1: merge).
    git merge "Tên nhánh" (Gộp nhánh: "Tên nhánh" vào nhánh đang đứng)

## Gộp nhánh trong git (C2: rebase).
    git rebase "Tên nhánh" (Sao chép commit nhánh đang đứng path vào nhánh: "Tên nhánh")

## Dịch chuyển trong git (C1: tham chiếu tuyệt đối).
    git checkout "Id commit" (Di chuyển đến commit bất kỳ bằng: "ID") 

## Dịch chuyển trong git (C2: tham chiếu tương đối).
    git checkout "Tên nhánh, commit"^ (Chuyển đến commit cha của nhánh hoặc commit được chỉ định. Có thể thêm nhiều dấu ^ để lùi về nhiều thế hệ, ví dụ ^^)
    git checkout HEAD^ (Chuyển từ commit hiện tại đến commit cha của HEAD. Tương tự, có thể dùng nhiều dấu ^ để tiếp tục lùi về các commit tổ tiên.)

## Dịch chuyển trong git (C3: toán tử ~).
    git checkout HEAD~"số" (Chuyển HEAD đến commit tổ tiên cách commit hiện tại <số> bước)
    git branch -f "tên nhánh" HEAD~"số" (Ép nhánh được chỉ định trỏ đến commit tổ tiên cách vị trí hiện tại của HEAD <số> bước.)
    
## Hoàn tác trong git.
    git reset HEAD~"số" (Di chuyển nhánh hiện tại lùi về commit tổ tiên cách HEAD <số> bước.)
    git revert HEAD^ (Tạo một commit mới để đảo ngược các thay đổi của commit cha của HEAD)

## Dịch chuyển commit với git cherry-pick
    git cherry-pick "commit" "commit" ... (Lấy phần thay đổi của một hoặc nhiều commit được chỉ định và áp dụng chúng vào nhánh hiện tại.)

## Git Rebase Tương tác
    git rebase -i HEAD~"số" (Mở chế độ rebase tương tác để bạn chỉnh sửa <số> commit gần nhất tính từ HEAD)

## The Staging Area
    git status (Kiểm tra trạng thái các file)
    git add "tên file" (Đưa một file vào Staging Area)
    git add . (Đưa tất cả file đã thay đổi vào Staging Area)
    git commit -m "Nội dung" (Tạo commit từ các file trong Staging Area)
    .gitignore (Liệt kê các file hoặc thư mục Git không cần theo dõi)

## Undoing with git restore
    git restore --staged "tên file" (Đưa file ra khỏi Staging Area nhưng vẫn giữ phần đã sửa)
    git restore "tên file" (Hủy toàn bộ thay đổi chưa commit của file)


    
