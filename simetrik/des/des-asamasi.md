# DES Aşaması ve Fonksiyonları

DES Algoritması 3 aşamadan oluşur. ⤵️

1. İnitial Permutation
2. Round
3. Reverse İnitial Permutation

## 1- Initial Permutation (Başlangıç Permütasyonu)

Bu aşama DES algoritmasının ilk aşamasıdır. ⚀

Dışarıdan gelen 64 bitlik plain text'teki verilerin her biti **initial permutation tablosuna** göre yer değiştirir. 🔁


![ip-table](/resimler/ip-table.png)

Bu tabloya göre 64 bitlik verinin 58. biti ilk sıraya 50. biti ikinci sıraya gelir ve tabloya göre böyle devam eder. Böylece veri karıştırılmış olur. ⚠️

## 2- Round (Döngü)

- Round aşaması 2 ana işlemden oluşur.
     - f fonksiyonu (Dersin devamında göreceğiz.✏) 
     - Xor işlemi ([Bitsel işlemler için tıklayınız 👆](/bitsel-islemler/bitsel-islemler.md))

- İnitial Permutation işleminden gelen karıştırılmış 64 bitlik veri sağ ve sol olmak üzere 32 bit olarak 2 parçaya ayrılır. 🔛

![round-asamasi](/resimler/round-asamasi.png)

### f Fonksiyonu

- Bu fonksiyonda ilk olarak _**expension(genişletme)**_ uygulanır. Bu uygulamada **selection tablosuna** göre bazı bitler 2 kere tekrar ettirilerek 32 bitlik veri 48 bite çıkarılır. ⬆️

**Peki neden⁉️**

❗Çünkü daha önce belirttiğimiz 56 bitlik anahtarı kullaanarak 16 tane 48 bitlik anahtar üretiliyor demiştik. Veriyi anahtar uzunluğuna eşitlemek için bu işlem gerçekleştiriliyor.

![selection-table](/resimler/selection-table.png)

Tabloya göre 32 bitlik verinin başına 32.biti koyarak başlıyoruz, 12 ile 13. biti koyduktan sonra 12 ve 13. biti tekrar koyuyoruz ve böyle devam ediyor. En sonundada 48 bitlik veri elde etmiş oluyoruz.

⚠️Örneği inceleyerek daha iyi anlayabilirsiniz.

> R0 = 1111 0000 1010 1010 1111 0000 1010 1010 

> expansion_edilmis(R0) = 011110 100001 010101 010101 011110 100001 010101 010101


- Anahtar üretici tarafından 56 bitlik anahtar kullanılarak her döngüde kullanılacak 16 adet birbirinden farklı 48 bitlik anahtarlar üretilir.✔

- 32 bitten 48 bite genişletilen veri, kaçıncı aşamadaysa o aşamaya ait 48 bitlik veri ile **xor işlemine** tabi tutulur. Sonuç olarak xorlanmış 48 bitlik veri oluşur. ➕

- Oluşan 48 bitlik yeni veri 6'şar bite bölünerek 8 grup elde edilir ve her grup **S kutularına** gönderilir.📦

- f fonksiyonunun içinde 8 adet S kutusu bulunur ve bu kutulara giriş **6 bit çıkış 4 bittir.**  ⬇️

- Her S kutusu 4 satur, 16 sütundan oluşur ve 64 adet 4 bitlik sayıyı barındırır.(Her S kutusunun tablosu birbirinden farklıdır.🔁)

S1 kutusuna ait tablo. (Diğeleri internette kolaylıkla bulunabilir.🌐)

![s1-table](/resimler/s1-table.png)

⚠️Örneğin S1 tablosuna 37 sayısıs girerse, bu ikilik sayı sisteminde 100101 'e karşılık gelmektedir, sonuç 8 , binary 1000, olacaktır.

**Peki nasıl⁉️**

- ❗100101 ikilik sayısının  başındaki(en sol) ve sonundaki (en sağ) bitler birleştirilir ve elde edilen binary sayısının onluk tabandaki değeri satır sayısını verir.
 
  11(2) => 3(10).satır
 
