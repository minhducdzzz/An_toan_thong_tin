#  Tìm nghịch đảo nhân trong GF(2¹⁰) bằng thuật toán Euclid mở rộng
## Sinh viên
* Họ và tên: Nguyễn Minh Đức
* MSSV: 20234001
## 1. Mô tả bài toán

Trong lý thuyết **trường hữu hạn GF(2ⁿ)**, mỗi phần tử được biểu diễn dưới dạng **đa thức nhị phân**.
Bài toán yêu cầu:

* Làm việc trong trường **GF(2¹⁰)**
* Đa thức tối giản (irreducible polynomial):

[
m(x) = x^{10} + x^3 + 1
]

* Hai phần tử cần tìm nghịch đảo:

```
a = 523
b = 1015
```

### Mục tiêu

Tìm:

[
a^{-1} \pmod{m(x)}
]

[
b^{-1} \pmod{m(x)}
]

sao cho:

[
a(x) \cdot a^{-1}(x) \equiv 1 \pmod{m(x)}
]

[
b(x) \cdot b^{-1}(x) \equiv 1 \pmod{m(x)}
]

Ngoài ra chương trình phải:

* In **từng bước của thuật toán Euclid mở rộng**
* Hiển thị các giá trị trung gian:

  * r(x)
  * q(x)
  * v(x)
  * w(x)

---

# 2. Biểu diễn phần tử trong GF(2¹⁰)

Các số nguyên được biểu diễn dưới dạng **đa thức nhị phân**.

Ví dụ:

### a = 523

Nhị phân:

```
523 = 1000001011
```

Đa thức:

[
a(x) = x^9 + x^3 + x + 1
]

---

### b = 1015

Nhị phân:

```
1015 = 1111110111
```

Đa thức:

[
b(x) = x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^2 + x + 1
]

---

# 3. Các phép toán trong GF(2)

Trong trường GF(2), các phép toán đa thức được thực hiện như sau:

| Phép toán | Cách thực hiện                |
| --------- | ----------------------------- |
| Cộng      | XOR                           |
| Trừ       | XOR                           |
| Nhân      | Nhân đa thức nhị phân         |
| Chia      | Chia đa thức                  |
| Mod       | Lấy phần dư theo đa thức m(x) |

Lưu ý:

```
+ = -
```

vì trong GF(2):

```
1 + 1 = 0
```

---

# 4. Thuật toán Euclid mở rộng cho đa thức

Thuật toán dùng để tìm:

[
gcd(a(x), b(x))
]

đồng thời tìm các đa thức:

[
v(x), w(x)
]

sao cho:

[
r(x) = a(x)v(x) + b(x)w(x)
]

Nếu:

```
gcd = 1
```

thì:

```
b⁻¹ = w(x)
```

---

# 5. Khởi tạo thuật toán

Ban đầu:

| i  | r(x) | v(x) | w(x) |
| -- | ---- | ---- | ---- |
| -1 | a(x) | 1    | 0    |
| 0  | b(x) | 0    | 1    |

---

# 6. Công thức lặp

Tại mỗi bước:

###  Chia đa thức

[
r_{i-2}(x) = q_i(x) r_{i-1}(x) + r_i(x)
]

###  Cập nhật hệ số

[
v_i(x) = v_{i-2}(x) - q_i(x)v_{i-1}(x)
]

[
w_i(x) = w_{i-2}(x) - q_i(x)w_{i-1}(x)
]

Trong GF(2):

```
- = XOR
```

---

# 7. Điều kiện dừng

Thuật toán dừng khi:

```
r(x) = 1
```

Lúc đó:

```
b⁻¹ = w(x)
```

---






