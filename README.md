# PANDAS NEDİR?

Pandas Kütüphanesinin ne olduğu ve bu kütüphane ile (**Özellikle Veri Çerçevesi (Data Frame) konusunda**) neler yapılabildiğine dair öğrendiklerimi paylaştığım repo.

Pandas, veri işleme ve veri analizi için Python Python programlama dilinde yazılmış olan bir Python kütüphanesidir. 
Bu kütüphane, **Seriler (Series)** ve **Veri Çerçevesi (DataFrame)** isimli iki veri yapısının üzerine kurulmuştur. serileri tek boyutlu diziler, veri çerçevelerini ise iki boyutlu matrisler (SQL ya da Excel tabloları) gibi düşünebiliriz.

Kütüphane özellikleri

- İndeksli DataFrame (veri çerçevesi) objeleri ile veri işlemesi yapabilmek.
- Hafızadaki veya farklı türlerde bulunan veriyi okuyabilmek ve yazabilmek için araçlar sağlamak.
- Veri sıralama ve bütünleşik kayıp veri senaryolarına karşı esnek imkanlar sunmak
- Veri setlerinin tekrar boyutlandırılması veya döndürülmesi.
- Etiket bazlı dilimleme, özel indeksleme ve büyük veri setlerini ayrıştırmak
- Veri çerçevesine sütun ekleme veya var olan sütunu çıkarma.
- Veri gruplama özelliği ile ayırma-uygulama-birleştirme uygulamaları yapılabilmek.
- Veri setlerini birleştirilmek ve birbirine eklenmek.
- Çok boyutlu veriden, daha az boyutlu veri elde edilebilmek.
- Veri filtrelemek.

Kütüphane performans konusunda son derece iyidir. Bu yüzden kütüphanenin önemli parçaları CPython ve C üzerinde yazılmışlardır.

## Pandas Veri Çerçevesi (Data Frame) Konu Başlıkları

1. [Veri Çerçevesi (Data Frame) Oluştur](01_Veri_Cercevesi_Olustur.ipynb)
   
   - DataFrame() Fonksiyonu
   
   - read_csv() Fonksiyonu
     
     - index_col Parametresi
   
   - read_table() Fonksiyonu
     
     - delimiter Parametresi
   
   - read_excel() Fonksiyonu
   
   - read_json() Fonksiyonu
   
   - read_html() Fonksiyonu
   
   - read_clipboard() Fonksiyonu

2. [Excel Dosyaları ile Çalışmak](02_Excel_Dosyasi_ile_Calis.ipynb)
   
   - read_excel() Fonksiyonu
     
     - header ve names Parametreleri
     
     - sheet_name Parametresi
     
     - decimal Parametresi

3. [Veriyi Keşfet (İncele)](03_Veriyi_Kesfet_incele.ipynb)
   
   - head() Fonksiyonu
   - tail() Fonksiyonu
   - columns Fonksiyonu
   - len() Fonksiyonu
   - info() Fonksiyonu
   - dtypes Fonksiyonu
   - describe() Fonksiyonu
   - shape Fonksiyonu
   - index Fonksiyonu
   - isnull() Fonksiyonu
   - value_counts() Fonksiyonu

4. [Veri Seçim Yöntemleri](04_Secim_Yontemleri.ipynb)
   
   - iloc[] Metodu
   - loc[] Metodu
   - Index() Fonksiyonu
   - lambda() Fonksiyonu
   - at[] metodu
   - iat[] metodu

5. [Eksik - Kayıp Veri Yöntemleri](05_Eksik_Kayip_Veri_Yontemleri.ipynb)
   
   - isnull() Fonksiyonu
   
   - dropna() Fonksiyonu
     
     - axis Parametresi
     
     - inplace Parametresi
     
     - thresh Parametresi
   
   - fillna() Fonksiyonu
     
     - value Parametresi
     - method Parametresi

6. [Veri Düzenleme Yöntemleri](06_Duzenleme_Yontemleri.ipynb)
   
   - İndeks Değerlerini Ayarlamak
     
     - index_col Parametresi
   
   - set_index() Fonksiyonu
   
   - Sütunları Atla
     
     - usecols Parametresi
   
   - Satırları Atla
     
     - skiprows Parametresi
   
   - Sütun Ekle
   
   - Satır ya da Sütun Sil
     
     - drop() Fonksiyonu
       
       - axis Parametresi
       
       - inplace Parametresi
     
     - drop_duplicates() Fonksiyonu
       
       - subset Parametresi
       
       - keep Parametresi
   
   - String Metotları
   
   - transpose() Fonksiyonu
   
   - apply() Fonksiyonu
   
   - Veri Çerçevelerini Birleştir
     
     - concat() Fonksiyonu
     
     - join() Fonksiyonu
       
       - how parametresi
       
       - right join
       
       - outer join
       
       - inner join
     
     - merge() Fonksiyonu
       
       - on Parametresi
       
       - how Parametresi
         
         - inner Seçeneği
         
         - outer Seçeneği
         
         - left Seçeneği
         
         - right Seçeneği
         
         - cross Seçeneği
       
       - left_on Parametresi
       
       - right_on Parametresi
       * suffixes Parametresi 

7. [Veri Sıralama Yöntemleri](07_Siralama_Yontemleri.ipynb)
   
   - sort_index() Fonksiyonu
     
     - ascending Parametresi
     - axis Parametresi
   
   - sort_values() Fonksiyonu
     
     - by Parametresi
     - ascending Parametresi
     - - na_position Parametresi

8. [Veri Filtreleme Yöntemleri](08_Filtreleme_Yontemleri.ipynb)
   
   - Karşılaştırma Operatorü Kullanımı
   - between() Fonksiyonu
   - Mantıksal Operatör Kullanımı

9. [Gruplama Yöntemleri](09_Gruplama_Yontemleri.ipynb)
   
   - groupby() Fonksiyonu

10. [pivot_table() Fonksiyonunun Kullanımı](10_pivot_table() Fonksiyonunun Kullanımı.ipynb)

11. [melt() Fonksiyonu](11_Melt_Fonksiyonu.ipynb)

12. [Operator_Kullanımı](12_Operator_Kullanimi.ipynb)
    
    - Aritmetik İşlem Operatörleri
      
      - sum() Metodu
      - mean() Metodu
    
    - Toplama, Çıkarma, Çarpma ve Bölme İşlemleri
      
      - Toplama Operatörü
      - Çıkarma Operatörü
      - Çarpma Operatörü
      - Bölme Operatörü
    
    - Mantıksal / Karşılaştırma Operatörleri
      
      - Büyüktür (>),
      - Küçüktür (<),
      - Eşittir (==),
      - Eşit Değildir (!=),
      - İçerir (contains),
      - İçermez / Değil (not)
