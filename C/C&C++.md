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
  - Hàm malloc và free : là một hàm trong thư viện cstdlid, trả về một con trỏ void  : Memory Allocation (cấp phát bộ nhớ).

            int* dynamicInt = (int*)malloc(n*sizeof(int));  // Cấp phát một biến int động , n là kích cỡ, sizeof(int) là kích thước tính bằng byte.
            free(dynamicInt);                            // Giải phóng bộ nhớ
  - Hàm calloc và free : có thể khởi tạo giá trị mặc định cho byte vừa cấp phát      : Contiguous Allocation (cấp phát liên tục).

            int* dynamicArray = (int*)calloc(5, sizeof(int));  // Cấp phát mảng int động với 5 phần tử
            free(dynamicArray);                                // Giải phóng bộ nhớ
  - Hàm relloc : để thay đổi kích thước bộ nhớ đã cấp phát trước đó 

            int* dynamicArray = (int*)malloc(5 * sizeof(int));   // Cấp phát mảng int động với 5 phần tử
            dynamicArray = (int*)realloc(dynamicArray, 10 * sizeof(int));  // Thay đổi kích thước mảng đến 10 phần tử
            free(dynamicArray);                                   // Giải phóng bộ nhớ
  - So sánh calloc và malloc :
      + Tham số:
        1. malloc: Nhận một tham số là kích thước của bộ nhớ cần cấp phát (tính bằng byte).
        2. calloc: Nhận hai tham số là số lượng phần tử và kích thước của mỗi phần tử.
      + Giá trị ban đầu của bộ nhớ:
        1. malloc: Không đảm bảo rằng bộ nhớ được cấp phát có giá trị khởi tạo. Nó có thể chứa giá trị ngẫu nhiên từ bộ nhớ đã sử dụng trước đó.
        2. calloc: Bộ nhớ được cấp phát bằng calloc có giá trị khởi tạo là 0 cho tất cả các byte.
      + Hiệu suất:
        1. malloc: Thực hiện nhanh hơn vì không cần phải thiết lập giá trị ban đầu của bộ nhớ.
        2. calloc: Có thể chậm hơn vì cần phải thiết lập giá trị khởi tạo của tất cả byte trong bộ nhớ cấp phát.
  - Sử dụng:
        1. malloc: Thích hợp khi bạn không quan tâm đến giá trị ban đầu của bộ nhớ và muốn cấp phát một lượng lớn bộ nhớ nhanh chóng.
        2. calloc: Thích hợp khi bạn muốn đảm bảo rằng tất cả giá trị ban đầu trong bộ nhớ đều là 0, đặc biệt là trong trường hợp của mảng hoặc dữ liệu cần được khởi tạo một cách an toàn.
# Memory Layout
![image](https://github.com/LeslieEngr/knowledge/assets/128287548/92111a9f-6744-400f-a1cd-eaaea28b2c9c)
  - OS Kernel Space (Không gian Kernel của Hệ điều hành): Là phần của bộ nhớ được dành cho hạt nhân (kernel) của hệ điều hành. Nó chứa mã và dữ liệu của hạt nhân, cũng như các cấu trúc dữ liệu và bảng trang quản lý bộ nhớ.
  - Stack: Dùng để lưu trữ các biến cục bộ và giữa các giá trị trả về từ các hàm. Hoạt động theo nguyên tắc "Last In, First Out" (LIFO). Mỗi thread của một chương trình có một ngăn xếp riêng.
  - Heap: Là nơi lưu trữ dữ liệu động được cấp phát trong quá trình chạy của chương trình. Cấp phát và giải phóng bộ nhớ trên heap tùy thuộc vào yêu cầu của chương trình.
  - BSS (Block Started by Symbol): Uninitialized Data Segment:  Là một phần của Data Segment, chứa các biến toàn cục và tĩnh chưa được khai báo giá trị. Trong nhiều trường hợp, BSS chứa các biến với giá trị mặc định là 0, có thể đọc và ghi được.
  - Data Segment: Chứa các biến toàn cục và tĩnh đã được khởi tạo. Dữ liệu trong segment này thường được sao chép từ file thực thi vào khi chương trình bắt đầu.
    + Vùng nhớ hằng: Cho phép đọc và ghi lần đầu, sau đó chúng sẽ tồn tại trong suôt chương trình mà không thể thay đổi giá trị
    + Lưu trữ biến toàn cục, static được khai báo giá trị, tồn tại trong cả quá trình chạy, có thể đọc, ghi được.
  - Text Segment (Đoạn văn bản): Còn được gọi là Code Segment, chứa mã máy của chương trình. Thường là chỉ đọc và không thể thay đổi trong quá trình chạy.
# Khác:
  - Một macro không thực sự là một hàm, nó đơn giản là phép thay thế văn bản. Trước khi biên dịch, nó sẽ thay thế tất cả sự xuất hiện của macro đó bằng mọi nội dung của nó. vd:

        '#define EXAMPLE_MACRO(x)   \
            do {                   \
                printf("%d", x);   \ trong hàm xuất hiện EXAMPLE_MACRO(x) ở đâu, nó sẽ thay thế bằng hàm do - while này.
            } while (0)
    
