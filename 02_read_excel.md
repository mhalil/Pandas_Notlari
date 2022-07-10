# Excel dosyasını içe aktarmak

## read_excel() fonksiyonu

**Excel** ve **Calc** dosyalarının içeriğini çalışmamıza dahil etmek için **read_excel()** fonksiyonunu kullanmalıyız.

<u>Bu fonksiyon;</u>

* **xls, xlsx, xlsm, xlsb, odf, ods** ve odt **uzantılı** dosyaları destekler.

* Yerel bir dosya sisteminde veya bir URL'den depolanan excel dosyalarını yükleyebilir.

* URL için **http, ftp, s3** ve **dosya**yı destekler.

* Ayrıca tek bir çalışma sayfasından veya bir sayfa listesinden okumayı da destekler.

* İki sayfayı okunurken, **DataFrame**'i bir Sözluk yapısı (Dict) döndürür.

```python
pd.read_excel(dosya_adi)
```

Bu fonksiyon kullanıldığında, varsayılan olarak, excel dosyasının ilk çalışma sayfası yüklenir ve ilk satır bir Veri Çerçevesi (DataFrame) başlığı (sütun adı) olarak ayarlanır.

### header ve names Parametreleri

**read_excel ()** fonksiyonu, Excel'deki ilk satırı varsayılan olarak bir başlık kabul eder ve bunu Veri Çerçevesi (DataFrame) sütun adları olarak kullanır. Excel dosyasındaki ilk satırın başlık değil, bir veri olduğu düşünüldüğünde, yani sadece verilerden oluşan excel dosyası ile çalıştığımızda, **header=None** parametresi kullanılmalıdır. Bu durumda Başlık (sütun adlarını) belirtmek için **names** parametresi kullanılır. 

İlk olarak **OSD** uzantılı bir dosyayı çalışmamıza dahil edip içeriğine bakalım.

```python
basliksiz = pd.read_excel("basliksiz.ods")
print(basliksiz.head())
```

çıktı;

|     | 9   | 82  | 246 |
| --- | --- | --- | --- |
| 0   | 7   | 78  | 180 |
| 1   | 8   | 83  | 565 |
| 2   | 6   | 82  | 486 |
| 3   | 10  | 37  | 615 |
| 4   | 2   | 18  | 341 |

Gördüğünüz gibi ilk satır başlık değil veriden oluşuyor. Bunu **header=None** ve **names** parametreleri ile düzenleyelim.

```python
baslik = ["Birler", "Onlar", "Yüzler"]
basliksiz = pd.read_excel("basliksiz.ods", header = None, names = baslik )
print(basliksiz.head())
```

çıktı;

|     | Birler | Onlar | Yüzler |
| --- |:------ | ----- | ------ |
| 0   | 9      | 82    | 246    |
| 1   | 7      | 78    | 180    |
| 2   | 8      | 83    | 565    |
| 3   | 6      | 82    | 486    |
| 4   | 4      | 37    | 615    |

Aylara göre doğum sayılarını barındıran dosyamızı çalışmamıza dahil edip ilk 5 veriye göz atalım.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx")
print(df.head())
```

çıktı:

|     | Yıl  | Toplam  | Ocak   | Şubat  | Mart   | Nisan  | Mayıs  | Haziran | Temmuz | Ağustos | Eylül  | Ekim   | Kasım | Aralık |
| --- | ---- | ------- | ------ | ------ | ------ | ------ | ------ | ------- | ------ | ------- | ------ | ------ | ----- | ------ |
| 0   | 2001 | 1323341 | 170397 | 103476 | 107912 | 102585 | 110391 | 111722  | 119752 | 120963  | 109590 | 103662 | 92554 | 70337  |
| 1   | 2002 | 1229555 | 155065 | 103446 | 102175 | 95976  | 99501  | 102627  | 109747 | 108061  | 99701  | 96216  | 89285 | 67755  |
| 2   | 2003 | 1198927 | 138670 | 89548  | 101046 | 92574  | 99531  | 104644  | 109225 | 109159  | 98766  | 94838  | 89542 | 71384  |
| 3   | 2004 | 1222484 | 141538 | 94596  | 100696 | 100801 | 102214 | 105728  | 111102 | 110425  | 98492  | 94840  | 90833 | 71219  |
| 4   | 2005 | 1244041 | 142311 | 94234  | 100529 | 97441  | 106833 | 108536  | 111066 | 111430  | 103273 | 103310 | 92364 | 72714  |

### sheet_name Parametresi

Excel dosyamızın içinde birden fazla çalışma sayfası (sekme) bulunması halinde, istediğimiz çalışma sayfasına erişebilmek için, **sheet_name** parametresini kullanmalıyız. 

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", sheet_name = "ortalama")
print(df.head())
```

