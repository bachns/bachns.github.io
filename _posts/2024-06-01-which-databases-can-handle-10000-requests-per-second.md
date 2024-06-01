---
layout: single
author_profile: true
title: Databases nào có thể xử lý hơn 10,000 request mỗi giây
excerpt: Hãy tỉnh táo lựa chọn CSDL đúng trước khi lưu trữ bất cứ cái gì
header:
  image: /assets/images/database.jpg
---

# Databases nào có thể xử lý hơn 10,000 request mỗi giây

Trước hết cần phải nói rằng:

1. Trừ khi anh em có dữ liệu lớn và phức tạp, còn không, anh em sẽ không bao giờ đạt đến giới hạn về khả năng của bất kỳ CSDL nào. Ngay cả với CSDL đơn giản như SQLite.

2. Kiến trúc dữ liệu cũng quan trọng như thiết kế ứng dụng, nếu không muốn nói là quan trọng hơn. Do vậy, thiết kế ứng dụng phải tuân theo kiến trúc dữ liệu.

Ok, còn giờ là những gợi ý để anh em chọn databases có khả năng xử lý hơn 10,000 request mỗi giây:

- Nếu phải sử dụng rất nhiều **các câu lệnh truy vấn đọc** một phần của bảng (hoặc nhiều bảng) thì CSDL loại SQL là phù hợp, như **MySQL, MariaDB, PostgreSQL.** Vì chúng được thiết kế chủ yếu cho việc này.

- Nếu phải sử dụng rất nhiều câu lệnh truy vấn đọc trên một phần nhỏ của **nhiều bảng nối (join table)** thì CSDL đồ thị (Graph Databases) là lựa chọn tốt. **Neo4J** là lựa chọn phổ biến nhất và cũng miễn phí.

- Nếu phải thực hiện một lượng rất lớn, hơn 10,000 **các lệnh ghi** vào bảng thì các loại CSDL cột (columnar DB) hoặc CSDL chuỗi thời gian (time-series DB) sẽ cho nhiều lợi thế, **Cassandra** và **Google BigTable** là các lựa chọn tốt. Hoặc CSDL là loại SQL Enterprise như **Oracle** thì cũng ngon. Ngoài ra còn một lựa chọn nữa cũng khá ổn là **MariaDB** (không phải MySQL nhé).

- Nếu phải thực hiện rất nhiều **các lệnh cật nhật (update)**, hơn 10,000 request đến một loạt các bảng khác nhau thì CSDL loại SQL là tốt nhờ khả năng cách ly dữ liệu của nó. **PostgreSQL** là lựa chọn tuyệt vời.

Gần đây với sự trỗi dậy của Nodejs, dẫn đến sự bùng nổ các chồng công nghệ front-end. **MongoDB** như là một sự lựa chọn hàng đầu trong nhiều chồng công nghệ đó, như: MEAN, MERN. Với khả năng lưu trữ tài liệu (Document Stores) loại JSON mạnh mẽ, tốc độ phản hồi nhanh. Tuy nhiên, xét về phương diện CSDL, tính nhất quán, tính ràng buộc thì **MongoDB** chưa bao giờ là CSDL tốt.
