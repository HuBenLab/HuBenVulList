# OTCMS was discovered to contain an arbitrary file download vulenrability via the filename
## Description
    OTCMS was discovered to contain an arbitrary file download vulenrability via the filename
## Vendor Homepage
    http://otcms.com/

## Author
    HuBenLab
## Proof of Concept
Post an article after logging in as a member user.

![image-20230606101010699](./img/image-20230606101010699.png)

Add additional parameters to the packet capture

![image-20230606101031313](./img/image-20230606101031313.png)

payload

```
file=../../../../../../../../../../../../../etc/passwd&isRenameFile=1&fileName=1.php
```

Then it can be downloaded in the foreground to read the passwd file.

![image-20230606101126190](./img/image-20230606101126190.png)