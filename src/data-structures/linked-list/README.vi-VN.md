# Linked List

_Read this in other languages:_
[_简体中文_](README.zh-CN.md),
[_Русский_](README.ru-RU.md),
[_日本語_](README.ja-JP.md),
[_Português_](README.pt-BR.md),
[_한국어_](README.ko-KR.md),
[_Español_](README.es-ES.md),
[_Türkçe_](README.tr-TR.md),
[_Українська_](README.uk-UA.md),
[_Tiếng Việt_](README.vi-VN.md)

In computer science, a **linked list** is a linear collection
of data elements, in which linear order is not given by
their physical placement in memory. Instead, each
element points to the next. It is a data structure
consisting of a group of nodes which together represent
a sequence. Under the simplest form, each node is
composed of data and a reference (in other words,
a link) to the next node in the sequence. This structure
allows for efficient insertion or removal of elements
from any position in the sequence during iteration.
More complex variants add additional links, allowing
efficient insertion or removal from arbitrary element
references. A drawback of linked lists is that access
time is linear (and difficult to pipeline). Faster
access, such as random access, is not feasible. Arrays
have better cache locality as compared to linked lists.

Trong khoa học máy tính, danh sách liên kết là một tập hợp tuyến tính của các
thành phần tử dữ liệu, trong đó thứ tự tuyến tính không phải là sự lưu trữ trong bộ nhớ. 
Thay vào đó, mỗi phần tử chỉ đến một phần tử tiếp theo. Nó là một cấu trúc dữ liệu 
chứa một nhóm các node cùng nhau đại diện một trình tự. Dưới dạng đơn giản nhất,
mỗi node la sự tổng hợp  của dữ liệu và một đường dẫn tới node tiếp theo theo trình tự. 
Cấu trúc dữ liệu cho phép thêm và loại bỏ các phần tử từ bất kì vị trí nào mốt cách
dễ dang trong khi đang lặp qua (hoặc iterate: duyệt qua ) danh sách.
Có những biến thể phức tạp hơn với nhiều đường dẫn hơn trên một node,
cho phép thêm và loại bỏ một phần tử tuy ý một cách hiệu quả.
Một hạn chế của danh sách liên kết là thời gian truye cập (và khó định tuyến). 
Với sự truy cập nhanh, như truy cập ngẫu nhiên sẽ khó để thực thi.
Mảng sẽ có bộ đệm (cache)tốt hơn so với danh sách liên kết.

![Linked List](./images/linked-list.jpeg)

*Được làm bằng [okso.app](https://okso.app)*

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
    tail.next ← n
    tail ← n
  end if
end Add
```

```text
Prepend(value)
 Pre: value is the value to add to the list
 Post: value has been placed at the head of the list
 n ← node(value)
 n.next ← head
 head ← n
 if tail = ø
   tail ← n
 end
end Prepend
```

### Tìm kiếm

```text
Contains(head, value)
  Pre: head is the head node in the list
       value is the value to search for
  Post: the item is either in the linked list, true; otherwise false
  n ← head
  while n != ø and n.value != value
    n ← n.next
  end while
  if n = ø
    return false
  end if
  return true
end Contains
```

### Xóa/Loại bỏ

```text
Remove(head, value)
  Pre: head is the head node in the list
       value is the value to remove from the list
  Post: value is removed from the list, true, otherwise false
  if head = ø
    return false
  end if
  n ← head
  if n.value = value
    if head = tail
      head ← ø
      tail ← ø
    else
      head ← head.next
    end if
    return true
  end if
  while n.next != ø and n.next.value != value
    n ← n.next
  end while
  if n.next != ø
    if n.next = tail
      tail ← n
      tail.next = null
    else
      n.next ← n.next.next
    end if
    return true
  end if
  return false
end Remove
```

### Lặp qua/Duyệt qua

```text
Traverse(head)
  Pre: head is the head node in the list
  Post: the items in the list have been traversed
  n ← head
  while n != ø
    yield n.value
    n ← n.next
  end while
end Traverse
```

### Lặp qua/Duyệt qua trong trình tự đảo ngược

```text
ReverseTraversal(head, tail)
  Pre: head and tail belong to the same list
  Post: the items in the list have been traversed in reverse order
  if tail != ø
    curr ← tail
    while curr != head
      prev ← head
      while prev.next != curr
        prev ← prev.next
      end while
      yield curr.value
      curr ← prev
    end while
   yield curr.value
  end if
end ReverseTraversal
```

## Độ phức tạp

### Độ phức tạp thời gian

| Truy cập    | Tìm kiếm    | Thêm      | Xóa/Loại bỏ  |
| :---------: | :---------: | :-------: | :----------: |
| O(n)        | O(n)        | O(1)      | O(n)         |

### Độ phức tạp không gian

O(n)

## Nguồn tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Linked_list)
- [YouTube](https://www.youtube.com/watch?v=njTh_OwMljA&index=2&t=1s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
