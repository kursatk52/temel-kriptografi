# AES Operasyon Modları

- Bir bloktan uzun verilen şifrelenmesi bazen tam olarak işe yaramayabilmektedir. Örneğin resimleri blokları ayırıp sırasıyla şifrelemek aşağıdaki gibi sonuç verebilmektedir. Bu da verinin güvenliğini tehlikeye atmaktadır.

![aes-image-encrpytion](/resimler/aes-img-enc.png)

- AES şifrelemede kullanılabilecek modlar;

1. Electronic Code Block (ECB)
2. Cipher Block Chain (CBC)
3. Counter (CTR)
4. Cipher Feed Back (CFB)
5. Output Feed Back (OFB)

## 1. Electronic Code Block (ECB)

- Yukarıdaki resmin şifrelendiği moddur.

- Giriş mesajı bloklara bölünür ve sırasıyla AES işlemine tabi tutulur ve oluşan şifreli bloklar yine sırayla birleştirilir. 
- Bu modun birden fazla bloktan oluşan verilerde kullanımı sakıncaılıdır.
 
 ![aes-ecb](/resimler/aes-modes-ecb.png)

## 2. Cipher Block Chain (CBC)

- İlk blok şifrelenmeden önce "Initialization Vector (IV)" ile xor'lanır sonra şifrelenir.
  
- Oluşturulan bu şifreli blok aynı zamanda bir sonraki şifrelenecek bloğun IV'si olur.

 ![aes-cbc](/resimler/aes-modes-cbc.png)
 
- En sonda oluşturulan **Cipher Text**'ler birleştirilir.

- Şifre çözerken ise **Cipher Text 1** ile **IV** **xorlanır**. Elde edilen sonuç **Plain text 1** 'dir aynı zamanda bir sonraki bloğun **IV**'sidir.


## 3. Counter (CTR)

- Bu durumda bir counter değeri vardır ve şifrelenen plaintext değil counter değeridir.

- İlk counter hariçi diğerleri hep bir öncekinin bir arttırılmış halidir.
- Şifrelenen _counter_ ile _plaintext_ **xor** 'lanır ve **cipher text** bulunmuş olur.

 ![aes-ctr](/resimler/aes-modes-ctr.png)
 
 - Her AES işlemi birbirinden bağımsız olduğu için AES işlemleri paralelde çalıştırılarak yüksek performans elde edilebilir.
 
 ## 4. Cipher Feed Back (CFB)

 ![aes-cfb](/resimler/aes-modes-cfb.png)
 
 - Bu işlem bitene kadar böyle devam ediyor.
 
 ## 5. Output Feed Back (OFB)
 
 - Algoritma olarak CFB ile benzer. Arasındaki farklılık ise IV oluşturulurken **cipher text** değil **EIV** kullanılmasıdır.

  
  ![aes-ofb](/resimler/aes-modes-ofb.png)
 
 
 [**Ana Sayfaya Dön**](/README.md)


 
