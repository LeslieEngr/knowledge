# Các thể loại cấu trúc chương trình
  I. ABOUT FREERTOS

  - Khi sử dụng RTOS, ứng dụng phải viết dưới dạng một tập hợp các tác vụ độc lập. Có nghĩa là hàm mai() không chứa chức năng ứng dụng, mà chỉ tạo tác vụ ứng dụng. Sau đó
khởi động nhân RTOS.
  - Cấu trúc một dự án RTOS: https://www.freertos.org/Creating-a-new-FreeRTOS-project.html
  - Một số quy ước chung : https://www.freertos.org/FreeRTOS-Coding-Standard-and-Style-Guide.html#CodingStandard

**Tại sao sử dụng RTOS**
![image](https://github.com/LeslieEngr/knowledge/assets/128287548/d3fd396b-1990-4b5e-a72e-8eebfad5d36e)

   1. Rtos so với super loop khác nhau ở chỗ, super loop sẽ chạy từng task một, Rtos sẽ chạy gần như đồng thời- thực tế, nó sẽ phân cách khe thời gian cho mỗi task và nhanh chóng chuyển đổi chạy giữa các task, nên ta hình dung như chúng chạy đồng thời.
   2. Chúng giả lập như việc chạy trên nhiều core, thực tế chỉ trên 1 core.
   3. Task State: 
![image](https://github.com/LeslieEngr/knowledge/assets/128287548/c825e247-bee3-4846-bcc9-75b701ebe2af)
        + Running : Đang chạy
        + Ready : Sẵn sàng
        + Block : Đang bị khóa, để chờ ready
        + Suspended : Ngủ đông
     
  II. Khác:
  - Super Loop: Vòng lặp vô hạn, tuần tự
    + Ưu: Đơn giản, dễ hiểu
    + Ngược: Không linh hoạt khi xử lý công việc đồng thời, hiệu suất kém, khó mở rộng
  - Event-Driven:  Hệ thống phản ứng vào sự kiện, không chạy liên tục mà chờ đợi sự kiện xảy ra.
    + Ưu: Linh hoạt, hiệu suất tốt cho các ứng dụng yêu cầu xử lý ngắn gọn.
    + Ngược: Khó quản lý khi số lượng sự kiện lớn và phức tạp
  - RTOS: Sử dụng hệ điều hành thời gian thực để quản lý đồng thời các tác vụ
    + Ưu: Đảm bảo thời gian thực, quản lý tốt các nhiệm vụ đồng thời , chia sẻ tài nguyên một cách hiệu quả.
    + Nhược: Tính phức tạp và tốn tài nguyên hệ thống so với các phương pháp đơn giản hơn
  - State Machine: sử dụng State Machine để quản lý hệ thống, chuyển đổi giữa các trạng thái với nhau.
    + Ưu: Hiệu quả cho các ứng dụng với logic chuyển đổi trạng thái
    + Nhược: Khó mở rộng khi có nhiều trạng thái và chuyển đổi phức tạp
  - Microkernel: Phân chia hệ điều hành thành các phần nhỏ(kernel) chạy trên chế độ người cung cấp các dịch vụ như quản lý tác vụ, giao tiếp,bảo mật.
    + Ưu: Linh hoạt, có thể tùy chỉnh các thành phần hệ điều hành 
    + Nhược: Tăng độ phức tạp, yêu cầu quản lý tốt các module và tương tác tốt giữa chúng.
