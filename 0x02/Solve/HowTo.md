 
# Bài 1
Tóm tắt lại các bước giải mã và phân tích cách thức hoạt động của mã độc `2fa71019.php` được tìm thấy trên một server chạy `Wordpress`.


# Bài 2
http://ksnctf.sweetduet.info/problem/32
 - View source code của trang web :
          if (strcasecmp($_POST['password'], $password) == 0)
          cecho "Congratulations! The flag is $password";
 - Với strcasecmp, dùng array để bypass: 
   Dùng Burpsuite bắt gói tin và submit query: password[]=1
 - Lấy được Flag:  FLAG_VQcTWEK7zZYzvLhX


# Bài 3
http://ksnctf.sweetduet.info/problem/31
- View source code của trang web :
    + Mảng shipname chứa 11 phần tử, mỗi lần nhấn button Gacha, sẽ thấy random ra 1 phần tử trong shipname
    + Tuy nhiên hàm random: $ship[] = mt_rand(0, count($shipname)-2); chỉ random đến phần tử thứ 10, phần tử thứ 11 chính là Flag
    + Cần sửa giá trị signature trong cookie cho đúng, sử dụng Hashpump:
        Input signature: 24b7447578c89ea8f5f8854d60e253f23bb5b8856d8a135c19af423db354ac60a1a4c932cecd80
                         a0550211e8cc6e28e73e1ac93e7b9c786adc24702e48701c5 (signature ban đầu khi gancha)
        Input data        : 1 (giá trị của ship trong cookie)
        Input key length  : 21 (Word Counter đoạn : FLAG_????????????????)
        Input Data to add : ,10 (theo format của đoạn code: $ship = explode(',', $_COOKIE['ship'])
                           trong đó 10 là index của yumato(Flag) )
    => Sau Hashpump:
c9ef7bfe7acb622ecda2d108392d190a1540949652c72be0d49fca0946c3b15cbbd4c877b69ac90a3ef04de1b890a0527070e26b317e42bc6e37738b5a2de02d
1\x80\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\xb0,10
    + Được signature mới : c9ef7bfe7acb622ecda2d108392d190a1540949652c72be0d49fca0946c3b15cbbd4c877b69ac90a3ef04de1b890a0527070e26b317e42bc6e37738b5a2de02d
    + Lấy ship mới bằng cách sửa \x thành %
    + Forward request mới, nhận được Flag:
               FLAG_uc8qVFa8Sr6DwYVP

        
# Bài 4
http://ksnctf.sweetduet.info/problem/35
- View soure, thấy : sqlite:database.db => lấy được đường dẫn tới file dữ liệu.
- Truy cập http://ctfq.sweetduet.info:10080/~q35/auth.php => lấy được database
- Truy vấn tới bảng user:
      sqlite> select * from user , lấy được Flag:
      root|FLAG_iySDmApNegJvwmxN
