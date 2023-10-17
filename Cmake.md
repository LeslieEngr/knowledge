# Bước 1: Điểm Khởi Đầu Cơ Bản:

**Bai 1+2: Build 1 project+Them tieu chuan Cpp (VScode lam cho roi)**

  1. cmake_minimum_required(VERSION 3.22) #tep cau hinh toi thieu
  2. project(MyCMakeProject) #dat ten project la My..
  3. add_executable(**my_app** main.cpp): Tao mot ung dung thuc thi ten my_app tu main.cpp
  4. set(CMAKE_CXX_STANDARD 14) : Thiet lap tieu chuan C++14
  5. set(VERSION_NUMBER 1.0.0) : dat phien ban la 1.0.0
  - >>cmake . : Xay dung cac tep git o vi tri hien tai
  - >>cmake --build . : Built chuong trinh **my_app** o vi tri hien tai ( tuong tuong gcc -o **my_app**)
  - ****Luu y: target chinh la ten ung dung sau khi build. O day target la **my_app**

# Bước 2: Them Library:

  - Dau tien , tao mot thu vien **ten_thuvien.cpp** va **ten_thuvien.hpp**, sau do, them vao CMakeList.txt:
  1. add_library(<tên_thư_viện> [STATIC | SHARED] <danh_sách_tệp_nguồn>)
  2. target_link_libraries(<tên_mục_tiêu> [PRIVATE | PUBLIC | INTERFACE] <tên_thư_viện1> <tên_thư_viện2> ...)  #ten_danh_sach_tep_nguon: la ten goi dai dien cho **ten_thuvien.cpp** va **ten_thuvien.hpp**

# Buoc 3: Them Directories

  -  target_include_directories(<tên_mục_tiêu> [SYSTEM] INTERFACE|PUBLIC|PRIVATE
    <đường_dẫn_thư_mục1>
    <đường_dẫn_thư_mục2>
    ...
) : lenh nay cho phep tat ca cac file.cpp deu co the su dung thu vien <tên_mục_tiêu>, duoc chi dinh trong <đường_dẫn_thư_mục1>
  - add_subdirectory(<ten_thu_muc>) : them thu muc

  - Noi chung, khi them Directories, ta dung 2 lenh tren. 