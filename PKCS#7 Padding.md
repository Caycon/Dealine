# PKCS#7 Padding
PKCS#7 Padding là một chuẩn padding được sử dụng trong các thuật toán mã hóa khối như AES. Chuẩn này được định nghĩa trong RFC 2315 và được sử dụng rộng rãi trong các ứng dụng bảo mật.

Cơ chế hoạt động của PKCS#7 Padding như sau: Nếu kích thước khối ban đầu không phải là bội số của kích thước khối mong muốn, thì chuẩn này sẽ thêm vào các byte padding để đạt được kích thước mong muốn. Giá trị của các byte padding sẽ bằng với số lượng byte cần thêm vào để đạt được kích thước mong muốn.

Ví dụ: Nếu kích thước khối ban đầu là 15 byte và kích thước khối mong muốn là 16 byte, chuẩn PKCS#7 Padding sẽ thêm vào 1 byte có giá trị là 0x01.
