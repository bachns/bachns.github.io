---
layout: single
author_profile: true
title: Nói nhanh về một số CSDL
excerpt: Phân loại và kể một số loại cơ sở dữ liệu mới lạ
header:
  teaser: /assets/images/database.webp
  overlay_image: /assets/images/database.webp
  overlay_filter: 0.5
toc: true
toc_sticky: true
---

# Nói nhanh về một số CSDL

Nhóm cơ sở dữ liệu SQL như **MySQL, PostgreSQL** thì thôi khỏi phải nói vì nó đã quá rõ và phổ biến rồi. Chúng ta sẽ chỉ nói về những cái mới mẻ và lạ lẫm thôi.

## 1. NoSQL Databases

### **Apache Casaandra**

**Casaandra** là một cơ sở dữ liệu NoSQL có khả năng mở rộng cao, được thiết kế để xử lý một lượng lớn dữ liệu thông qua nhiều máy chủ mà không có bất kỳ “điểm yếu chí tử “ (single point of failure) nào. Nó sử dụng kiến trúc phi tập trung và các **hash table** phân tán để bảo đảm tính khả dụng và hiệu năng cao.

### **MongoDB**

**MongoDB** là một cơ sở dữ liệu NoSQL hướng tài liệu, được thiết kế để có thể mở rộng theo chiều ngang bằng cách thêm nhiều máy chủ vào cụm (cluster). Nó hỗ trợ phân chia dữ liệu (sharding) tức là một CSDL lớn được phân chia thành nhiều CSDL nhỏ hơn nằm phân tán ở nhiều node. Điều này cho phép nó có thể xử lý một lượng lớn các request yêu cầu.

## **2. In-memory Databases**

Nhóm cơ sở dữ liệu này là không thể thiếu nếu anh em muốn xây dựng một hệ thống web ở mức độ chuyên nghiệp, hàng triệu người dùng.

### Redis

**Redis** khá là phổ biến nên chắc hẳn nhiều người đã từng nghe về nó. Redis là một cơ sở dữ liệu phân tán in-memory mã nguồn mở, được sử dụng như một CSDL bộ đệm (cache), lưu trữ dữ liệu dạng cặp key-value thông qua **Message Broker** trong bộ nhớ, trong khoảng thời gian tùy chọn. Nó được biết đến vì có hiệu năng cao, khả năng xử lý một lượng lớn các yêu cầu trong một giây nhờ giữ dữ liệu trong memory.

### **Memcached**

**Memcached** là một hệ thống lưu trữ dữ liệu và các đối tượng (_objects_) có tần suất truy cập nhiều để tăng tốc độ truy xuất. Memcached thường được sử dụng để tối ưu hóa việc tải dữ liệu từ cơ sở dữ liệu cho các ứng dụng trên nền web. Nhờ lưu trữ dữ liệu và đối tượng trong RAM nên memcached giúp giảm số lần phải đọc nguồn dữ liệu ngoài.

## **3. Time-series Databases**

Nhóm cơ sở dữ liệu này anh em sẽ phải đụng đến khi làm về giám sát.

### Prometheus

**Prometheus** là cơ sở dữ liệu chuỗi thời gian mã nguồn mở được phát triển bởi SoundCloud. Prometheus đảm nhiệm vai trò lưu trữ cho hệ thống giám sát. Lấy cảm hứng từ hệ thống Gorilla tại Facebook, nó được thiết kế đặc biệt để giám sát và thu thập số liệu. Prometheus có thể chứa mô hình dữ liệu nhiều chiều do người dùng xác định, và một ngôn ngữ truy vấn trên dữ liệu nhiều chiều được gọi là PromQL. Ngoài lưu trữ đĩa cục bộ, Prometheus còn có tích hợp lưu trữ từ xa thông qua Protocol Buffer.

### **InfluxDB**

**InfluxDB** là cơ sở dữ liệu chuỗi thời gian được tối ưu hóa để xử lý khối lượng lớn dữ liệu được đánh dấu timestamp. Nó lưu trữ tuân theo mô hình cây LSM, và được thiết kế để lưu trữ và truy vấn dữ liệu theo thời gian một cách hiệu quả, giúp dữ liệu này phù hợp với các trường hợp sử dụng như giám sát, IoT và phân tích thời gian thực.

## 4. NewSQL Databases

Nhóm này khá là mới mẻ và lạ lẫm. Nhưng thôi, kệ đi, kiến thức càng tiếp thu nhiều càng tốt.

### **CockroachDB**

**CockroachDB** là một cơ sở dữ liệu SQL phân tán, được thiết kế để có tính khả dụng cao và khả năng mở rộng tổng quát (global scalability). CockroachDB lưu trữ các bản sao dữ liệu ở nhiều vị trí địa lý khác nhau để mang lại khả năng truy cập nhanh chóng ở bất kì đâu. Nó sử dụng kiến trúc phân tán lấy cảm hứng của Google Spanner để cung cấp tính nhất quán mạnh mẽ và khả năng xử lý số lượng yêu cầu lớn.

### **VoltDB**

**VoltDB** là một cơ sở dữ liệu NewSQL in-memory (trong bộ nhớ) được tối ưu hóa để xử lý giao dịch tốc độ cao. Nó sử dụng kiến trúc phân tán và in-memory để đạt được thông lượng cao, độ trễ thấp cho khối lượng công việc OLTP (Online Transactional Processing).

## **5. Columnar Databases**

Nhóm cơ sở dữ liệu này có cái tên cũng khá thú vị là **“CSDL cột”,** trước giờ chỉ thấy bản ghi, **hàng** trong bảng thôi. Ấy thế mà khi anh em làm về **Big Data, Data Lake, Data Warehouse** thường sẽ đụng đến nó.

**Apache HBase**

**HBase** là cơ sở dữ liệu mã nguồn mở, phân tán, không quan hệ, hướng cột (column-oriented database) được xây dựng dựa trên HDFS của Hadoop. Nó được thiết kế để xử lý lượng lớn dữ liệu thưa thớt và có thể mở rộng theo chiều ngang để xử lý tỷ lệ yêu cầu cao. HBase cho phép truy cập ngẫu nhiên, hoàn toàn nhất quán, theo thời gian thực vào hàng **petabyte** dữ liệu.

**Túm lại thì nói nhanh qua thế đã, để cho anh em nắm được sơ bộ và định hình qua về chúng.**
