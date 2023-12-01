# Thu vien chuan:
  - type_traits.

# Kiều dữ liệu: *: số bit
  - uint*_t : 
  - uint_fast*_t : tối ưu hiệu suất và linh hoạt về kích thước, kích thước có thể **lớn hơn hoặc bằng** *
  - Bảng mã ASCII, bình thường tra là bảng basic, ngoài ra còn rất nhiều loại, phục vụ cho mục đích sử dụng khác nhau : 
       + Printable Characters:Bao gồm các ký tự có thể hiển thị được trên màn hình, bao gồm chữ cái, số, ký hiệu, dấu chấm câu, và các ký tự đặc biệt khác như khoảng trắng.
       + **Control Characters**:Bao gồm các ký tự không thể hiển thị trực tiếp trên màn hình, được sử dụng để kiểm soát và định hình dữ liệu, như ký tự xuống dòng (newline), ký tự tab, và ký tự kết thúc tệp (end of file).
       + Extended ASCII:Mở rộng bảng mã ASCII để bao gồm thêm các ký tự và ký tự đặc biệt, chẳng hạn như ký tự với dấu, ký tự tiếng Pháp, tiếng Đức, và một số ký tự đặc biệt khác.
       + Non-Printable Characters:Bao gồm cả các ký tự không thể in được và không hiển thị trực tiếp trên màn hình. Đây thường là các ký tự điều khiển và các ký tự đặc biệt không thể nhìn thấy.
       + Whitespace Characters:Bao gồm khoảng trắng, tab, và các ký tự trắng khác được sử dụng để tạo khoảng trắng và định dạng văn bản.
       + Symbol Characters:Bao gồm các ký tự đặc biệt như dấu cộng (+), dấu trừ (-), dấu nhân (*), dấu chia (/), và các ký tự toán học khác.
       + Numeric Characters:Bao gồm các chữ số từ 0 đến 9.
       + Alphabetic Characters:Bao gồm các ký tự chữ cái từ A đến Z và từ a đến z.
   
  - Một kiểu liệt kê (enum):giúp tập hợp một nhóm hằng số có chung một ý nghĩa, chẳng hạn gán giá trị cho các thứ trong một tuần, mang lại nhiều ý nghĩa cho người đọc chương trình. Các phần tử trong enum có thể tự động gán giá trị tăng dần, ta cũng có thể chủ động gán giá trị cho chúng, và nó sẽ tăng dần giá trị của chính phần tử cuối cùng được gán.
  - Chuyển từ Bigendian sang Little endian chỉ đơn giản là đảo byte, vd :0x12345678 thì  Big : 12345678  >>> Little :  78563412  , chuyển đổi theo cặp vì mỗi 1 hex = 4 bit, 1 cặp hex là 8 bit ( tức 1 byte). Lý do phải chuyển : Các giao thức mạng hoặc học đọc, ghi dữ liệu, hoặc do cấu trúc máy tính khác nhau . Để tương thích cần chuyển đổi. 

# OOP
  I. Struct
# Khái niệm cơ bản:
  - Hàm tạo (Constructor) : Khởi tạo giá trị ban đầu cho struct, tránh trường hợp nó ở dạng không xác định
  - Con trỏ đến struct : Có thể dùng con trỏ đến một đối tượng struct và truy cập vào thành phần của nó
    
        'Point* pPtr = &p1'
        'cout << "X: " << pPtr->x << ", Y: " << pPtr->y << endl'
  - Hàm hủy (Descontructor) : hàm hủy ~ten_class , được gọi tự động khi một đối tượng của lớp được hủy, dùng để giải phóng tài nguyên cho đối tượng cấp phát trong quá trình sử dụng.
  - Hàm gán (copy assignment operator) : gán giá trị của một object cho một object khác cùng loại, mục đích để sao chép dữ liệu tránh bị lỗi, mất dữ liệu.
