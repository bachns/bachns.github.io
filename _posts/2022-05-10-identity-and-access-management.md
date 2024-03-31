---
layout: single
author_profile: true
title: Quản lý danh tính và truy cập (IAM)
excerpt: Lỗi kinh hoàng vì có quá nhiều mật khẩu phải nhớ
header:
  teaser: /assets/images/iam.jpg
  overlay_image: /assets/images/iam.jpg
  overlay_filter: 0.5
toc: true
toc_sticky: true
---

# Vấn đề định danh và xác thực người dùng

Để truy cập vào mỗi ứng dụng, người dùng phải thực hiện chứng minh họ là ai với ứng dụng. Cách tiếp cận truyền thống là các ứng dụng sẽ thực hiện xác thực người dùng mỗi khi họ truy cập vào ứng dụng, và hình thức xác thực thường được sử dụng là khai báo tài khoản và mật khẩu.

Giả sử Alice muốn truy cập vào ứng dụng A. Ứng dụng A sẽ cần phải xác thực người đang muốn truy cập là ai và để làm điều đó nó sẽ yêu cầu người đang truy cập cung cấp tài khoản và mật khẩu. Alice lúc này sẽ khai báo tài khoản và mật khẩu của mình cho ứng dụng A. Ứng dụng A sẽ kiểm tra thông tin mà Alice vừa nhập, nếu đúng thì Alice đã được xác thực thành công và được truy cập vào ứng dụng A.

Việc này được lặp lại tương tự khi Alice truy cập vào ứng dụng B. Quá trình xác thực Alice cứ lặp đi lặp lại nhàm chán như vậy mỗi khi Alice truy cập vào các ứng dụng khác nhau. Hãy thử tưởng tượng, Alice sử dụng 20 ứng dụng khác nhau, và Alice sẽ phải nhớ 20 tài khoản và mật khẩu trên các ứng dụng đó để khai báo khi muốn truy cập. Thật là khủng khiếp khi phải ghi nhớ hết số đó và còn tệ hơn nữa khi số lượng ứng dụng mà Alice sử dụng ngày càng tăng.

Alice cũng không thể sử dụng một tài khoản và mật khẩu giống nhau cho tất cả ứng dụng, điều này chẳng mấy an toàn. Vì khi bị lộ mật khẩu, có thể do Alice hoặc do một ứng dụng nào đó thì sẽ ảnh hưởng đến tất cả các ứng dụng khác. Kẻ xấu có thể sử dụng mật khẩu bị đánh cắp để truy cập vào nhiều ứng dụng khác nhau.

## Mô hình khi Alice truy cập vào các ứng dụng

![](/assets/images/authentication-problem.jpg?raw=true)

Điều tồi tệ tiếp theo là thông tin danh tính, hồ sơ của Alice sẽ nằm rải rác ở tất cả các ứng dụng. Không có gì bảo đảm rằng các ứng dụng sẽ bảo vệ thông tin của Alice. Sự lộ lọt thông tin cá nhân rất dễ xảy ra, Alice càng sử dụng nhiều ứng dụng thì càng gia tăng nguy cơ bị xâm phạm dữ liệu cá nhân.

# Vậy có giải pháp nào cho vấn đề này không?

Câu trả lời là Có, và đó là lý do ra đời của các giải pháp Quản lý danh tính và truy cập (IAM - Identity and Access Management) và Đăng nhập một lần (SSO - Single Sign-On).

Lúc này Alice chỉ cần nhớ và sử dụng duy nhất một tài khoản của hệ thống IAM, và cũng chỉ cần xác thực với hệ thống IAM mà thôi. Sau khi quá trình xác thực Alice thành công, hệ thống IAM sẽ gửi thông tin danh tính của Alice cho ứng dụng mà Alice đang muốn truy cập.

## Mô hình khi Alice sử dụng IAM

![](/assets/images/alice-iam.png?raw=true)
