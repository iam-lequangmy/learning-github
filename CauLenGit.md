# CÁC CÂU LỆNH CƠ BẢN TRONG GIT

## 1. Lưu lại lịch sử thay đổi

```bash
git commit
```

Dùng để lưu lại các thay đổi của dự án thành một **commit** trong lịch sử Git.

Thông thường, ta sẽ thêm nội dung mô tả cho commit:

```bash
git commit -m "Nội dung mô tả thay đổi"
```

---

## 2. Làm việc với nhánh — Branch

### Tạo một nhánh mới

```bash
git branch ten-nhanh
```

Lệnh này chỉ tạo nhánh mới, nhưng chưa chuyển sang nhánh đó.

### Chuyển sang một nhánh khác

```bash
git checkout ten-nhanh
```

Lệnh này giúp chuyển từ nhánh hiện tại sang nhánh được chỉ định.

### Tạo nhánh mới và chuyển sang nhánh đó

```bash
git checkout -b ten-nhanh
```

Lệnh này thực hiện đồng thời hai thao tác:

1. Tạo một nhánh mới.
2. Chuyển sang nhánh vừa tạo.

---

## 3. Gộp nhánh bằng Merge

```bash
git merge ten-nhanh
```

Dùng để gộp nội dung của một nhánh khác vào **nhánh hiện tại**.

Ví dụ, muốn gộp nhánh `feature` vào nhánh `main`:

```bash
git checkout main
git merge feature
```

Sau khi chạy lệnh, các thay đổi từ nhánh `feature` sẽ được đưa vào nhánh `main`.

---

## 4. Gộp nhánh bằng Rebase

```bash
git rebase ten-nhanh
```

Dùng để đưa các commit của nhánh hiện tại lên phía sau các commit mới nhất của nhánh được chỉ định.

Ví dụ, muốn cập nhật nhánh `feature` dựa trên nhánh `main`:

```bash
git checkout feature
git rebase main
```

Git sẽ tạm thời lấy các commit riêng của nhánh `feature`, đặt nhánh này lên commit mới nhất của `main`, sau đó áp dụng lại các commit của `feature`.

Rebase giúp lịch sử commit thẳng và dễ theo dõi hơn. Tuy nhiên, không nên tùy ý rebase những commit đã được đẩy lên kho lưu trữ chung và đang được nhiều người sử dụng.