çıktı;

|     | Yıl  | Toplam  | Ortalama      |
| --- | ---- | ------- | ------------- |
| 0   | 2001 | 1323341 | 110278.416667 |
| 1   | 2002 | 1229555 | 102462.916667 |
| 2   | 2003 | 1198927 | 99910.583333  |
| 3   | 2004 | 1222484 | 101873.666667 |
| 4   | 2005 | 1244041 | 103670.083333 |

Gördüğünüz gibi, kodumuza **sheet_name = "ortalama"** ibaresi ekleyerek, aynı excel dosyasının **ortalama** isimli çalışma sayfasındaki verileri, çalışmamıza veri çerçevesi olarak ekledik.

Birden fazla çalışma sayfasını, çalışmamıza dahil etmek (içe aktarmak) istersek, **sheet_name** parametresine bir liste girdisi vermeliyiz. Bu durumda çıktı, bir **sözlük yapısı (dict)** olacaktır.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", sheet_name = ["ortalama", "2001-2021"])
print(df)
```

çıktı;

```python
{'ortalama':      Yıl   Toplam       Ortalama
0   2001  1323341  110278.416667
1   2002  1229555  102462.916667
2   2003  1198927   99910.583333
3   2004  1222484  101873.666667
....
....
18  2019  1188524   99043.666667
19  2020  1115821   92985.083333
20  2021  1079842   89986.833333, 
'2001-2021':      Yıl   Toplam    Ocak   Şubat    Mart   Nisan   Mayıs  Haziran  Temmuz  \
0   2001  1323341  170397  103476  107912  102585  110391   111722  119752   
1   2002  1229555  155065  103446  102175   95976   99501   102627  109747   
2   2003  1198927  138670   89548  101046   92574   99531   104644  109225   
3   2004  1222484  141538   94596  100696  100801  102214   105728  111102   
....
....   
18  2019  1188524  104044   85510   96631   93013  105166    97965  112628   
19  2020  1115821   94888   83433   89503   88526   93159    99232  105970   
20  2021  1079842   80733   77535   86214   82789   88506    94266   99252   

    Ağustos   Eylül    Ekim   Kasım  Aralık  
0    120963  109590  103662   92554   70337  
1    108061   99701   96216   89285   67755  
2    109159   98766   94838   89542   71384  
3    110425   98492   94840   90833   71219  
....
....
18   109182   99981   98320   92936   93148  
19   100478   96018   93428   87540   83646  
20   100407   97334   93290   92189   87327  }
```

## İndeks değerlerini Ayarlamak

## index_col() Fonksiyonu

Veri Çerçevemiz içerisinde bulunan sütunlardan birini, indeks değeri olarak ayarlamak istersek, **index_col()** fonksiyonunu kullanabiliriz.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", sheet_name = "ortalama")
print(df.head())
```

çıktı;

|     | Yıl  | Toplam  | Ortalama      |
| --- | ---- | ------- | ------------- |
| 0   | 2001 | 1323341 | 110278.416667 |
| 1   | 2002 | 1229555 | 102462.916667 |
| 2   | 2003 | 1198927 | 99910.583333  |
| 3   | 2004 | 1222484 | 101873.666667 |
| 4   | 2005 | 1244041 | 103670.083333 |

