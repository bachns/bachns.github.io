---
layout: single
classes: wide
title: Bốn thế giới ảo và một thế giới thực
excerpt: Từ "P=NP" đến Mật mã hóa khóa công khai
header:
  image: /assets/images/cryptography-feature.jpg
---

Tác giả: Thầy **Phan Dương Hiệu**

Gần 20 năm trước, Russell Impagliazzo đưa ra định nghĩa rất thú vị về 5 thế giới khác nhau (cseweb.ucsd.edu/~russell/average.ps). Chúng ta sống ở một trong 5 thế giới đó, nhưng không biết chắc mình sống trong thế giới nào. Gần 20 năm trôi qua, vẫn chưa có thế giới nào chia tay chúng ta. Hiện vẫn đang có 4 thế giới ảo và một thế giới thực quanh ta, và ta không biết là mình đang ở đâu.

Đến một ngày, nếu có anh hùng nào may mắn chứng minh chúng ta đang thực sự sống ở đâu, thì cũng là ngày tận thế của 4 thế giới ảo còn lại, điều đó thật buồn và những người còn lại thật kém may... Chẳng hạn một chứng minh P=NP sẽ là ngày tận thế của 4 thế giới. Tuy nhiên, ta sẽ thấy rằng, một chứng minh P khác NP thì chỉ làm 1 thế giới tận thế và vẫn còn lại 4 thế giới lung linh :smile: Vì vậy, nếu Bụt hiện xuống và cho chọn giữa “ P=NP” hay “P khác NP” thì mình sẽ chọn P khác NP :laughing:

Impagliazzo minh họa 5 thế giới một cách rất xuất sắc để ai cũng hiểu được, thông qua câu chuyện tưởng tượng giữa thầy giáo Grouse và cậu học trò Gauss. Cậu trò Gauss thông minh nổi tiếng, trên lớp thầy giao bài nào cũng giải ngon ơ rồi rỗi rãi chọc phá các bạn làm thầy giáo rất là phiền lòng. Ông thầy Grouse quyết tâm tìm những bài toán siêu khó để nhằm mục đích làm cho Gauss bớt kiêu.

Và do đó dẫn tới 5 thế giới theo định nghĩa của Impagliazzo:

**Thế giới Algorithmica** (thuật toán), là nơi P = NP. Khi đó bài toán nào có khả năng kiểm tra lời giải cũng có khả năng tìm ra lời giải. Tức là mọi bài toán thực tế (là bài toán mà ta có thể kiểm tra xem một lời giải là đúng hay sai) đều giải được dễ dàng. Đó là thế giới chán ngán nhất, cái gì cũng giải được. Thật tội cho ông thầy Grouse, dù cố công cũng không thể tìm ra bài toán nào làm Gauss bó tay cả.

**Thế giới Heuristica** là nơi tuy NP khác P nhưng mọi bài toán NP đều có lời giải trong trường hợp trung bình (đầu vào của bài toán - instance - được chọn ngẫu nhiên theo một phân bố xác suất nào đó). Tức là sẽ có những bài toán khó giải trong trường hợp xấu nhất, nhưng mà không có cách gì tìm ra cái trường hợp xấu nhất đó. Mọi cách chọn bài toán đều dẫn tới bài toán dễ giải. Đây là trường hợp càng làm cho ông Grouse cảm thấy cay đắng: ông biết là Gauss không phải thượng đế, có những bài Gauss không giải được, nhưng ông không có cách nào tìm ra chúng. Bài nào mà ông lựa chọn thì Gauss đều giải được.

**Thế giới Pessiland** là nơi tồn tại các bài toán NP khó ngay cả trường hợp trung bình, nhưng không tồn tại hàm một chiều (one-way function). Hàm một chiều là hàm tính xuôi thì dễ mà tính ngược thì khó. Nói một cách trực quan, hàm một chiều cho phép ta sinh ra một bài toán khó giải từ lời giải của nó, tức là ta có thể sinh ra một bài toán khó kèm theo lời giải. Thế nhưng, trong Pessiland, giả thiết là không tồn tại hàm một chiều. Điều đó có nghĩa ông thầy Grouse có thể tìm ra những bài toán khó mà Gauss không giải được (vì tồn tại bài toán NP khó trong trường hợp trung bình), nhưng bản thân ông Grouse cũng không thể giải được bài toán đó (vì không tồn tại hàm một chiều). Đưa ra cho cả lớp một bài toán mà bản thân mình cũng không giải được, liệu ông Grouse có dám không ?

