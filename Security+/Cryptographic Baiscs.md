# 1 caeasr cipher #
![caeasr cipher](images/cryptographic%20basics.png)

---

# 2 symmetric cipher #
- using the mail to send the message ` msg.txt`, we usually need to ***encode*** it 
  ```
  base64 msg.txt > msg.base64
  base64 -d msg.base64 > msg.txt
  ```
- use openssl to ***generate a secret key***
  ```
  openssl genpkey -algorithm rsa -out key.key
  ```
- use openssl to ***encrypt and decrypt***a message
  ```
  openssl pkeyutl -encrypt -inkey key.key -in msg.txt -out msg.enc
  openssl pkeyutl -decrypt -inkey key.key -in msg.en -out msg.txt
  ```

---

# 3 asymmetric cipher #
- using openssl generate ***private and public key pair***
  ```
  openssl genpkey -algorithm rsa -out privat.key
  openssl rsa -pubout -in private.key -out public.key
  ```
- use openssl to ***encrypt and decrypt***a message
  ```
  openssl pkeyutl -encrypt -inkey public.key -pubin -in filename.txt -out filename.enc
  openssl pkeyutl -decrypt -inkey private.key -in filename.txt -out filename.enc
  ```

---

# 4 Hash Function #
- using openssl to create ***hash*** of a file
  ```
  openssl dgst -md5 filename
  openssl dgst -sha256 filename
  ```
   
