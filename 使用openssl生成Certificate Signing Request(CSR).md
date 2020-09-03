## 使用openssl生成Certificate Signing Request(CSR) 

1. 使用openssl 命令生成2048bit RSA private key 和 csr

   ```
   openssl req -newkey rsa:2048 -keyout PRIVATEKEY.key -out MYCSR.csr
   ```

   

   

