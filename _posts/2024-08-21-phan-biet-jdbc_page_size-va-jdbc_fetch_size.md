---
layout: single
classes: wide
author_profile: true
title: Phân biệt jdbc_page_size và jdbc_fetch_size trong Input Plugin JDBC của Logstash
header:
  image: /assets/images/elk-stack.webp
---

`jdbc_page_size` và `jdbc_fetch_size` là hai tùy chọn cấu hình trong input plugin JDBC của Logstash, nhưng chúng có vai trò khác nhau trong việc quản lý cách dữ liệu được tải từ cơ sở dữ liệu:

1. **`jdbc_page_size`**:
   - **Mục đích**: Định nghĩa số lượng bản ghi (rows) được truy vấn mỗi lần Logstash thực hiện truy vấn SQL. Khi sử dụng tùy chọn này, Logstash sẽ chia kết quả truy vấn thành nhiều "trang" (pages), mỗi trang chứa `jdbc_page_size` bản ghi.
   - **Ví dụ**: Nếu bạn có 10,000 bản ghi trong bảng và `jdbc_page_size` được thiết lập là `1000`, Logstash sẽ chia kết quả thành 10 trang, mỗi trang chứa 1000 bản ghi. Logstash sẽ thực hiện 10 lần truy vấn (hoặc fetch) để lấy tất cả dữ liệu.
2. **`jdbc_fetch_size`**:
   - **Mục đích**: Định nghĩa số lượng bản ghi mà driver JDBC tải về bộ nhớ của Logstash trong một lần fetch từ cơ sở dữ liệu. Tùy chọn này điều chỉnh hiệu suất bằng cách kiểm soát kích thước lô (batch) dữ liệu mà driver JDBC sẽ lấy từ cơ sở dữ liệu trong mỗi lần kết nối.
   - **Ví dụ**: Nếu `jdbc_fetch_size` được thiết lập là `500`, driver JDBC sẽ cố gắng lấy 500 bản ghi mỗi lần từ cơ sở dữ liệu, giảm bớt lượng bộ nhớ tiêu thụ khi thực hiện một truy vấn lớn.

### Ví dụ

Giả sử bạn có một bảng `orders` với 20,000 bản ghi và bạn cấu hình Logstash như sau:

```bash
input {
  jdbc {
    jdbc_driver_library => "path/to/your/jdbc/driver.jar"
    jdbc_driver_class => "com.mysql.jdbc.Driver"
    jdbc_connection_string => "jdbc:mysql://localhost:3306/your_database"
    jdbc_user => "your_username"
    jdbc_password => "your_password"
    statement => "SELECT * FROM orders"

    jdbc_page_size => 5000
    jdbc_fetch_size => 1000
  }
}

output {
  stdout { codec => json_lines }
}
```

- **`jdbc_page_size => 5000`**: Logstash sẽ chia kết quả truy vấn thành 4 "trang", mỗi trang chứa 5000 bản ghi. Vì bảng `orders` có 20,000 bản ghi, Logstash sẽ thực hiện 4 lần truy vấn để lấy đủ toàn bộ dữ liệu.
- **`jdbc_fetch_size => 1000`**: Khi mỗi trang được truy xuất, driver JDBC sẽ lấy dữ liệu về bộ nhớ của Logstash theo từng lô 1000 bản ghi, giảm thiểu tải bộ nhớ trong khi vẫn đảm bảo hiệu suất.

### Tóm Lại

- **`jdbc_page_size`**: Xác định số lượng bản ghi mà Logstash sẽ xử lý trong một lần truy vấn lớn.
- **`jdbc_fetch_size`**: Xác định số lượng bản ghi mà driver JDBC sẽ tải về từ cơ sở dữ liệu trong một lần fetch.

Việc kết hợp đúng giữa `jdbc_page_size` và `jdbc_fetch_size` giúp tối ưu hóa hiệu suất tải dữ liệu mà không gây quá tải bộ nhớ hoặc làm chậm quá trình xử lý.
