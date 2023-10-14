# Các lệnh cơ bản :

**1. Vị trí :**
  - **cd**: change directory: **cd ../..** ; **cd /** ;
  - **sudo nautilus + vị_trí_thư_mục**: mở explorer giao diện người dùng 
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
  - **sudo dpkg -i tên-tệp.deb** : cài đặt
  - **sudo dpkg -r tên-gói** : gỡ cài đặt gói
  - **dpkg -l | grep tên-gói** : kiển thị trạng thái gói đã cài đặt
  - **dpkg -I tên-tệp.deb** : kiểm tra thông tin về một gói đã cài đặt
  - **dpkg -S /đường-dẫn-đến-tệp** : tìm ứng dụng liên quan đến một tệp cụ thể.
  - dpkg: Debian Package


# Quản lý quyền (permissions) : có 3 quyền chính: Read,(R) Write(W) and Execute(X):Quyền thực thi cho phép bạn chạy một tệp hoặc truy cập một thư mục

  - **chmod +r tên-tệp** : cấp quyền đọc cho tất cả mọi người
  - chmod: change mod
  - **chmod [tùy-chọn] quyền tên-tệp-thư-mục** 
  - **chown tên-người-dùng tên-tệp** : thay đổi chủ sở hữu tệp
  - **chgrp tên-nhóm tên-tệp** : thay đổi nhóm của một tệp, thư mục
  - **chown tên-người-dùng:tên-nhóm tên-tệp** : kết hợp cả 2.

# Hệ thống tệp và thư mục : 

  - **/** là thư mục gốc của hệ thống, tất cả các thư mục và tệp đều bắt đầu từ đây.
  - **/bin**: Chứa các tệp thực thi cơ bản (binary) như các lệnh hệ thống cần để khởi động hệ thống ngay cả khi chưa có tệp hệ thống được gắn kết.
  - **/boot**: Chứa tệp cần thiết để khởi động hệ thống như hạt nhân (kernel) và tệp cấu hình khởi động.
  - **/etc**: Chứa tệp cấu hình hệ thống và ứng dụng.
  - **/home**: Là thư mục chứa các thư mục cá nhân của người dùng. Mỗi người dùng có một thư mục riêng trong đây.
  - **/lib** và **/lib64**: Chứa các thư viện cơ bản cần cho các chương trình thực thi trong /bin và /sbin.
  - **/mnt**: Thư mục dùng để gắn kết các thiết bị ngoại vi như đĩa CD, USB, và ổ đĩa cứng.
  - **/opt**: Thư mục chứa các ứng dụng cài đặt tùy ý.
  - **/root**: Thư mục chứa tệp cá nhân của người dùng gốc (superuser hoặc root) - người có quyền cao nhất trong hệ thống.
  - **/usr**: Chứa các ứng dụng và tệp cơ bản dành cho người dùng, bao gồm cả mã nguồn và tài liệu.
  - **/var**: Chứa các tệp dữ liệu biến đổi thường xuyên, chẳng hạn như tệp ghi log (log files) và dữ liệu cơ sở dữ liệu.

# Quản lý hệ thống, kiểm tra tài nguyên, hiệu suất, dung dương ổ đĩa trên Ubuntu : 

  - **top** là một tiện ích dòng lệnh mạnh mẽ để theo dõi hoạt động hệ thống. Nó hiển thị danh sách các quy trình đang chạy theo thời gian thực, cùng với các thông tin về tài nguyên hệ thống như CPU, RAM, và tài nguyên swap đang sử dụng. Bạn sẽ thấy một bảng hiển thị danh sách các quy trình, thời gian hoạt động, tài nguyên CPU và RAM. Sử dụng các phím mũi tên lên/xuống để điều hướng trong danh sách và phím q để thoát.
  - **htop** : cài đặt: **sudo apt-get install htop**  ; sau đó chạy **htop** : nó là nâng cấp của top, giao diện cũng thân thiện hơn
  - **df -h** : lệnh disk free, kiểm tra dung lượng đã sử dụng, và còn lại.
  - kill: dừng quá trình
  - nice valua: thể hiện mức độ "tốt" của quá trình...

