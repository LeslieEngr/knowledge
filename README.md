![image](https://github.com/LeslieEngr/protocol/assets/128287548/6f027e30-da71-4e89-ac17-9f073fa25324)# Khái niệm:
**1. Cáp Cản Trở (Shielded Cable):**
Cáp cản trở là cáp có một lớp bao ngoài bằng chất liệu dẫn điện (điển hình là lá bạc) để bảo vệ dây dẫn bên trong khỏi nhiễu từ môi trường xung quanh.
Bao vỏ bằng kim loại bao quanh dây dẫn được kết nối đến đất (ground) để đảm bảo chất liệu bao ngoài này có thể tiếp xúc với đất và loại bỏ nhiễu.
Cáp cản trở thường được sử dụng trong các ứng dụng yêu cầu bảo vệ chống nhiễu mạnh như trong môi trường công nghiệp hoặc khi cáp phải chạy qua các khu vực có nhiễu điện từ mạnh.

**2. Cáp Không Cản Trở (Unshielded Cable):**
Cáp không cản trở không có lớp bao ngoài bằng kim loại để bảo vệ dây dẫn bên trong. Thay vào đó, nó thường có một lớp bao vỏ bằng nhựa hoặc cao su để bảo vệ dây dẫn và giữ chúng cách ly khỏi môi trường bên ngoài.
Cáp không cản trở thường có giá thành thấp hơn và dễ dàng lắp đặt hơn so với cáp cản trở.
Tuy nhiên, cáp không cản trở không thích hợp cho các ứng dụng yêu cầu bảo vệ chống nhiễu mạnh hoặc khi phải chạy qua môi trường có nhiễu điện từ mạnh.

**3. RS232:**
RS232 sử dụng cáp đôi không cản trở (twisted pair) với hai sợi dẫn, một sợi cho dữ liệu truyền đi (TXD) và một sợi cho dữ liệu nhận về (RXD).
Cáp RS232 thường có cấu trúc đơn giản với một sợi dẫn chung (common ground) và hai sợi dẫn dữ liệu. Điều này tạo ra một kết nối điểm-điểm giữa hai thiết bị.
Cáp RS232 thường sử dụng cắp xoắn nhẹ (twisted pair) để giảm nhiễu.RS232 thường được sử dụng cho giao tiếp một-một (point-to-point) nghĩa là chỉ có một thiết bị gửi và một thiết bị nhận dữ liệu. Nó không hỗ trợ nhiều thiết bị chia sẻ cùng một đường truyền một cách dễ dàng.

**4. RS485:**
RS485 thường sử dụng cáp đôi xoắn cản trở (twisted pair) với ít nhất hai sợi dẫn dữ liệu (A và B), và có thể có thêm các sợi dẫn khác như yêu cầu gửi (RTS) và cho phép gửi (DE).
Cáp RS485 thường được thiết kế để hỗ trợ truyền tải dữ liệu trên khoảng cách dài hơn và để chống lại nhiễu từ môi trường công nghiệp. Các sợi dẫn thường được xoắn chặt hơn để cải thiện khả năng chống nhiễu. RS485 được thiết kế cho giao tiếp đa điểm (multi-point) nghĩa là nhiều thiết bị có thể chia sẻ cùng một đường truyền. Điều này làm cho nó phù hợp cho các mạng nhiều thiết bị trong môi trường công nghiệp. RS485 được thiết kế cho giao tiếp đa điểm (multi-point) nghĩa là nhiều thiết bị có thể chia sẻ cùng một đường truyền.

**Lưu ý :** Chân RS232 và RS485: Bình thường chỉ dùng 2 chân TX (Transmit) và RX (Receive), Các chân kiểm soát luồng dữ liệu như RTS (Request to Send) và CTS (Clear to Send) có thể được sử dụng (tùy thuộc vào yêu cầu của ứng dụng).
# protocol
**1. Hoạt động của M-S trong 1 chu kì truyền nhận dữ liệu:**

**Master** : ví dụ:   **[| Địa_chỉ_slave(2byte) | function_code(2byte) | Địa_chỉ_bắt_đầu_đọc(4byte) | Số_lượng_thanh_ghi_cần_đọc(4byte) |]**

  1. Khởi tạo truyền thông: Trong một chu kỳ truyền nhận dữ liệu, Master sẽ bắt đầu quá trình truyền thông bằng cách gửi một tín hiệu bắt đầu (Start-of-Frame). Điều này sẽ đánh dấu sự bắt đầu của truyền thông và chuẩn bị các thiết bị Slave để lắng nghe.

  2. Chọn Slave: Master sau đó chọn một Slave cụ thể mà nó muốn giao tiếp. Điều này thường được thực hiện bằng cách gửi địa chỉ của Slave trong trường địa chỉ của gói tin Modbus RTU. ví dụ gửi tới địa chỉ Slave là **[02]**

  3. Gửi yêu cầu: Master gửi yêu cầu đến Slave, yêu cầu dữ liệu cụ thể hoặc thực hiện một chức năng như đọc hoặc ghi vào các thanh ghi của Slave. ví dụ đọc thanh ghi, nên function code là **[03]** ; địa chỉ là **[03E8]** ; số thanh ghi là **[0002]**. Vậy frame truyền là: **[02 03 03E8 0002]** ( đây là dạng hex, thực tế gửi ở dạng binary-vì truyền 2 dây tín hiệu 0,1)

  4. Truyền dữ liệu: Sau khi gửi yêu cầu, Master tiếp tục gửi các tín hiệu dữ liệu và chờ Slave trả lời. 

  5. Nhận phản hồi từ Slave: Slave xử lý yêu cầu từ Master và gửi phản hồi lại Master. Phản hồi này có thể chứa dữ liệu yêu cầu hoặc thông báo lỗi nếu có.

  6. Kết thúc truyền thông: Sau khi nhận được phản hồi từ Slave, Master có thể tiếp tục gửi các yêu cầu khác hoặc kết thúc truyền thông bằng cách gửi tín hiệu kết thúc (End-of-Frame).

     Các function code:(trong phạm vi Belink, chỉ cần dùng 03 và 04)
     
     ![image](https://github.com/LeslieEngr/protocol/assets/128287548/fdc7d52e-ec3d-4751-98ca-8fd24475e83e)

Một số ví dụ với các loại function code khác : 

**04.1:**

Địa chỉ Slave: 05 (địa chỉ của thiết bị Slave Modbus RTU).
Mã chức năng: 04 (mã chức năng "Read Input Registers").
Địa chỉ thanh ghi bắt đầu: 0BB8 (3000 ở dạng hex).
Số lượng thanh ghi cần đọc: 0004 (4 ở dạng hex). Vậy frame truyền là : 05 04 0BB8 0004

**04.2:**

Địa chỉ Slave: 02 (địa chỉ của Slave).
Mã chức năng: 04 (Đọc thanh ghi Input).
Địa chỉ thanh ghi bắt đầu: Ví dụ, chúng ta muốn đọc từ thanh ghi Input có địa chỉ 0100 (256 ở dạng decimal hoặc 100 ở dạng hex).
Số lượng thanh ghi cần đọc: Ví dụ, chúng ta muốn đọc 100 thanh ghi. Vậy frame truyền là : 02 04 0100 0064

**Slave**
