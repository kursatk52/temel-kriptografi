# DES Anahtar Oluşturma (Key Schedule)

## Anahtar Oluşturma Algoritması

![key-generator-algorithm](/resimler/key-generator-algorithm.png)

## Anahtar Oluşturma İşlemi

- İlk olarak 64 bitlik anahtar girilir. Girilen 64 bitlik anahtar içinden PC-1 tablolsuna göre 56 bit seçilir.

  ![pc-1-table](/resimler/pc-1-table.png)
  
     - Oluşturulacak 56 bitlik anahtara K diyelim, ilk girilen 64 bitlik anahtara B diyelim.
     
     - Bu tabloya göre orjinal D'deki 57.bit K'nın 1.biti olacak, B'deki 49.bit K'nın 2.biti olacak ve   böylece 56 bite kadar gidecek.  

    > **Orjinal Anahtar (B)(64 bit):** 00010011 00110100 01010111 01111001 10011011 10111100 > > 11011111 11110001

     olursa;

     > **Key (K)(56 bit):** 1111000 0110011 0010101 0101111 0101010 1011001 1001111 0001111 olur.  

- Oluşturulan 56 bitlik anahtar 28bit olmak üzere ikiye ayrılır. Bunlarada  N0 ve P0 diyelim.
 
     **Key (K)(56 bit):** 1111000 0110011 0010101 0101111 0101010 1011001 1001111 0001111
     
     **N0:** 1111000 0110011 0010101 0101111
     
     **P0:** 0101010 1011001 1001111 0001111
     olur.

- Bu ikisi kullanılarak 16 adet 48 bitlik anahtarlar oluşturulur.
     -Her anahtar kendinmden önceki anahtarın N ve P değerinin sola kaydırılmasından oluşturulur. **Tabi her aşamadaki sola kaydırma miktarı değişiktir.** Aşağıdaki tabloda her turdaki kaydırma miktarı verilmiştir.
     
     ![shift-table](/resimler/shift-table.jpeg)
          
     -  Bu tabloya göre 1. anahtar oluşturuluyrken N0 ve P0 bitleri 1 kez sola kaydırma işlemi uygulanır.
     -  3. aşamada ise N2 ve P2 bitlerini 2 kez kaydırıldıktan sonra **Key3** oluşturulur.

- 1. pozisyondaki bit'e sola kaydırma işlemi yaptığımızda sıranın en sonuna geçiyıor.

- Yukarıdaki N0 ve P0 değerlerine göre oluşturulan 16 adet N ve P değerleri aşağıdaki gibi olur.

     N0 = 1111000011001100101010101111
     P0 = 0101010101100110011110001111
     
     N1 = 1110000110011001010101011111
     P1 = 1010101011001100111100011110
     
     N2 = 1100001100110010101010111111
     P2 = 0101010110011001111000111101
     
     N3 = 0000110011001010101011111111
     P3 = 0101011001100111100011110101
     
     N4 = 0011001100101010101111111100
     P4 = 0101100110011110001111010101
     
     N5 = 1100110010101010111111110000
     P5 = 0110011001111000111101010101
     
     N6 = 0011001010101011111111000011
     P6 = 1001100111100011110101010101
     
     N7 = 1100101010101111111100001100
     P7 = 0110011110001111010101010110
     
     N8 = 0010101010111111110000110011
     P8 = 1001111000111101010101011001
     
     N9 = 0101010101111111100001100110
     P9 = 0011110001111010101010110011
     
     N10 = 0101010111111110000110011001
     P10 = 1111000111101010101011001100
     
     N11 = 0101011111111000011001100101
     P11 = 1100011110101010101100110011
     
     N12 = 0101111111100001100110010101
     P12 = 0001111010101010110011001111
     
     N13 = 0111111110000110011001010101
     P13 = 0111101010101011001100111100
     
     N14 = 1111111000011001100101010101
     P14 = 1110101010101100110011110001
     
     N15 = 1111100001100110010101010111
     P15 = 1010101010110011001111000111
     
     N16 = 1111000011001100101010101111
     P16 = 0101010101100110011110001111

 - Oluşturulan N ve P değerleri birleştirilerek (N0 ve P0 hariç) 16 adet NP ikilisi oluşturulur. Oluşturulan bu ikililerden aşağıdaki tabloya göre 48 bit seçilir ve 16 adet 48 bitlik anahtarlar oluşturulmuş olur.
 
   ![pc-2-table](/resimler/pc-2-table.jpeg) 
   
   Bu tabloya göre anahtarın birinci biti NP ikilisinin 14.bitidir, ikinci biti NP ikilisinin 17.bitidir  ve böyle devam eder.
   
        > N1P1: 11100001100110010101010111111010101011001100111100011110
   
   ise
   
        > Key1 : 000110 110000 001011 101111 111111 000111 000001 110010 olur.
   
   Bu şekilde 16 adet anahtar oluşturulur.
   
   [**Ana Sayfaya Dön**](/README.md)
  
   