# Quản lý mạng

  - **ifconfig** (interface configuration) cho phép bạn xem và quản lý các thông tin mạng của các giao diện mạng trên hệ thống.
  - **ip** : quản lý giao diện mạng, thay đổi cấu hình, vd: **ip a** : xem thông tin mạng của tất cả giao diện; **ip route** : xem bảng bộ định tuyến
  - **ping địa-chỉ-ip-hoặc-tên-máy-chủ** : kiểm tra kết nối mạng và đo thời gian phản hồi từ một máy tính khác
  - **netstat -tuln** : Xem danh sách các cổng mạng đang lắng nghe
  - Lệnh **ifup** và **ifdown** : bật tắt giao diện mạng (cũng không cần thiết lắm)

# Quản lý tác vụ - xử lý (Process)

  - Mỗi một task đều có một dạng duy nhất gọi là PID(process id), cho biết vị trí của quy trình trong hệ thống.
  - Lệnh **ps** là một công cụ dòng lệnh để xem danh sách các quy trình đang chạy trên hệ thống. Bạn có thể sử dụng **ps** với các tùy chọn để xem thông tin chi tiết về các quy trình. ví dụ: **ps aux**: a là tùy chọn để hiển thị tất cả các quy trình, u là tùy chọn để hiển thị thông tin chi tiết.
  - **kill number_of_PID** : kết thúc một quy trình. **kill -9 12345** : thêm -9 để kết thúc quy trình một cách bắt buộc
  - **pgrep myprocess** : trả về PID của quy trình tương ứng.
  - Tóm lại, các lênh thường dùng là ps **aux ; kill , pgrep** 

# File systems:

  - Thư mục
  - Tệp
  - Hệ thống tệp ext4: là hệ thống mặc định của linux, hỗ trợ nhiều tính năng như journaling (ghi nhật ký) để bảo vệ dữ liệu khỏi mất mát do sự cố hệ thống.
  - NTFS và FAT: New Technology File System và File Allocation Table, Ubuntu có hỗ trợ đọc ghi
  - Gắn kết thiết bị (Mounting Devices):
  - Ổ đĩa mạng (Network Drives): Ổ đĩa mạng là một phương tiện để kết nối và làm việc với dữ liệu lưu trên mạng thông qua giao thức mạng như SMB (Samba), NFS (Network File System), hoặc FTP (File Transfer Protocol).
  - **Mount và umount:** : Dùng lệnh **fdisk** hoặc **lsblk** để scan các ổ đĩa ; **sudo mkdir /media/mydrive** : tạo một thư mục trống làm mount point(điểm gắn kết) ; cuối cùng, mount thông qua lệnh: **sudo mount /dev/sdb1 /media/mydrive**; **sudo umount /media/mydrive** để unmount, lưu ý unmount được viết thành umount.

