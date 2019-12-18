 
# Bài 1
Tóm tắt lại các bước giải mã và phân tích cách thức hoạt động của mã độc `2fa71019.php` được tìm thấy trên một server chạy `Wordpress`.


# Bài 2
http://ksnctf.sweetduet.info/problem/32
 - View source code của trang web :
          if (strcasecmp($_POST['password'], $password) == 0)
          cecho "Congratulations! The flag is $password";
 - Với strcasecmp, dùng array để bypass: 
   Dùng Burpsuite bắt gói tin và submit query: password[]=1
 - Get Flag:  FLAG_VQcTWEK7zZYzvLhX


# Bài 3
http://ksnctf.sweetduet.info/problem/31
- View source code của trang web :
    + Mảng shipname chứa 11 phần tử, mỗi lần nhấn button Gacha, sẽ thấy random ra 1 phần tử trong shipname
    + Tuy nhiên hàm random: $ship[] = mt_rand(0, count($shipname)-2); chỉ random đến phần tử thứ 10, phần tử thứ 11 chính là Flag
    + Cần sửa giá trị signature trong cookie cho đúng, sử dụng Hashpump:
        Input signature:     24b7447578c89ea8f5f8854d60e253f23bb5b8856d8a135c19af423db354ac60a1a4c932cecd800a0550211e8cc6e28e73e1ac93e7b9c786adc24702e48701c5
         


# Bài 4
http://ksnctf.sweetduet.info/problem/35
- View soure, thấy : sqlite:database.db => lấy được đường dẫn tới file dữ liệu.
- Truy cập http://ctfq.sweetduet.info:10080/~q35/auth.php => lấy được database
- sqlite> select * from user , lấy được Flag:
  root|FLAG_iySDmApNegJvwmxN
