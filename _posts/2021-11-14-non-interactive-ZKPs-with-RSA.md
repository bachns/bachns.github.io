---
title: 'Non-interactive ZKPs with RSA'
date: 2021-11-14
permalink: /posts/21/11/non-interactive-ZKPs-with-RSA/
tags:
  - Cryptography
  - ZKP
---

ZKP không tương tác với RSA.

### Non interactive ZKPs with RSA

**Phương** (P) muốn chính minh với **Vinh** (V) là cô ấy biết bí mật \\(m\\), tuy nhiên cô ấy không muốn tiết lộ \\(m\\) cho anh ta. Biết rằng \\(m\\) được mã hoá bằng RSA như sau:

$$
m^e \equiv c \ (mod\ N)
$$

Với \\((c, e, N)\\) là công khai, chỉ \\(m\\) là bí mật. Làm sao chứng minh được điều đó mà không để lộ \\(m\\)?

Hãy cùng xem giao thức không tương tác sau:

Bước 1. Phương chọn ngẫu nhiên giá trị bí mật \\(r_1\\), và tính nghịch đảo của nó là \\(r_1^{-1}\\) rồi nhân với \\(m \ (mod \ N)\\) để được \\(r_2\\), như dưới: 

$$
r_2 = m * r_1^{-1} \ (mod\ N) 
$$

Bước 2. Phương tính tiếp \\(x_1\\) và \\(x_2\\) để làm bằng chứng, sau đó gửi cặp giá trị này cho Vinh, cách tính \\(x_1\\), \\(x_2\\) như sau: 

$$
x_1 = r_1^e \ (mod \ N)
$$

$$
x_2 = r_2^e \ (mod \ N)
$$

Bước 3. Vinh xác minh bằng cách tính: 

$$
x_1 * x_2 \equiv c' \ (mod \ N)
$$

Nếu \\(c'\\) bằng \\(c\\) thì Phương thực sự biết giá trị \\(m\\). Như vậy, Vinh **hoàn toàn bị thuyết phục** là Phương biết giá trị \\(m\\), mà **không hề biết được gì** về giá trị \\(m\\).

### Thật vậy

\\(c'\\) bằng \\(c\\) chỉ khi \\(x_1\\) và \\(x_2\\) là bằng chứng thực sự. Ta có thể tính lại như sau: 

$$
x_1 * x_2 \equiv r_1 ^ e * r_2^e \equiv (r_1*r_2)^e \\
\equiv (r_1 * m * r_1^{-1})^e \equiv m^e \equiv c \ (mod \ N)
$$

### Nhắc lại chút

| Giá trị công khai | Giá trị bí mật |
| ------------------| -------------- |
| \\(c, e, N, x_1, x_2\\) |\\(m, r_1, r_2\\)|

## Ví dụ

Hãy xem một ví dụ với những con số để xem cách giao thức này hoạt động như thế nào:

Giả sử ta có: 

$$
\begin{split}
  m &= 88 \\
  N &= 2430101 \\
  e &= 9007
\end{split}
$$

Và giá trị \\(c\\) sẽ là:

$$
\begin{split}
  m^e &\equiv c\ (mod\ N) \\
  88^{9007} &\equiv 160613\ (mod\ 2430101)
\end{split}
$$

### Bây giờ hãy bắt đầu giao thức

Phương chọn một số ngẫu nhiên:

$$
  r_1 = 67
$$

* Bước 1. Phương tính \\(r_2\\):
  
  Trước hết cần tính \\(x = r_1^{-1}\\) chính là giá trị nghịch đảo của \\(r_1\\), và sau đó sẽ nhân \\(x\\) nó với \\(m\\).

$$
  \begin{split}
      67 * x &\equiv 1\ (mod\ 2430101) \\
      x &= 217621 \\
      \\
      m* x &\equiv r_2\ (mod\ N) \\
      88 * 217621 &\equiv 2139941\ (mod\ 2430101)
  \end{split}
$$

  Vì vậy chúng ta có \\(r_2 = 2139941\\)

* Bước 2. Phương tính \\(x_1\\) và \\(x_2\\):

$$
  \begin{split}
      x_1 &\equiv r_1^e\ (mod\ N) \\
      67^{9007} &= 1587671\ (mod\ 2430101) \\
      x_1 &= 1587671 \\
      \\
      x_2 &\equiv r_2^e\ (mod\ N) \\
      2139941^{9007} &\equiv 374578\ (mod\ 2430101) \\
      x_2 &= 374578
  \end{split}
$$

  Phương gửi \\((x_1, x_2)\\) là \\((1587671, 374578)\\) cho Vinh.

* Bước 3. Cuối cùng, Vinh có thể xác minh như sau:

$$
  \begin{split}
    x_1 * x_2 &\equiv c'\ (mod\ N) \\
    1587671 * 374578 &\equiv 160613\ (mod\ 2430101) \\
    160613 &= c' \\
    \\
    c' = c\ (TRUE)
  \end{split}
$$

Ok !!! vậy giao thức này có thể bị tấn công không? Câu trả lời là: **Có.** 

Bài sau sẽ trình bày một tấn công vào giao thức này.