Oluşan veri çerçevesindeki **Yıl** sütununu indeks olarak ayarlayalım.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", index_col=0, sheet_name = "ortalama")
print(df.head())
```

|      | Toplam  | Ortalama      |
| ---- | ------- | ------------- |
| Yıl  |         |               |
| 2001 | 1323341 | 110278.416667 |
| 2002 | 1229555 | 102462.916667 |
| 2003 | 1198927 | 99910.583333  |
| 2004 | 1222484 | 101873.666667 |
| 2005 | 1244041 | 103670.083333 |

## Sütunları Atla

## usecols Parametresi

Bir Excel çalışma sayfasını, Pandas Veri Çerçevesine (DataFrame'e) dönüştürürken, bazı sütunları atlamamız / göz ardı etmemiz gerekebilir, bunu **usecols** parametresi kullanarak yapabiliriz. Bu parametre, tamsayı (int), metin (str), list-like veya callable (varsayılan None) değerlerini alır. Sütun adlarının veya konumlarının listesini belirtmek için, bir dize (string) listesi veya bir  tamsayı (int) listesi kullanmalıyız.

Aylara Göre Doğum Sayıları tablosunu yukarıda görmüştük. Bu tabloda 14 sütun bulunmaktadır. Sadece istediğimiz aylara ait sütun bilgilerini görüntülemek istersek **usecols** parametresine ya **ay isimlerini** ya da **ayın sütun indis değerini** yazmamız gerekir. Her iki kullanımı da görelim.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", usecols=["Ocak", "Haziran", "Ağustos"])
print(df.head())
```

çıktı;

|     | Ocak   | Haziran | Ağustos |
| --- | ------ | ------- | ------- |
| 0   | 170397 | 111722  | 120963  |
| 1   | 155065 | 102627  | 108061  |
| 2   | 138670 | 104644  | 109159  |
| 3   | 141538 | 105728  | 110425  |
| 4   | 142311 | 108536  | 111430  |

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", usecols=[2,7,9])
print(df.head())
```

çıktı;

|     | Ocak   | Haziran | Ağustos |
| --- | ------ | ------- | ------- |
| 0   | 170397 | 111722  | 120963  |
| 1   | 155065 | 102627  | 108061  |
| 2   | 138670 | 104644  | 109159  |
| 3   | 141538 | 105728  | 110425  |
| 4   | 142311 | 108536  | 111430  |

**usecols** parametresine, <u>sütun isimlerini yazarken</u>, sütun isimleri metinsel (string) ifade olduğu için **çift tırnak işareti "** kullandığımıza, <u>indis değeri yazarken</u> , indis değerleri tamsayı (int) olduğu için, tırnak işareti kullanmadığımıza dikkat edin.

Ayrıca, **usecols** parametresini, sütun aralığı seçerek te kullanabiliriz.  Veri çerçevemizin sütunlarını, Excel programının sütun isimleri gibi (A, B, C,... şeklinde) düşünerek aralık seçebiliriz. Aşağıdaki örnek ne demek istediğimi daha net anlatacaktır.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx", usecols = "C:H")
print(df.head())
```

çıktı;

|     | Ocak   | Şubat  | Mart   | Nisan  | Mayıs  | Haziran |
| --- | ------ | ------ | ------ | ------ | ------ | ------- |
| 0   | 170397 | 103476 | 107912 | 102585 | 110391 | 111722  |
| 1   | 155065 | 103446 | 102175 | 95976  | 99501  | 102627  |
| 2   | 138670 | 89548  | 101046 | 92574  | 99531  | 104644  |
| 3   | 141538 | 94596  | 100696 | 100801 | 102214 | 105728  |
| 4   | 142311 | 94234  | 100529 | 97441  | 106833 | 108536  |

Oluşturduğumuz Veri Çerçevemizdeki Yıl Sütunu **A**'ya, **Toplam** sütunu **B**'ye, **Ocak** Sütunu da **C**'ye denk geldiği için, çıktımız **Ocak** Ayından başlayıp H sütununa denk gelen Haziran ayına kadar aralığı alarak çıktı olarak bize sundu.

## Satırları Atla

## skiprows Parametresi

