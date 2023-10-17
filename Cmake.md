# Bước 1: Điểm Khởi Đầu Cơ Bản:

**Bai 1+2: Build 1 project+Them tieu chuan Cpp (VScode lam cho roi)**

  - cmake_minimum_required(VERSION 3.22) #tep cau hinh toi thieu
  - project(MyCMakeProject) #dat ten project la My..
  - add_executable(my_app main.cpp): Tao mot ung dung thuc thi ten my_app tu main.cpp
  - set(CMAKE_CXX_STANDARD 14) : Thiet lap tieu chuan C++14
  - >>cmake . : built chuong trinh  

**Bai 3: Thêm số phiên bản vào dự án và tạo tệp cấu hình.**

  - project(Tutorial VERSION 1.0)  : Ten du an + so phien ban
  - configure_file(TutorialConfig.h.in TutorialConfig.h)  : sao chep noi dung trong tep .h.in vao tep .h VD: 
  -> .h.in :  #define VERSION_NUMBER @VERSION_NUMBER@
  -> CMakeLists.txt :  set(VERSION_NUMBER "1.0")
  -> >> Vay khi chay CMake, tep .h se co noi dung : #define VERSION_NUMBER 1.0
  - target_include_directories(target_name  [SYSTEM] [AFTER|BEFORE]  directory1 [directory2 ...]) ; no cho phep cac function co the truy cap den cac thu vien, components
  - con nua: https://cmake.org/cmake/help/latest/guide/tutorial/A%20Basic%20Starting%20Point.html#exercise-3-adding-a-version-number-and-configured-header-file

# Bước 2: Them Library:

**Bai 1: Thêm Library.**  