- ❗100101 ikilik sayısının ortdaki 4 bit birleştirilirve eldeedilen binary sayısının onluk tabandaki değeri  sütun sayısını verir.
 0010(2) => 2(10).sütun
 
   Yukarıdaki tabloda 3 satır 2. sütundaki değer 8'e eşittir. Yani sonuç 8 [1000(2)] olacaktır.  
   
_Bu işlemler sonucunda 48 bitlik veri tekrardan 32 bite dönüştürülmüş oldu._


🔚 Son olarak 32 bitlik expansion uygulanmış veri tekrardan permutation işlemine tabi tutuluyor. Tabi ayrı bir tablosu var bununda 😁

![f-func-perm-table](/resimler/f-func-perm-table.png)

Aşağıdaki örneği inceleyerek algılayabilirsiniz yukarıdaki permutation işlemlerinin aynısı sadece tablo değişik.

Örneğin S kutularından çıkan veriler birleştirildiğinde oluşacak olan veri K olsun.

> K = 0101 1100 1000 0010 1011 0101 1001 0111

Oluşacak yeni veriye L diyelim. Yukarıdaki tabloya göre L'nin ilk biti K'nın 16.biti olacak ve böyle sırayla devam edecek.
 
> L = 0010 0011 0100 1010 1010 1001 1011 1011 olur.
 
 Yani f fonksiyonunun sonucu L'dir. Sonuç olarak f fonksiyonun algoritması aşağıdaki gibidir.
 
 ![f-func-algorithm](/resimler/f-func-algorithm.png)


### XOR İŞLEMİ ➕

- f fonksiyonu sonucu ortaya çıkan 32 bitlik veri ile 64 bitlik verinin sol kısmı (oda 32 bit) xor işlemine girer.

![round-dongusu](/resimler/round-dongusu.png)

- Bu döngü işlemi toplamda 16 kez tekrarlanır. 🔃
 

## 3- Reverse İnitial Permutation (Ters Permütasyon)

Bu DES algroritmasının son adımıdır. Tekrar permütasyon uygulanır tabi **reverse permutation tablosuna** göre ve 64 bitlik **cipher text(şifreli metin)**🛅 çıkışa verilir.

![reverse_perm_table](/resimler/reverse_perm_table.png)

⚠️ Örneğin DES algoritması sonucu şifrelenmiş 64 bitlik verinin Sol ve Sağ kısmı aşağıdaki gibi olsun.

> L16 = 0100 0011 0100 0010 0011 0010 0011 0100
> R16 = 0000 1010 0100 1100 1101 1001 1001 0101

Yukarıdaki tabloya göre **sonuç verinin**(64 bit olacak) ilk biti yukarıdaki sonuçların birleşiminin 40'ıncı biti. Tabi saymaya soldan başlıyoruz. Solda 32 bit olduğuna göre sağdakinin ilk 8'inci bitini alacağız ki oda 0'dır.

> L16+R16 = 0100 0011 0100 0010 0011 0010 0011 0100 0000 101**0** 0100 1100 1101 1001 1001 0101 


Hepsini uyguladığımızda en sonki sonuç;

> cipher text = 10000101 11101000 00010011 01010100 00001111 00001010 10110100 00000101

- Bu DES aşamaları plain text'in tüm 64 bit'lik gruplarına yapılmaktadır.

# Şifre Çözme İşlemi

- Şifrelenmiş verinin çözülmesi işlemi ise yukarıdaki işlemlerin tersten yapılmasıdır. 😛

- ⚠️ Bu arada kullandığınız 16 adet Key'leride tersten işleme dahil etmeniz gerekir. Yani şifrelerken ilk sırada KEY1'i kullandıysanız, şifre çözerken ilk sırada KEY16'yı kullanmalısınız aksi takdirde şifreli metni yanlış çözümleyeceksiniz.

[**Ana Sayfaya Dön**](/README.md)
