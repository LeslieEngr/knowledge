#UART/USART  - Universal Asynchronous Receiver/Transmitter
  - USART là truyền thông đồng bộ, tức cùng baudrate, UART là truyền thông không đồng bộ.
  - Dùgn 2 chân Rx tx, gnd để truyền dữ liệu .
  - Có thể có 2 chân rts-request to send , cts-clean to send. Chúng dùng để kiểm soát luồng dữ liệu
  - Frame truyền (thường là 8 bit, giới hạn là 9bit) : 1 Start bit + 5-9 bits data + 0-1 bit parity + 1-2 stop bit
    + Start bit : thường cao, chỉ khi bắt đầu thì hạ xuống Low
    + Parity bit: kiểm tra tính chẵn/lẻ của tổng số bit 1 trong data bits. 0 là tính chẵn, 1 là tính lẻ
    + stop bit : khi truyền xong, nó sẽ lên cao ít nhất là 2 bit để báo rằng lần truyền đã xong.
  