#Một số mẹo 
  - Sau khi khởi tạo Struct, ta khai báo , nếu nó rỗng thì nên đặt **ten_struct={};** .  tất cả các trường của struct sẽ được khởi tạo với giá trị mặc định cho kiểu dữ liệu tương ứng (ví dụ: float sẽ được khởi tạo là 0.0). Điều này giúp đảm bảo rằng bạn có một trạng thái khởi đầu kiểm soát hơn khi sử dụng biến. Ngược lại, nếu không khởi tạo giá trị ban đầu,  các trường của nó sẽ chứa giá trị ngẫu nhiên từ bộ nhớ, và điều này có thể gây ra lỗi nếu bạn sử dụng các trường mà không biết giá trị của chúng.
  - Khái niệm về phương thức thuần ảo : vd : kieu_dulieu ten_ham(int a, ... ,float b) = 0; đây là một kiểu phương thức thuần ảo, nó được khởi tạo trong hàm cơ sở (hàm cha) , và được gán = 0, nghĩa là nó sẽ được triển khai trong hàm dẫn xuất (hàm con).

# Cấp phát bộ nhớ động : lưu ý khi dùng xong phải giải phóng tài nguyên, và new, malloc, free, calloc không nên hòa trộn trong 1 chương trình để tránh conflic
  - Cách phổ biến nhất:  Từ khóa **new** cung cấp bộ nhớ động tới vùng nhớ HEAP(Quản lý bởi lập trình viên và không có giới hạn) cho đối tượng hoặc mảng, nó sẽ tạo vùng nhớ trong HEAP và trả về con trỏ trỏ tới vùng nhớ đó. Điều này giúp chia sẻ dữ liệu giữa các hàm, quản lý kích thước linh hoạt, tránh rủi ro vượt quá ngăn xếp. Lưu ý rằng sau khi sử dụng xong, ta cần **delete** result để giải phóng bộ nhớ. Hàm trả về con trỏ : dùng để cấp phát động, quản lý đối tượng được cấp phát động, trả về mảng từ hàm, thao tác trực tiếp trên đối tượng và hiệu quả khi truyền dữ liệu, đặc biệt là khi dữ liệu có kích thước lớn.  vd:

                    // Toán tử new và delete 
            int* dynamicInt = new int;  // Cấp phát một biến int động
            delete dynamicInt;          // Giải phóng bộ nhớ
                    // Toán tử new và delete cho mảng động 
            int* dynamicArray = new int[5];  // Cấp phát mảng int động
            delete[] dynamicArray;
                    // Hàm trả về con trỏ :
            double* createdynamicarray(int n){
            double* dynamicdouble = new double[n];
            return dynamicdouble;   // trả về con trỏ mảng kiểu double tới vùng nhớ HEAP
              } 
  - Hàm malloc và free : là một hàm trong thư viện cstdlid, trả về một con trỏ void 

            int* dynamicInt = (int*)malloc(sizeof(int));  // Cấp phát một biến int động
            free(dynamicInt);                            // Giải phóng bộ nhớ
  - Hàm calloc và free : có thể khởi tạo giá trị mặc định cho byte vừa cấp phát

            int* dynamicArray = (int*)calloc(5, sizeof(int));  // Cấp phát mảng int động với 5 phần tử
            free(dynamicArray);                                // Giải phóng bộ nhớ
  - Hàm relloc : để thay đổi kích thước bộ nhớ đã cấp phát trước đó 

            int* dynamicArray = (int*)malloc(5 * sizeof(int));   // Cấp phát mảng int động với 5 phần tử
            dynamicArray = (int*)realloc(dynamicArray, 10 * sizeof(int));  // Thay đổi kích thước mảng đến 10 phần tử
            free(dynamicArray);                                   // Giải phóng bộ nhớ
# Khác:
  - Một macro không thực sự là một hàm, nó đơn giản là phép thay thế văn bản. Trước khi biên dịch, nó sẽ thay thế tất cả sự xuất hiện của macro đó bằng mọi nội dung của nó. vd:

        '#define EXAMPLE_MACRO(x)   \
            do {                   \
                printf("%d", x);   \ trong hàm xuất hiện EXAMPLE_MACRO(x) ở đâu, nó sẽ thay thế bằng hàm do - while này.
            } while (0)
    
