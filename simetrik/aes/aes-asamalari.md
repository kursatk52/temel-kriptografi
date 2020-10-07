# AES Aşaması ve Fonksiyonları

- AES'in aşamaları;

1. Sub Bytes
2. Shift Rows
3. Mix Columns
4. Add Round Key

## 1- Sub Bytes

- Durum tablosundaki her bir byte **AES Sub Bytes** tablosuna göre yeni byte değeri ile değiştiriliyor. 
</br></br>
Örnek durum tablosu</br>
![aes-durum-tablosu](/resimler/aes-durum-tablosu.png)

- Bu tablo her seferinde aynı değildir. Belirli bir matematiğe göre oluşturulmaktadır.
</br></br>
Örnek sub bytes tablosu</br>
![s-box](/resimler/aes-s-box.png)
</br>

- Durum tablosundaki S0'ın içeriği hexadecimal olarak <b>32</b> ise ,_ki örnek tabloda öyle_, **x = 3 ve y = 2** olur.
Yukarıdak s tablosuna baktığımızda x = 3 ve y = 2 için değer **23**'tür. Bu durumda **S0'ın yeni değeri 23 olur** ve **her byte** için bu işlemler yapılır.
- S tablosunda **her değer farklı olduğu için** şifre çözerken de 23'ün x ve y değerlerine bakıp **xy** biçiminde birleştiriyoruz.

## 2- Shift Rows

- Sub bytes işleminden geçmiş durum tablosundaki satırlar **Cycled Rotation (Dairesel Dönüşüm)**'a tabi tutulur.

![shift-rows](/resimler/shiftrows.png)

- Şifre çözerken ise bu işlemler ters yönde. **Yani sola değil sağa uygulanır.**

## 3- Mix Columns
 - Burada ise sütunlar üzerinden işlemler yapılır.
 
 - Durum matrisindeki her bir sütunu alıyoruz ve verilen matris (aşağıdaki tabloda görebilirsiniz) ile çarpıyoruz.
 
 ![mix-columns](/resimler/mixcolumns.png)
 
 ## 4- Add Round Key
 
 - _Durum matrisindeki_ her bir sütunu, **tur anahtarını içeren matristeki (nasıl oluşturulduğunu göreceğiz)** her bir sütun ile **xor** işlemine tabi tutulur.

![add-round-key](/resimler/addroundkey.png)

- Şifre çözmek için ise şifrelenmiş olan matris tekrar **_o tura_ ait anahtar matrisi** ile **xor**'lanır.


[**Ana Sayfaya Dön**](/README.md)


