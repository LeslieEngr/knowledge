#Các lệnh cơ bản:

**1. Vị trí :**
  - **cd**: change directory: **cd ../..** ; **cd /** ;
  - **pwd**: print working directory:
  - (relative paths: đường dẫn tương đối): nơi bạn đến phụ thuộc vào thư mục làm việc hiện tại.
  - (absolute paths: đường dẫn tuyệt đối): cho dù đang ở thư mục nào, thì lệnh cũng tương tự. Và **/** là biểu thị của **root**, **~** biểu thị là **Home** 
  - **whoami**: tên user
  - **ls**: list
    
**2. Tạo Directory hoặc files:**
  - **ls > output.txt** : Tạo file bằng ls
  - **cat output.txt** : Xem nội dung tệp tin đó ; cat viết tắt trong từ con**cat**enate, nó còn dùng để nối dữ liệu: **cat test_1.txt test_2.txt**
với lệnh này, ta có thể dùng phím tắt **"?"**: cat test_?.txt hoặc phím tắt **"*"** :cat test_*, tương tự có thể dùng **">"** để tạo một file tổng hợp 
  - **echo "This is a test" > test_1.txt** : Tạo file test_1.txt với nội dung "text"
  - **less comnined.txt**: có thể sử dụng cái phím định hướng để di chuyển qua lại tệp tin. Nhấn q để thoát less.
    
**3. Di chuyển tệp, folder:**
  - **mv nguồn đích** : **mv file.txt Documents/** ; mv dir1/* .  : sao chép toàn bộ thư mục con của dir1 vào thư mục hiện tại **"."**
  - **cp nguồn đích** : **cp document.pdf Backup/** 
  - **rm tên_tệp** :  
  - **rm -r tên_thư_mục** :
    
**4. Cấu trúc pile:**
  - **wc -l combined.txt** : Đếm số dòng trong file txt 
  - **man tên_lệnh** : manual của lệnh đó
  - **lệnh1 | lệnh2** : chuyển dữ liệu từ lệnh1 làm đối tượng cho lệnh2
  - **>**: chuyển hướng dữ liệu đầu ra sang một tệp mới
  - **>>**: chuyển hướng dữ liệu đầu ra của lệnh1 về cuối của tệp mới
    
**5. Dòng lệnh super user:**
  - khi nhập mật khẩu, mật khẩu sẽ được luưu vào vùng nhớ đệm, mặc định là 15 phút.
  - **ls -a .hidden**: Hiển thị các tệp ẩn: 



