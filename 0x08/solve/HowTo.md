- Đọc raw content trong từng packet của file for.pcap, thấy nội dung của các ARP packet không có gì đáng chú ý, 
trong NTP pạket thứ 2 có chứa chuỗi: iVBORw0KGgoAAAANSUhEUgAAAzcAAADiCAIAAAD8qK6MAA, thử decode base64 ta nhận được
PNG

IHDR7
=> có thể là raw content của một bức ảnh
- Lấy tất cả dữ liệu bằng UDP Stream, bỏ đoạn .AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA.. của NTP packet đầu tiên,
- Decodce đoạn mã còn lại ta thu được cờ matesctf{s0_m4ny_3xf1l_pr0t0c0lz}
