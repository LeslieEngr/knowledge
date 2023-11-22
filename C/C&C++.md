# Thu vien chuan:
  - type_traits.

# Kiều dữ liệu: *: số bit
  - uint*_t : 
  - uint_fast*_t : tối ưu hiệu suất và linh hoạt về kích thước, kích thước có thể **lớn hơn hoặc bằng** *

#Struct
  - Sau khi khởi tạo Struct, ta khai báo , nếu nó rỗng thì nên đặt **ten_struct={};** .  tất cả các trường của struct sẽ được khởi tạo với giá trị mặc định cho kiểu dữ liệu tương ứng (ví dụ: float sẽ được khởi tạo là 0.0). Điều này giúp đảm bảo rằng bạn có một trạng thái khởi đầu kiểm soát hơn khi sử dụng biến. Ngược lại, nếu không khởi tạo giá trị ban đầu,  các trường của nó sẽ chứa giá trị ngẫu nhiên từ bộ nhớ, và điều này có thể gây ra lỗi nếu bạn sử dụng các trường mà không biết giá trị của chúng.
  - Khái niệm về phương thức thuần ảo : vd : kieu_dulieu ten_ham(int a, ... ,float b) = 0; đây là một kiểu phương thức thuần ảo, nó được khởi tạo trong hàm cơ sở (hàm cha) , và được gán = 0, nghĩa là nó sẽ được triển khai trong hàm dẫn xuất (hàm con).

#Data type 
  - Một kiểu liệt kê (enum):giúp tập hợp một nhóm hằng số có chung một ý nghĩa, chẳng hạn gán giá trị cho các thứ trong một tuần, mang lại nhiều ý nghĩa cho người đọc chương trình. Các phần tử trong enum có thể tự động gán giá trị tăng dần, ta cũng có thể chủ động gán giá trị cho chúng, và nó sẽ tăng dần giá trị của chính phần tử cuối cùng được gán.
  - Chuyển từ Bigendian sang Little endian chỉ đơn giản là đảo byte, vd :0x12345678 thì  Big : 12345678  >>> Little :  78563412  , chuyển đổi theo cặp vì mỗi 1 hex = 4 bit, 1 cặp hex là 8 bit ( tức 1 byte).

Lý do phải chuyển : Các giao thức mạng hoặc học đọc, ghi dữ liệu, hoặc do cấu trúc máy tính khác nhau . Để tương thích cần chuyển đổi. 

