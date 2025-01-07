---
title: 'Non-interactive ZKPs with RSA'
date: 2021-11-14
permalink: /posts/21/11/non-interactive-ZKPs-with-RSA/
tags:
  - Cryptography
  - ZKP
---

Chứng minh không tiết lộ tri thức không tương tác với RSA.

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


Ok !!! vậy giao thức này có thể bị tấn công không? Câu trả lời là: **Có.** 

Bài sau sẽ trình bày một tấn công vào giao thức này.