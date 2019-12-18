# Bài 1
Cơ bản về `Basic Auth`
https://ksnctf.sweetduet.info/problem/8

- Download file pcap và mở bằng Wire Shark:
- Trong gói tin HTTP - 502 /~q8/ HTTP/1.1 có chứa Flag:
    + Hypertext Tranfer Protocol:
    Authorization: Basic cTg6RkxBR181dXg3eksyTktTSDhmU0dB
    Credentials:  q8:FLAG_5ux7zK2NKSH8fSGA



# Bài 2
Level nâng cao
https://ksnctf.sweetduet.info/problem/9

- Download file pcap và mở bằng Wire Shark:
- Trong gói tin (số 37) HTTP - 701 /~q9/htdigest HTTP/1.1 :
     [truncated]Authorization: Digest username="q9", realm="secret", 
     nonce="bbKtsfbABAA=5dad3cce7a7dd2c3335c9b400a19d6ad02df299b", uri="/~q9/htdigest", 
     algorithm=MD5, response="d9f18946e5587401c303b34e00a059eb", qop=auth, nc=00000002, cnonce=
-  https://hashtoolkit.com/ : 
        MD5(response) = c627e19450db746b739f41b64097d449:
        bbKtsfbABAA=5dad3cce7a7dd2c3335c9b400a19d6ad02df299b:00000002:6945eb2a7ba8cf7f:
        auth:e09fc8a14736c6cba6d71e8af5781852
- MD5(1) = c627e19450db746b739f41b64097d449
  MD5(2) = e09fc8a14736c6cba6d71e8af5781852
