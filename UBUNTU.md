# Các lệnh cơ bản :

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
  - **sudo chmod a+rw /dev/ttyUSB0**: lệnh này thay đổi quyền(chmod) đọc và ghi(+rw) của đối tượng(/dev/ttyUSB0) cho tất cả người dùng(a).

# Cài đặt và quản lí các tệp tin :

**1. APT - advanced package tool :** Sử dụng các gói **DEB**- định dạng truyền thống của ubuntu. Tích hợp với hệ thống, đôi khi có thể xung đột vì chúng dùng thư viện hệ thống. Firmware không phải mới nhất nhưng ổn định
  - **sudo apt install tên-ứng-dụng**
  - **sudo apt remove tên-ứng-dụng**
  - **sudo apt update**: cập nhật danh sách gói ứng dụng
  - **sudo apt upgrade**: cập nhật hệ thống và ứng dụng
  - **apt search tên-ứng-dụng**
  - **apt show tên-ứng-dụng**
  - **dpkg -l**: hiển thị danh sách tất cả các gói ứng dụng đã cài đặt.

**2. Snap :** Cho phép cài ứng dụng mới nhất từ nhà phát triển, cách ly với hệ thống, nên quản lý cũng không can thiệp tới hệ thống APT.
  - **sudo snap install tên-ứng-dụng**
  - **sudo snap remove tên-ứng-dụng**
  - **snap list** : danh sách các ứng dụng đã cài đặt bởi snap
  - **sudo snap refresh** : cập nhật tât cả ứng dụng Snap
  - **snap info tên-ứng-dụng** : xem thông tin về một ứng dụng Snap đã cài đặt.

**3. PPA - Personal Package Archive :**
  - Thên một ppa : **sudo add-apt-repository ppa:repository-name** ; sau đó cần cập nhật gói ứng dụng : **sudo apt update**
  - Xóa một ppa: **sudo ppa-purge ppa:repository-name** hoặc **sudo add-apt-repository --remove ppa:repository-name** ; sau đó **sudo apt update**
  - Liệt kê cách lệnh đã cài đặt: kiểm tra tệp **/etc/apt/sources.list** và các thư mục **/etc/apt/sources.list.d/**
  - Xem thông tin về một tập PPA: kiểm tra tệp **.list** trong thư mục **/etc/apt/sources.list.d/**
  - Cập nhật gói ứng dụng sau thay đổi trong PPA: **sudo apt update**

**4. Ngoài ra còn có Flatpak( tệp đuôi .flatpakref), Local app project, cài đặt tệp deb thủ công, wine, cài đặt từ nguồn(ví dụ github) :**
  - **sudo dpkg -i tên-tệp.deb**

# Tạo một ứng dụng hiển thị trên dash :
    1. Tạo một file txt, sau đó sửa thành nội dung như sau:(bỏ bớt khoảng xuống dòng sau khi copy vào file)

[Desktop Entry]

Type=Application

Name=Tên ứng dụng

Exec=/đường-dẫn-đến-tệp.AppImage

Icon=/đường-dẫn-đến-biểu-tượng.png

    2. Sau đó, thay đổi thông số, sửa file thành đuôi .desktop

    3. Chạy lệnh **nautilus ~/.local/share/applications** để hiển thư mục application, rồi cho file .desktop vào trong.











