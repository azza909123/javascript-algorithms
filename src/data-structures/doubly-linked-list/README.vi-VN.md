# Danh sách liên kết đôi

_Đọc với ngôn ngữ khác:_
[_Русский_](README.ru-RU.md),
[_简体中文_](README.zh-CN.md),
[_日本語_](README.ja-JP.md),
[_Português_](README.pt-BR.md),
[_한국어_](README.ko-KR.md),
[_Español_](README.es-ES.md),
[_Українська_](README.uk-UA.md),
[_Tiếng Việt_](README.vi-VN.md)

Trong khoa học máy tính, **danh sách liên kết kép** là một cấu trúc dữ liệu liên kết
gồm một tập hợp các bản ghi liên kết tuần tự được gọi là node. Mỗi node chứa hai trường, 
được gọi là liên kết, các liên kết chhir đến node trước và node tiếp theo trong chuỗi các node. 
Các liên kết trước và tiếp theo của các nút đầu và cuối, tương ứng, trỏ đến một loại kết thúc, 
thường là một nút báo hiệu hoặc null, để thuận tiện cho việc duyệt qua danh sách. Nếu chỉ có một node, 
thì danh sách được liên kết theo vòng tròn thông qua node đó. Nó có thể được hình dung như hai danh sách liên
kết đơn được hình thành từ các mục dữ liệu giống nhau, nhưng theo thứ tự tuần tự đối diện nhau.

![Danh sách liên kết đôi](./images/doubly-linked-list.jpeg)

_Làm với [okso.app](https://okso.app)_

2 đầu liên kết của node cho phép duyệt qua cả hai hướng (trước và tiếp theo). Trong khi đó, 
thêm hoặc loại bỏ một node trong một danh sách liên kết kép yêu cầu thay đổi nhiều 
liên kết hơn so với phép toán tương tự với danh sách liên kết đơn, phép toán của danh sách liên kết
đơn đơn giản và có khả năng hiệu quả hơn vì ko cần phải theo dõi node trước trong khi duyệt qua hoặc 
không cần phải duyệt qua danh sách để tìm một node trước đó, nên các liên kết của danh sách liên kết đơn có thể điều chỉnh.

## Mã giả (pseudocode) cho các phép toán cơ bản

### Thêm

```text
Add(value)
  Pre: value is the value to add to the list
  Post: value has been placed at the tail of the list
  n ← node(value)
  if head = ø
    head ← n
    tail ← n
  else
    n.previous ← tail
    tail.next ← n
    tail ← n
  end if
end Add
```

### Xóa / Loại bỏ

```text
Remove(head, value)
  Pre: head is the head node in the list
       value is the value to remove from the list
  Post: value is removed from the list, true; otherwise false
  if head = ø
    return false
  end if
  if value = head.value
    if head = tail
      head ← ø
      tail ← ø
    else
      head ← head.next
      head.previous ← ø
    end if
    return true
  end if
  n ← head.next
  while n != ø and value !== n.value
    n ← n.next
  end while
  if n = tail
    tail ← tail.previous
    tail.next ← ø
    return true
  else if n != ø
    n.previous.next ← n.next
    n.next.previous ← n.previous
    return true
  end if
  return false
end Remove
```

### Duyệt qua với trình tự đảo ngược

```text
ReverseTraversal(tail)
  Pre: tail is the node of the list to traverse
  Post: the list has been traversed in reverse order
  n ← tail
  while n != ø
    yield n.value
    n ← n.previous
  end while
end Reverse Traversal
```

## Độ phức tạp 

## Độ phức tạp của thời gian

| Truy cập | Tìm kiếm | Thêm      | Xóa/Loại bỏ |
| :------: | :------: | :-------: | :---------: |
|  O(n)    |  O(n)    |   O(1)    |   O(n)      |

### Độ phức tạp của thời gian

O(n)

## Nguồn

- [Wikipedia](https://en.wikipedia.org/wiki/Doubly_linked_list)
- [YouTube](https://www.youtube.com/watch?v=JdQeNxWCguQ&t=7s&index=72&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
