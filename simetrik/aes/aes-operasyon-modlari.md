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
