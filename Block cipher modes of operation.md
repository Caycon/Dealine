# Block cipher modes of operation:

- Block cipher modes of operation là các phương thức hoạt động được sử dụng để mở rộng khả năng của một thuật toán mã hóa khối (block cipher) trong việc mã hóa dữ liệu có kích thước lớn hơn kích thước của khối mã hóa đơn lẻ. Đây là những quy tắc hoạt động được áp dụng cho việc mã hóa dữ liệu có kích thước dài hơn một khối mã hóa đơn lẻ của block cipher. Một số block cipher modes of operation phổ biến bao gồm:

  - `ECB (Electronic Codebook)`: Đây là phương thức đơn giản nhất, trong đó mỗi khối dữ liệu được mã hóa độc lập với cùng một khóa. Tuy nhiên, ECB có nhược điểm là không an toàn, vì các khối dữ liệu giống nhau sẽ được mã hóa thành mã đồng nhất, không giấu được cấu trúc của dữ liệu gốc.

  - `CBC (Cipher Block Chaining)`: Đây là phương thức mà mỗi khối dữ liệu được mã hóa kết hợp với khối dữ liệu trước đó trước khi tiến hành mã hóa, giúp đảm bảo tính riêng tư và ngăn chặn việc tiết lộ cấu trúc của dữ liệu gốc.

  - `CFB (Cipher Feedback)`: Đây là phương thức mà mỗi khối dữ liệu được dùng để mã hóa phần tử dữ liệu của khối tiếp theo, tạo thành một chuỗi phụ thuộc dữ liệu giúp đồng bộ giữa khối dữ liệu gốc và khối mã hóa.

  - `OFB (Output Feedback)`: Đây là phương thức mà mỗi khối dữ liệu được dùng để mã hóa phần tử của chuỗi khóa ngẫu nhiên, sau đó kết quả mã hóa được dùng để tạo khóa mới cho khối tiếp theo.

  - `CTR (Counter)`: Đây là phương thức mà mỗi khối dữ liệu được mã hóa bằng cách sử dụng một chuỗi số nguyên liên tiếp được gọi là "counter" làm khóa, thay đổi theo mỗi khối dữ liệu.

- Mỗi phương thức có ưu điểm và nhược điểm riêng, và việc lựa chọn phương thức thích hợp phụ thuộc vào yêu cầu của ứng dụng cụ thể, bao gồm tính bảo mật, tính hiệu suất, tính tiện dụng, và khả năng mở rộng.
-------
## ECB (Electronic Codebook):
- ECB (Electronic Codebook) là một phương thức hoạt động của block cipher, trong đó mỗi khối dữ liệu đầu vào được mã hóa độc lập với cùng một khóa, mà không có sự phụ thuộc vào các khối dữ liệu hay kết quả mã hóa của các khối trước đó. Cơ chế hoạt động của ECB được mô tả như sau:

  - Chia dữ liệu thành các khối con: Dữ liệu đầu vào được chia thành các khối con có cùng kích thước với khối mã hóa của block cipher. Các khối con này độc lập với nhau và không có sự phụ thuộc vào các khối dữ liệu hay kết quả mã hóa của các khối trước đó.

  - Mã hóa các khối con: Mỗi khối con được mã hóa độc lập bằng cùng một khóa sử dụng block cipher. Quá trình mã hóa được thực hiện bằng cách áp dụng thuật toán mã hóa của block cipher lên từng khối con, đầu ra của quá trình này là các khối mã hóa.

  - Ghép các khối mã hóa: Các khối mã hóa đầu ra từ bước trước được ghép lại để tạo thành dữ liệu đã được mã hóa. Các khối mã hóa được ghép lại theo thứ tự của các khối con tương ứng trong dữ liệu đầu vào.

  - Kết quả mã hóa: Kết quả của quá trình mã hóa là dữ liệu đã được mã hóa bằng ECB, có cùng kích thước với dữ liệu đầu vào.

