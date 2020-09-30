# DES Şifreleme ve Şifre Çözme 🔱

DES algoritması içerisinde bulunan **f fonksiyonu**, **initial permutation işlemi**, **reverse initial permutation** işlemi ileride anlatılacaktir. 

Şimdilik 64 bitlik plain text verinin hangi yollardan, ne sırada geçtiğini bilseniz yeterli.

![des_algorithm](/resimler/des_algorithm.png)

- Her bir L'nin değeri (L0 hariç) bir önceki R değerine eşittir. L0 ise direk olarak plain text'in 32 bitlik degerine eşittir. ⬆️

- Her bir R degeri bir önceki **xor işleminin sonucuna** eşittir. ➕
- Her R değeri anahtar ile** f fonksiyonuna** girer ve çıktıktan sonra L degeri ile **xor** işlemine tabi tutulur. Böylece bir sonraki R değeri elde edilmiş olunur.
- 16 kere tekrar eden bu döngü DES algoritmasının **Round** aşamasıdır. 🔃
- En sonunda **reverse initial permutation** aşamasına girilir ve sonuç şifreli 64 bitlik cipher text'tir. 🔒

[**Ana Sayfaya Dön**](/README.md)