Bir Excel çalışma sayfasını, Pandas Veri Çerçevesine (DataFrame'e) dönüştürürken, bazı satırları atlamamız / göz ardı etmemiz gerekebilir, bunu **skiprows** parametresi kullanarak yapabiliriz. Bu parametre olarak, list-like, tamsayı (int) veya callable (isteğe bağlı) değerlerini alır. Bu parametre ile  ilk birkaç satırı, seçilen satırı ve satır aralığını atlayabiliriz.  

```python
basliksiz = pd.read_excel("SatırAtla.ods")
print(basliksiz.head(10))
```

çıktı;

|     | Unnamed: 0               | Unnamed: 1 | Unnamed: 2 | Unnamed: 3   |
| --- | ------------------------ | ---------- | ---------- | ------------ |
| 0   | mhg                      | NaN        | NaN        | NaN          |
| 1   | NaN                      | NaN        | 654        | NaN          |
| 2   | NaN                      | NaN        | NaN        | NaN          |
| 3   | Film_Adı                 | Yıl        | Puan       | Oylayan_Kişi |
| 4   | The Shawshank Redemption | 1994       | 9,2        | 1071904      |
| 5   | The Godfather            | 1972       | 9,2        | 751381       |
| 6   | The Godfather: Part II   | 1974       | 9          | 488889       |
| 7   | Pulp Fiction             | 1994       | 8,9        | 830504       |
| 8   | The Dark Knight          | 2008       | 8,9        | 1045186      |
| 9   | 12 Angry Men             | 1957       | 8,9        | 264112       |

Yukarıdaki tabloda, ilk 4 satırı (2. indis dahil) atlayıp, 5. satırı (3. indisi) başlık olarak kabul eden bir veri çerçevesi oluşturmak istersek aşağıdaki kodu uygulamamız gerekir.

```python
basliksiz = pd.read_excel("SatırAtla.xlsx", skiprows=4)
print(basliksiz.head(10))
```

|     | Film_Adı                                       | Yıl  | Puan | Oylayan_Kişi |
| --- | ---------------------------------------------- | ---- | ---- | ------------ |
| 0   | The Shawshank Redemption                       | 1994 | 9,2  | 1071904      |
| 1   | The Godfather                                  | 1972 | 9,2  | 751381       |
| 2   | The Godfather: Part II                         | 1974 | 9    | 488889       |
| 3   | Pulp Fiction                                   | 1994 | 8,9  | 830504       |
| 4   | The Dark Knight                                | 2008 | 8,9  | 1045186      |
| 5   | 12 Angry Men                                   | 1957 | 8,9  | 264112       |
| 6   | Schindler's List                               | 1993 | 8,9  | 545703       |
| 7   | The Lord of the Rings: The Return of the King  | 2003 | 8,8  | 758388       |
| 8   | Fight Club                                     | 1999 | 8,8  | 814389       |
| 9   | Star Wars: Episode V - The Empire Strikes Back | 1980 | 8,8  | 519895       |

Atlamak / gözardı etmek istediğimiz satırları tek tek te belirtebiliriz.

```python
basliksiz = pd.read_excel("SatırAtla.xlsx", skiprows=[0,1,2,3,5,8,10,12])
basliksiz.head(10)
```

çıktı;

|     | Film_Adı                                          | Yıl  | Puan | Oylayan_Kişi |
| --- | ------------------------------------------------- | ---- | ---- | ------------ |
| 0   | The Godfather                                     | 1972 | 9,2  | 751381       |
| 1   | The Godfather: Part II                            | 1974 | 9    | 488889       |
| 2   | The Dark Knight                                   | 2008 | 8,9  | 1045186      |
| 3   | Schindler's List                                  | 1993 | 8,9  | 545703       |
| 4   | Fight Club                                        | 1999 | 8,8  | 814389       |
| 5   | Star Wars: Episode V - The Empire Strikes Back    | 1980 | 8,8  | 519895       |
| 6   | The Lord of the Rings: The Fellowship of the R... | 2001 | 8,8  | 784999       |
| 7   | One Flew Over the Cuckoo's Nest                   | 1975 | 8,7  | 447005       |
| 8   | Goodfellas                                        | 1990 | 8,7  | 465445       |
| 9   | Seven Samurai                                     | 1954 | 8,7  | 161969       |