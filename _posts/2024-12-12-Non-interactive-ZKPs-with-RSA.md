---
layout: single
classes: wide
title: Non-interactive ZKPs with RSA
excerpt: Chứng minh không tiết lộ tri thức không tương tác với RSA
header:
  image: /assets/images/cryptography-feature.jpg
---

**Phương** (P) muốn chính minh với **Vinh** (V) là cô ấy biết bí mật [m], tuy nhiên cô ấy không muốn tiết lộ [m] cho anh ta. Biết rằng [m] được mã hoá bằng RSA như sau:

$$
m^e \equiv c \ (mod\ N)
$$

Với (c, e, N) là công khai, chỉ [m] là bí mật. Làm sao chứng minh được điều đó mà không để lộ [m]?

Hãy cùng xem giao thức sau: 

1. Phương chọn ngẫu nhiên giá trị bí mật [r1], và tính nghịch đảo của nó INV[r1] rồi nhân với [m] (module N) để được r2. 

$$
r_2 = m * r_1^{-1} \ (mod\ N) 
$$

2. Phương tính tiếp x1 và x2 như sau: 

$$
x_1 = r_1^e \ (mod \ N) \\
x_2 = r_2^e \ (mod \ N)
$$

3. Vinh xác minh bằng cách tính: 

$$
x_1 * x_2 \equiv c \ (mod \ N)
$$

Nếu x1 * x2 bằng c thì Phương thực sự biết giá trị [m]. Như vậy, Vinh hoàn toàn bị thuyết phục là Phương biết giá trị [m], mà không hề biết được giá trị [m]. 

Thật vậy, ta có thể tính lại như sau: 

$$
x_1 * x_2 \equiv r_1 ^ e * r_2^e \equiv (r_1*r_2)^e \\
\equiv (r_1 * m * r_1^{-1})^e \equiv m^e \equiv c \ (mod \ N)
$$

Giao thức này có thể bị tấn công không? Câu trả lời là: **Có.** 

Phần tiếp theo sẽ trình bày một tấn công vào giao thức RSA ZKP này.