- Cơ chế hoạt động của ECB đơn giản và dễ hiểu, tuy nhiên nó có nhược điểm là không đảm bảo tính riêng tư và bảo mật cao, do các khối dữ liệu giống nhau sẽ được mã hóa thành mã đồng nhất. Vì vậy, ECB không được khuyến cáo sử dụng trong việc mã hóa dữ liệu nhạy cảm, và các phương thức hoạt động khác như CBC, CFB, OFB, hoặc CTR thường được sử dụng thay thế.
##### Tìm hiểu kỹ hơn về `ECB` [tại đây](https://www.techtarget.com/searchsecurity/definition/Electronic-Code-Book)
-------
## CBC (Cipher Block Chaining):
- CBC (Cipher Block Chaining) là một trong những phương thức hoạt động của block cipher modes of operation, được sử dụng để mã hóa dữ liệu theo cách thức chuỗi các khối dữ liệu lại với nhau. Trong CBC, mỗi khối dữ liệu được mã hóa trước khi được kết hợp với khối dữ liệu trước đó trong chuỗi, từ đó tạo thành khối dữ liệu đầu vào cho khối dữ liệu tiếp theo.

- Cơ chế hoạt động của CBC được mô tả như sau:

  - Khởi tạo vector khởi đầu (IV): Một vector khởi đầu (IV) được sinh ra ngẫu nhiên và được sử dụng làm giá trị đầu vào cho khối dữ liệu đầu tiên trong chuỗi.

  - Chia dữ liệu thành các khối con: Dữ liệu đầu vào được chia thành các khối con có cùng kích thước với khối mã hóa của block cipher.

  - Pha XOR với IV hoặc khối dữ liệu trước đó: Để tạo sự phụ thuộc giữa các khối dữ liệu trong chuỗi, mỗi khối dữ liệu con (trừ khối đầu tiên) được thực hiện phép XOR với khối dữ liệu trước đó trong chuỗi hoặc với IV.

  - Mã hóa các khối con: Mỗi khối con, sau khi đã được thực hiện phép XOR với IV hoặc khối dữ liệu trước đó, sẽ được mã hóa bằng cùng một khóa sử dụng block cipher.

  - Ghép các khối mã hóa: Các khối mã hóa đầu ra từ bước trước được ghép lại để tạo thành dữ liệu đã được mã hóa.

  - Kết quả mã hóa: Kết quả của quá trình mã hóa là dữ liệu đã được mã hóa bằng CBC.

  - Sau khi quá trình mã hóa hoàn tất, IV và dữ liệu đã được mã hóa sẽ được truyền đi hoặc lưu trữ. Khi giải mã, quá trình tương tự được thực hiện với việc sử dụng khóa giải mã để giải mã các khối dữ liệu đã được mã hóa trong chuỗi, sau đó thực hiện phép XOR với IV hoặc khối dữ liệu trước đó để khôi phục lại dữ liệu gốc.

- CBC được sử dụng phổ biến trong nhiều ứng dụng mã hóa dữ liệu, bao gồm bảo mật dữ liệu trên mạng, mã hóa dữ liệu đăng nhập, và các ứng dụng khác đòi hỏi tính bảo mật cao.  
##### Tìm hiểu kỹ hơn về `CBC` [tại đây](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#Cipher-block_chaining_(CBC)).  
-------
## CFB (Cipher Feedback):
- CFB (Cipher Feedback) là một trong các chế độ hoạt động của các thuật toán mã hóa khối (block cipher) trong mật mã học. Nó cho phép mã hóa các khối dữ liệu có kích thước nhỏ hơn kích thước khối đầu vào của thuật toán mã hóa khối, và cũng cho phép mã hóa đầu ra phụ thuộc vào các khối dữ liệu trước đó, tạo ra tính toàn vẹn (integrity) cho dữ liệu được mã hóa.