**Thế giới Minicrypt** là nơi tồn tại hàm một chiều one-way function nhưng không tồn tại mã hóa khóa công khai (public-key encryption). Cuối cùng cũng đã tới một thế giời mà ông Grouse có thể hài lòng: ông có thể ra những bài toán khó, Gauss không thể giải được và ông thì đĩnh đạc trình bày lời giải cho cả lớp! Tuy thế, ông chưa thật thỏa mãn, vì Gauss tuy không giải được, nhưng các bạn khác cũng chẳng ai giải được nên Gauss vẫn còn có thể tinh tướng.

**Thế giới Cryptomania** là nơi tồn tại mã hóa khóa công khai (public-key encryption). Với sự tồn tại mã hóa khóa công khai, ông thầy Grouse có thể dạy cho Gauss một bài học nhớ đời. Sự tồn tại mã hóa khóa công khai cũng có nghĩa là hai bên có thể trao đổi những thông điệp bí mật với nhau mà không cần phải chia sẻ, thống nhất bất cứ thông tin bí mật nào trước, và sự trao đổi là hoàn toàn công khai. Ở thế giới Cryptomania, ông thầy không những có thể ra những bài toán khó làm Gauss không thể giải được mà còn có thể đưa ra các gợi ý trên bảng để cho tất cả các học sinh đều giải được, trừ Gauss. Đây quả là một tình huống lý tưởng - Gauss trở thành cậu học sinh duy nhất trong lớp không giải được bài!

![](/assets/images/maths.png)

## Nói riêng về mật mã

Minicrypt là thế giới tối thiểu để có thể nói tới từ mật mã, mật mã chỉ tồn tại nếu có one-way function (xem thêm bài “Mật mã dưới góc nhìn độ phức tạp tính toán”).

Chúng ta đang được giả thuyết là sống trong thế giới Cryptomania. Các giao dịch ngân hàng, việc sử dụng thẻ tín dụng... đều có sử dụng public-key encryption. Tuy nhiên, độ an toàn của các hệ mã này đều dựa trên một giả thuyết nào đó, như là bài toán phân tích thành thừa số nguyên tố là khó, bài toán logarithm rời rạc trên nhóm các điểm trên đường cong elliptic là khó, hay tổng quát lên là tồn tại các hoán vị xuôi dễ ngược khó và có cửa lật (trapdoor permutation)…

Điều gì sẽ xảy ra khi một đêm, một siêu nhân từ đâu rơi xuống giải hết tuốt các bài toán tưởng là khó này, hủy diệt Cryptomania, đưa chúng ta trở lại thế giới Minicrypt?

Minicrypt, đó là thế giới nguyên thủy của mật mã, khi mật mã chưa là một ngành khoa học, tức là khi chưa có mật mã hóa khóa công khai. Ấy thế mà trong Minicrypt lại vẫn có rất nhiều thứ thú vị : vẫn sẽ tồn tại zero-knowledge proof, vẫn sẽ tồn tại chữ ký điện tử . Điều đặc biệt hay là chữ ký điện tử ra đời trên xương sống của mã hóa khóa công khai. Khi hệ mã RSA được đưa ra, người ta cứ nghĩ là mã hóa và chữ ký điện tử là hai quá trình ngược nhau: mã hóa thì dùng khóa công khai để mã và khóa bí mật để giải mã; còn chữ ký thì dùng khóa bí mật để ký và dùng khóa công khai để kiểm thử chữ ký. Tưởng vậy mà không phải là vậy, chúng nó ở hai thế giới khác nhau. (xem thêm bài “Vẻ đẹp bất định của mật mã hiện đại”)

Nếu tương lai chúng ta quay lại Minicrypt, đó không phải là thảm họa, mà sẽ là sự kỳ thú. Mật mã được đánh dấu bước chuyển mình từ nghệ thuật thành một ngành khoa học kể từ khi ra đời mật mã hóa khóa công khai. Để rồi khi nếu có chứng minh mã hóa công khai không tồn tại, mật mã lại trở về thời kỳ chỉ có mã hóa khóa bí mật. Lúc đó, có nghĩa chúng ta đi một vòng qua thế giới ảo Cryptomania, và chính nhờ cuộc thám hiểm ở xứ sở diệu kỳ đó sẽ đem về những thành quả thực vẫn sẽ tồn tại ngay trong Minicrypt: zero-knowledge proof và rộng hơn là các chứng minh tương tác (interactive proofs), chữ ký điện tử, khả năng thiết lập mọi trò chơi ảo như oẳn tù tì qua điện thoại...

Chính thế mà đôi lúc chúng ta nên giả vờ sống ở một thế giới ảo, và ngoài sự sung sướng được sống trong thế giới kỳ bí đó, thì khi quay trở lại thế giới thực ta còn có khi mang về những sáng tạo thực mà nếu sống mãi trong thế giới thực ta sẽ không thể tạo ra chúng.
