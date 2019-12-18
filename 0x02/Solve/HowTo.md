 
# Bài 1
Tóm tắt lại các bước giải mã và phân tích cách thức hoạt động của mã độc `2fa71019.php` được tìm thấy trên một server chạy `Wordpress`.


# Bài 2
http://ksnctf.sweetduet.info/problem/32
 - View source code của trang web :
          if (strcasecmp($_POST['password'], $password) == 0)
          cecho "Congratulations! The flag is $password";
 - Submit query: password[]=1
 - Get Flag:  FLAG_VQcTWEK7zZYzvLhX


# Bài 3
http://ksnctf.sweetduet.info/problem/31


# Bài 4
http://ksnctf.sweetduet.info/problem/35
- View soure, thấy : sqlite:database.db
- Truy cập http://ksnctf.sweetduet.info/problem/35/database.db => lấy được database
- sqlite> select * from user , lấy được Flag:
  root|FLAG_iySDmApNegJvwmxN