- Cơ chế hoạt động của CFB là:

  - Đầu tiên, một vector khởi động (Initialization Vector - IV) được sử dụng để khởi tạo quá trình mã hóa. IV là một chuỗi ngẫu nhiên có cùng kích thước với kích thước khối của thuật toán mã hóa khối.

  - IV sau đó được mã hóa bằng thuật toán mã hóa khối để tạo ra một khối mã hóa đầu tiên (còn gọi là khối feedback).

  - Khối feedback này sau đó được kết hợp với khối dữ liệu gốc (plain text) thông qua phép XOR (hoặc phép cộng modulo 2).

  - Kết quả của phép XOR được đưa vào đầu vào của thuật toán mã hóa khối để tạo ra khối mã hóa tiếp theo.

  - Quá trình mã hóa được lặp lại cho tới khi tất cả các khối dữ liệu đầu vào được mã hóa.

- Lợi ích của CFB là nó cho phép mã hóa các khối dữ liệu có kích thước nhỏ hơn kích thước khối của thuật toán mã hóa khối, đồng thời cũng cho phép mã hóa đầu ra phụ thuộc vào các khối dữ liệu trước đó, đồng nghĩa với việc nó cung cấp tính toàn vẹn cho dữ liệu được mã hóa. Tuy nhiên, nhược điểm của CFB là nó không thích hợp cho việc mã hóa đồng thời (parallel encryption) và có thể dẫn đến vấn đề phụ thuộc giữa các khối dữ liệu.
##### Tìm hiểu kỹ hơn về CFB [tại đây](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
-------
### OFB (Output Feedback):
- OFB (Output Feedback) là một trong những chế độ hoạt động của mật mã học đối xứng, được sử dụng để mã hóa dữ liệu trong quá trình truyền thông an toàn. Cơ cấu hoạt động của OFB dựa trên việc sử dụng đầu ra của một khối mã hóa trước đó để tạo ra một luồng mã hóa (keystream), sau đó được XOR (hoặc phép toán logic XOR) với dữ liệu gốc để tạo ra dữ liệu mã hóa.

- Dưới đây là cơ cấu hoạt động của OFB:

  - Khởi tạo: OFB bắt đầu bằng việc khởi tạo một khối đầu vào (iv) hoặc một chuỗi khởi tạo (nonce). IV hoặc nonce là một giá trị ngẫu nhiên được sử dụng để khởi tạo quá trình mã hóa. Giá trị này cần được truyền đồng bộ giữa người gửi và người nhận.

  - Mã hóa: OFB sử dụng một khối mã hóa (chẳng hạn AES) để mã hóa giá trị khởi tạo (IV hoặc nonce) để tạo ra một keystream (luồng mã hóa). Keystream này có cùng độ dài với dữ liệu gốc cần được mã hóa.

  - XOR: Keystream được XOR (hoặc phép toán logic XOR) với dữ liệu gốc (plaintext) để tạo ra dữ liệu mã hóa (ciphertext). Điều này đồng nghĩa với việc dữ liệu gốc được "hòa tan" vào trong dãy bit ngẫu nhiên của keystream.

  - Lặp lại: Quá trình mã hóa được lặp lại cho từng khối dữ liệu liên tiếp trong thông điệp gốc, sử dụng đầu ra của khối mã hóa trước đó làm đầu vào cho khối mã hóa tiếp theo.

- Giải mã: Khi nhận được dữ liệu mã hóa, người nhận sử dụng cùng một quá trình OFB với cùng giá trị khởi tạo (IV hoặc nonce) để tạo ra lại keystream, sau đó XOR keystream này với dữ liệu mã hóa để khôi phục lại dữ liệu gốc.

- Lưu ý: OFB là một chế độ hoạt động không có bộ nhớ, nghĩa là nó không phụ thuộc vào đầu ra của khối mã hóa trước đó khi mã hóa dữ liệu. Điều này có nghĩa là nó có khả năng chống lại tấn công "truy cập bộ nhớ trước" (memory-differential attack)
##### Tìm hiểu kỹ hơn về OFB [tại đây](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
-------
## CTR (Counter):
- CTR (Counter) là một trong những chế độ hoạt động của mật mã học đối xứng, được sử dụng để mã hóa dữ liệu trong quá trình truyền thông an toàn. Cơ cấu hoạt động của CTR dựa trên việc sử dụng một bộ đếm (counter) để tạo ra một chuỗi giá trị đơn điệu (monotonically increasing) để làm "khóa" (key) cho việc mã hóa.

