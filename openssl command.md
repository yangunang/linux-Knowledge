#                       openssl command 

## 1. create csr file (java生成证书请求文件)

```
  keytool -genkey -alias tomcat -keyalg RSA -keysize 2048 -keystore ./server.jks

  keytool -certreq -alias tomcat -keystore erver.jks -file certreq.csr
```

   证书颁发机构，返回cer   file, 尝试下面两种方式

```
  openssl x509 -inform DER -in certificate.cer -out certificate.crt
  openssl x509 -inform PEM -in certificate.cer -out certificate.crt
```



## 2.Extract .key and .crt files from JKS file

​    **(提取key和crt文件从jks文件)**

```
keytool -export -alias tomcat -file server.der -keystore server.jks
```

```
openssl x509 -inform der -in server.der -out server.crt
```

```
keytool -importkeystore -srckeystore server.jks -destkeystore keystore.p12 -deststoretype PKCS12
```

```
openssl pkcs12 -in keystore.p12 -nodes -nocerts -out server.key
```

## 3.create pfx file  

```
openssl pkcs12 -export -out   example.pfx  -inkey  nclient.key -in  nclient.crt  -certfile beijing2CA.crt  -certfile genCA.crt
```

## 4 verify  key crt  

```
openssl x509 -noout -modulus -in cert.crt | openssl md5
openssl rsa -noout -modulus -in privkey.key | openssl md5
```

