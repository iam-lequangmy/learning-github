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