- Dưới đây là cơ cấu hoạt động của CTR:

  - Khởi tạo: CTR bắt đầu bằng việc khởi tạo một giá trị đầu vào (iv) hoặc một chuỗi khởi tạo (nonce). IV hoặc nonce là một giá trị ngẫu nhiên được sử dụng để khởi tạo quá trình mã hóa. Giá trị này cần được truyền đồng bộ giữa người gửi và người nhận.

  - Bộ đếm: CTR sử dụng một bộ đếm để tạo ra chuỗi giá trị đơn điệu. Bộ đếm thường là một con số nguyên được tăng lên sau mỗi lần mã hóa. Giá trị của bộ đếm cũng được kết hợp với giá trị khởi tạo (IV hoặc nonce) để tạo ra khóa cho việc mã hóa.

  - Mã hóa: Chuỗi giá trị đơn điệu từ bộ đếm được đưa vào khối mã hóa (chẳng hạn AES) để tạo ra một chuỗi giá trị độc lập (keystream). Keystream này có cùng độ dài với dữ liệu gốc cần được mã hóa.

  - XOR: Keystream được XOR (hoặc phép toán logic XOR) với dữ liệu gốc (plaintext) để tạo ra dữ liệu mã hóa (ciphertext). Điều này đồng nghĩa với việc dữ liệu gốc được "hòa tan" vào trong chuỗi giá trị độc lập của keystream.

  - Lặp lại: Quá trình mã hóa được lặp lại cho từng khối dữ liệu liên tiếp trong thông điệp gốc, sử dụng chuỗi giá trị đơn điệu từ bộ đếm làm khóa cho mã hóa các khối dữ liệu.

- Giải mã: Khi nhận được dữ liệu mã hóa, người nhận sử dụng cùng một quá trình CTR với cùng giá trị khởi tạo (IV hoặc nonce) và cùng bộ đếm để tạo ra lại chuỗi keystream, sau đó XOR keystream này với dữ liệu mã hóa để khôi phục lại dữ liệu gốc.

- Lưu ý quan trọng là bộ đếm trong CTR phải được duy trì đúng và duy nhất giữa người gửi và người nhận. Bất kỳ sai sót nào trong quá trình đồng bộ hóa bộ đếm có thể dẫn đến sự mất mát dữ liệu hoặc sai sót trong quá trình giải mã.

- Một số đặc điểm của CTR:

  - Tính độc lập: Các khối dữ liệu được mã hóa độc lập với nhau, không phụ thuộc vào các khối trước đó hay sau đó, do đó CTR có tính độc lập trong việc mã hóa và giải mã.

  - Tính chống lại thay đổi: Một thay đổi nhỏ trong dữ liệu gốc hoặc trong chuỗi giá trị đơn điệu của bộ đếm chỉ dẫn đến thay đổi tương ứng trong ciphertext, giúp phát hiện các sự thay đổi này trong quá trình truyền thông.

  - Tính đồng thời: CTR cho phép mã hóa và giải mã có thể thực hiện đồng thời trên cùng một chuỗi dữ liệu, giúp tăng tốc độ xử lý và hiệu quả trong các ứng dụng yêu cầu độ trễ thấp.

- Tuy nhiên, cũng cần lưu ý rằng CTR không cung cấp tính bảo mật chống lại việc phá vỡ tính bí mật nếu cùng khóa được sử dụng để mã hóa các dữ liệu khác nhau, do đó cần đảm bảo tính duy nhất của khóa được sử dụng trong quá trình mã hóa và giải mã.

##### Tìm hiểu kỹ hơn về CTR [tại đây](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