# Bảo mật: 

  - Firewall : **sudo ufw enable**    # Kích hoạt tường lửa ; **sudo ufw allow 22/tcp**    # Cho phép lưu lượng truy cập SSH
  - Sử dụng phần mềm chống vi-rút: **sudo apt install clamav** ; **sudo freshclam** Cập nhật Cơ sở dữ liệu Chữ ký Virus ; **sudo clamscan -r /**     # Quét toàn bộ hệ thống

# Một Số lệnh cho ESP-IDF:

**1. Biên Dịch Ứng Dụng:**

  - **idf.py build**: Biên dịch mã nguồn của ứng dụng.

**2. Nạp Chương Trình Lên ESP32:**

  - **idf.py -p (port) flash**: Nạp chương trình đã biên dịch lên ESP32 thông qua cổng nối tiếp (ví dụ: /dev/ttyUSB0).

**3. Chạy Chương Trình và Theo Dõi Output:**

  - **idf.py -p (port) monitor**: Chạy chương trình trên ESP32 và theo dõi kết quả output trực tiếp.

**4. Tạo Dự Án Mới:**

  - **idf.py create-project** (project_name): Tạo một dự án mới với tên project_name.

**5. Xóa Dự Án:**

  - **idf.py fullclean**: Xóa toàn bộ dự án, bao gồm các tệp đã biên dịch.

**6. Cài Đặt Thư Viện Bên Ngoài:**

  - **idf.py menuconfig**: Cho phép bạn cài đặt và cấu hình thư viện và chức năng dự án.

**7. Tạo Tệp .bin cho Firmware:**

  - **idf.py -p (port) build**: Biên dịch và tạo tệp .bin chứa firmware để nạp lên ESP32.

**8. Lập Trình UART (Giao Tiếp Serial):**

  - **idf.py menuconfig** và sau đó vào "Serial flasher config" để cấu hình UART để nạp chương trình.

**9. Kiểm Tra Log System:**

  - **idf.py monitor** cho phép bạn theo dõi log hệ thống trong thời gian chạy.

**10. Cài Đặt Gói Mở Rộng ESP-IDF:**

  - Sử dụng **idf.py set-target** để cài đặt gói mở rộng như **esp-aws-iot, esp-mqtt**

**Làm việc với tệp và thư mục:**

  - ls: Liệt kê các tệp và thư mục trong thư mục hiện tại.
  - cd: Di chuyển giữa các thư mục.
  - mkdir: Tạo thư mục mới.
  - touch: Tạo tệp mới hoặc cập nhật thời gian truy cập của một tệp.
  - rm: Xóa tệp hoặc thư mục.
    
**Biên dịch và biên dich chương trình:**

  - gcc: Trình biên dịch C/C++.
  - g++: Trình biên dịch C++.
  - make: Sử dụng để biên dịch và xây dựng dự án với Makefile.
    
**Kiểm tra tệp và thư mục:**

  - file: Hiển thị thông tin về loại tệp.
  - stat: Hiển thị thông tin về tệp hoặc thư mục.
  - diff: So sánh hai tệp văn bản.
  - hexdump: Hiển thị nội dung của tệp dưới dạng mã hex.
    
**Giao tiếp với thiết bị ngoại vi (ví dụ: microcontroller):**

  - minicom: Ứng dụng giao diện dòng lệnh để truy cập và giao tiếp với thiết bị ngoại vi thông qua cổng serial.
  - picocom: Tương tự như minicom, nhưng có giao diện dòng lệnh đơn giản hơn.

**Chuyển đổi và soạn thảo mã nguồn:**

  - nano hoặc vim: Trình soạn thảo văn bản dòng lệnh.
  - gedit hoặc Visual Studio Code: Trình soạn thảo mã nguồn với giao diện đồ họa.

**Quản lý gói và phần mềm:**

  - apt-get hoặc apt: Quản lý gói và phần mềm trên Ubuntu với APT.
  - snap: Quản lý ứng dụng Snap.
  - dpkg: Quản lý gói DEB trực tiếp.

**Kiểm tra và quản lý tài nguyên hệ thống:**

  - htop: Hiển thị thông tin về việc sử dụng CPU và RAM.
  - df: Hiển thị thông tin về dung lượng đĩa.
  - free: Hiển thị thông tin về RAM còn trống.

**Debug và kiểm tra:**

  - gdb: Trình gỡ lỗi GNU Debugger.
  - strace: Theo dõi cuộc gọi hệ thống.

**Giao tiếp mạng:**

  - ping: Kiểm tra kết nối mạng bằng cách gửi gói tin ping.
  - ifconfig hoặc ip: Hiển thị và quản lý cài đặt mạng.























