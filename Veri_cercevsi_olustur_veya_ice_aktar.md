# Veri Çerçevesi Oluştur ya da İçe Aktar

## import Fonksiyonu

Pandas Kütüphanesini içe aktarıp kodlamada kolay ve hızlı olması adına bu kütüphaneye **pd** adını atayalım;

```python
import pandas as pd
```

## DataFrame() Fonksiyonu

Veri Çerçevesi (Data Frame) Oluşturmak için **DataFrame()** fonksiyonunu kullanıyoruz.  Veri Çerçevesine dönüştürmek istediğimiz veriyi, parantez içine, parametre olarak yazmalıyız.

```python
pd.DataFrame(dosya veya veri)
```

örneğin bir sözlük (dict) yapısı oluşturup bu yapıyı **Veri Çerçevesi**ne (**Data Frame**'e) dönüştürelim;

```python
sozluk = {"isim" : ["Mustafa", "Halil", "Burak", "Emre", "Ersin", "Sertaç", "Furkan","Murat","Ahmet","Abdülkadir"],
                    "yaş" : [25, 38, 41, 23, 37, 52, 30, 23, 40, 38],
                   "iş-meslek" : ["mühendis", "programcı", "akademisyen", "yönetici","amir","mühendis", "yönetici","müdür","veteriner","yönetici"]}
veri = pd.DataFrame(sozluk)
```

Oluşturduğumuz Veri Çerçevesinin içeriğini görelim;

```python
print(veri)
```

çıktı;

|     | isim       | yaş | iş-meslek   |
| --- | ---------- | --- | ----------- |
| 0   | Mustafa    | 25  | mühendis    |
| 1   | Halil      | 38  | programcı   |
| 2   | Burak      | 41  | akademisyen |
| 3   | Emre       | 23  | yönetici    |
| 4   | Ersin      | 37  | amir        |
| 5   | Sertaç     | 52  | mühendis    |
| 6   | Furkan     | 30  | yönetici    |
| 7   | Murat      | 23  | müdür       |
| 8   | Ahmet      | 40  | veteriner   |
| 9   | Abdülkadir | 38  | yönetici    |

Gördüğünüz gibi verimiz, **DataFrame()** fonksiyonu ile, SQL ya da Excel tablosuna benzer şekilde satır ve sütunlardan oluşan yapıya dönüştürüldü. artık bu yapıyı yönetmek ve analiz etmek oldukça kolaylaştı.

## head() Fonksiyonu

Oluşturduğumuz ya da çalışmamıza dahil ettiğimiz (içe aktardığımız) Veri Çerçevelerinin ilk satırlarını görüp, içerik hakkında bilgi edinmek istersek **head()** fonksiyonunu kullanabiliriz. **Head** kelimesi Türkçede **Baş, Kafa** anlamına gelmektedir.

```python
print(veri.head())
```

çıktı;

|     | isim    | yaş | iş-meslek   |
| --- | ------- | --- | ----------- |
| 0   | Mustafa | 25  | mühendis    |
| 1   | Halil   | 38  | programcı   |
| 2   | Burak   | 41  | akademisyen |
| 3   | Emre    | 23  | yönetici    |
| 4   | Ersin   | 37  | amir        |

**head()** fonksiyonunda parantez içine parametre olarak bir değer yazmazsak, veri çerçevesinin **ilk 5** değeri görüntülenir. Değer belirtirsek belirttiğimiz değer kadar veri görüntülenir.

```python
print(veri.head(3))
```

|     | isim    | yaş | iş-meslek   |
| --- | ------- | --- | ----------- |
| 0   | Mustafa | 25  | mühendis    |
| 1   | Halil   | 38  | programcı   |
| 2   | Burak   | 41  | akademisyen |

İndex değerinin 2'de bitmesi sizi şaşırtmasın, pekçok programlama dilindi olduğu gibi Python programlama dilinde de, sayma sayıları sıfırdan başlar. Zaten tabloyu incelerseniz, tabloda 3 kullanıcıya ait veri olduğunu görürsünüz.

## tail() Fonksiyonu

**head()** fonksiyonuna oldukça benzer bir fonksiyondur. Oluşturduğumuz ya da çalışmamıza dahil ettiğimiz Veri Çerçevelerinin **son satırlarını** görüp içerik hakkında bilgi edinmek istersek **tail()** fonksiyonunu kullanabiliriz. **Tail** kelimesi Türkçede, **kuyruk, son kısım** anlamına gelmektedir.

```python
print(veri.tail())
```

|     | isim       | yaş | iş-meslek |
| --- | ---------- | --- | --------- |
| 5   | Sertaç     | 52  | mühendis  |
| 6   | Furkan     | 30  | yönetici  |
| 7   | Murat      | 23  | müdür     |
| 8   | Ahmet      | 40  | veteriner |
| 9   | Abdülkadir | 38  | yönetici  |

**tail()** fonksiyonunu içine parametre olarak bir değer yazmazsak, veri çerçevesinin **son 5 değerini** görüntüler. Değer belirtirsek belirttiğimiz değer kadar veri görüntüler.

```python
print(tail(7))
```

|     | isim       | yaş | iş-meslek |
| --- | ---------- | --- | --------- |
| 3   | Emre       | 23  | yönetici  |
| 4   | Ersin      | 37  | amir      |
| 5   | Sertaç     | 52  | mühendis  |
| 6   | Furkan     | 30  | yönetici  |
| 7   | Murat      | 23  | müdür     |
| 8   | Ahmet      | 40  | veteriner |
| 9   | Abdülkadir | 38  | yönetici  |

## columns Fonksiyonu

**columns** fonksiyonu, oluşturulan ya da içe aktarılan Veri Çerçevelerinin başlık satırını çıktı olarak verir / görüntüler. **columns** fonksiyonunu kullanırken sonunda <u>parantez işaretleri kullanmadığımıza</u> dikkat edin.

Sütun isimlerini değiştirmek ya da veri çerçevesine filtreleme işlemi uygulamak istediğimiz zaman, bu fonksiyon çok işimize yarar.

```python
print(veri.columns)
```

çıktı;

```python
Index(['isim', 'yaş', 'iş-meslek'], dtype='object')
```

## info() Fonksiyonu

**info()** fonksiyonu, Veri Çerçevesinin satır ve sütun sayısı,  başlık tipleri (sayı, metin, ...vb) ve doluluk oranı (boş olmayan hücre sayısı) hakkında bilgi görüntüler. 

```python
print(veri.info())
```

çıktı;

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 10 entries, 0 to 9
Data columns (total 3 columns):
 #   Column     Non-Null Count  Dtype 
---  ------     --------------  ----- 
 0   isim       10 non-null     object
 1   yaş        10 non-null     int64 
 2   iş-meslek  10 non-null     object
dtypes: int64(1), object(2)
memory usage: 368.0+ bytes
```

<u>Çıktıyı incelersek;</u>

**class 'pandas.core.frame.DataFrame** : **veri**'nin Pandas sınıfına ait bir DataFrame yapısı olduğunu,

**RangeIndex: 10 entries, 0 to 9** : Veri Çerçevesinin 0 ile 9 arasında, toplam 10 satırlık yapı olduğunu,

**Data columns (total 3 columns)** : Veri Çerçevesinin 3 sütundan oluştuğunu,

 **Column** : Sütun isimlerini,

**Non-Null Count** :  Boş olmayan veri sayısını,

**Dtype** : Veri biçimini tanımlar.

**int34** ya da int64 **ibaresi**, **tamsayı (integer)** olduğunu, **object** ibaresi, verinin **metin (string)** ifadesi olduğunu,

**dtypes: int64(1), object(2)** : Veri Çerçevesinin 1 adet tamsayı (**int64(1)**), 2 adet metinsel (string / **object(2)**) başlık/sütun içerdiğini temsil eder. 

## dtypes Fonksiyonu

**dtypes** fonksiyonu, veri çerçevesinin başlık tiplerini görüntüler. **dtypes** fonksiyonunu kullanırken sonunda <u>parantez işaretleri kullanmadığımıza</u> dikkat edin.

```python
print(veri.dtypes)
```

çıktı;

```python
isim         object
yaş           int64
iş-meslek    object
dtype: object
```

## describe() Fonksiyonu

**describe()** fonksiyonu, sayısal veri barındıran sütunlar hakkında detaylı matematiksel bilgiler verir.

```python
veri.describe()
```

çıktı;

|       | yaş       |
| ----- | --------- |
| count | 10.000000 |
| mean  | 34.700000 |
| std   | 9.333929  |
| min   | 23.000000 |
| 25%   | 26.250000 |
| 50%   | 37.500000 |
| 75%   | 39.500000 |
| max   | 52.000000 |

<u>Çıktıyı incelersek;</u>

**count :** yaş isimli sütunda kaç adet veri olduğunu,

**mean :** yaş isimli sütudaki verilerin ortalamasını,

**std :** yaş isimli sütudaki verilerin standart sapmasını,

**min:** yaş isimli sütudaki verilerin en küçük değerini

**%25 :** yaş isimli sütundaki verilerin medyanın alt çeyreğini (dörttebirliğini),

**%50 :** yaş isimli sütundaki verilerin Ortanca medyanını,

**%75 :** yaş isimli sütundaki verilerin medyanın üst çeyreğini (dörttebirliğini),

**max :** yaş isimli sütudaki verilerin en büyük değerini, tanımlar

## CSV Dosyasını İçe Aktarmak

## read_csv() Fonksiyonu

csv uzantılı dosyaların içeriğini çalışmalarımıza eklemek istersek kullanabileceğimiz fonksiyon, **read_csv()** fonksiyonudur.

örneğin **nba.csv** isimli dosyasınının içeriğini çalışmamıza aktaralım;

```python
nba_csv = pd.read_csv("nba.csv")
print(nba_csv)
```

çıktı;

|     | Name          | Team           | Number | Position | Age  | Height | Weight | College           | Salary    |
| --- | ------------- | -------------- | ------ | -------- | ---- | ------ | ------ | ----------------- | --------- |
| 0   | Avery Bradley | Boston Celtics | 0.0    | PG       | 25.0 | 6-2    | 180.0  | Texas             | 7730337.0 |
| 1   | Jae Crowder   | Boston Celtics | 99.0   | SF       | 25.0 | 6-6    | 235.0  | Marquette         | 6796117.0 |
| 2   | John Holland  | Boston Celtics | 30.0   | SG       | 27.0 | 6-5    | 205.0  | Boston University | NaN       |
| 3   | R.J. Hunter   | Boston Celtics | 28.0   | SG       | 22.0 | 6-5    | 185.0  | Georgia State     | 1148640.0 |
| 4   | Jonas Jerebko | Boston Celtics | 8.0    | PF       | 29.0 | 6-10   | 231.0  | NaN               | 5000000.0 |
| ... | ...           | ...            | ...    | ...      | ...  | ...    | ...    | ...               | ...       |
| 453 | Shelvin Mack  | Utah Jazz      | 8.0    | PG       | 26.0 | 6-3    | 203.0  | Butler            | 2433333.0 |
| 454 | Raul Neto     | Utah Jazz      | 25.0   | PG       | 24.0 | 6-1    | 179.0  | NaN               | 900000.0  |
| 455 | Tibor Pleiss  | Utah Jazz      | 21.0   | C        | 26.0 | 7-3    | 256.0  | NaN               | 2900000.0 |
| 456 | Jeff Withey   | Utah Jazz      | 24.0   | C        | 26.0 | 7-0    | 231.0  | Kansas            | 947276.0  |
| 457 | NaN           | NaN            | NaN    | NaN      | NaN  | NaN    | NaN    | NaN               | NaN       |

458 rows × 9 columns

## read_table() fonksiyonu

**read_table()** fonksiyonu ile **csv** uzantılı dosyalar içe aktarıldığında, dosyanın her satırı, tablonun bir sütununa yazılır. Yani tabloda 2 sütun oluşturulur birinde index bilgisi, ikinci sütunda ise **csv** dosyasının satırlarındaki bilgiler bulunur.

```python
nba = pd.read_table("nba.csv")
print(nba)
```

çıktı;

|     | Name,Team,Number,Position,Age,Height,Weight,College,Salary |
| --- | ---------------------------------------------------------- |
| 0   | Avery Bradley,Boston Celtics,0.0,PG,25.0,6-2,1...          |
| 1   | Jae Crowder,Boston Celtics,99.0,SF,25.0,6-6,23...          |
| 2   | John Holland,Boston Celtics,30.0,SG,27.0,6-5,2...          |
| 3   | R.J. Hunter,Boston Celtics,28.0,SG,22.0,6-5,18...          |
| 4   | Jonas Jerebko,Boston Celtics,8.0,PF,29.0,6-10,...          |
| ... | ...                                                        |
| 453 | Shelvin Mack,Utah Jazz,8.0,PG,26.0,6-3,203.0,B...          |
| 454 | Raul Neto,Utah Jazz,25.0,PG,24.0,6-1,179.0,,90...          |
| 455 | Tibor Pleiss,Utah Jazz,21.0,C,26.0,7-3,256.0,,...          |
| 456 | Jeff Withey,Utah Jazz,24.0,C,26.0,7-0,231.0,Ka...          |
| 457 | ,,,,,,,,                                                   |

### delimiter parametresi

CSV dosyaları **read_table()** fonksiyonu ile içe aktarılırken **delimiter = ","** parametresi  eklenirse, dosya içeriği, **read_csv** fonksiyonu ile aynı çıktıyı verir. Satırlardaki veriler, **","** virgül kısımlarından ayrılarak, ayrı sütunlara yazılır.

```python
nba = pd.read_table("nba.csv", delimiter=",")
print(nba)
```

çıktı;

|     | Name          | Team           | Number | Position | Age  | Height | Weight | College           | Salary    |
| --- | ------------- | -------------- | ------ | -------- | ---- | ------ | ------ | ----------------- | --------- |
| 0   | Avery Bradley | Boston Celtics | 0.0    | PG       | 25.0 | 6-2    | 180.0  | Texas             | 7730337.0 |
| 1   | Jae Crowder   | Boston Celtics | 99.0   | SF       | 25.0 | 6-6    | 235.0  | Marquette         | 6796117.0 |
| 2   | John Holland  | Boston Celtics | 30.0   | SG       | 27.0 | 6-5    | 205.0  | Boston University | NaN       |
| 3   | R.J. Hunter   | Boston Celtics | 28.0   | SG       | 22.0 | 6-5    | 185.0  | Georgia State     | 1148640.0 |
| 4   | Jonas Jerebko | Boston Celtics | 8.0    | PF       | 29.0 | 6-10   | 231.0  | NaN               | 5000000.0 |
| ... | ...           | ...            | ...    | ...      | ...  | ...    | ...    | ...               | ...       |
| 453 | Shelvin Mack  | Utah Jazz      | 8.0    | PG       | 26.0 | 6-3    | 203.0  | Butler            | 2433333.0 |
| 454 | Raul Neto     | Utah Jazz      | 25.0   | PG       | 24.0 | 6-1    | 179.0  | NaN               | 900000.0  |
| 455 | Tibor Pleiss  | Utah Jazz      | 21.0   | C        | 26.0 | 7-3    | 256.0  | NaN               | 2900000.0 |
| 456 | Jeff Withey   | Utah Jazz      | 24.0   | C        | 26.0 | 7-0    | 231.0  | Kansas            | 947276.0  |
| 457 | NaN           | NaN            | NaN    | NaN      | NaN  | NaN    | NaN    | NaN               | NaN       |

458 rows × 9 columns

## Excel dosyasını içe aktarmak

## read_excel() fonksiyonu

**Excel** ve **Calc** dosyalarının içeriğini çalışmamıza dahil etmek için **read_excel()** fonksiyonunu kullanmalıyız.

<u>Bu fonksiyon;</u>

* **xls, xlsx, xlsm, xlsb, odf, ods** ve odt **uzantılı** dosyaları destekler

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

İlk olarak **OSD** uzantılı bir dosyayı çalışmamıza dahil edip içeriine bakalım.

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

## JSON dosyasını içe aktarmak

## read_json() Fonksiyonu

**read_json()** fonksiyonu ile **json** uzantılı dosyaları çalışmalarınıza dahil edebilirsiniz.

```python
veri_json = pd.read_json("json_verisi.json")
print(veri_json)
```

çıktı;

|     | Duration | Pulse | Maxpulse | Calories |
| --- | -------- | ----- | -------- | -------- |
| 0   | 60       | 110   | 130      | 409      |
| 1   | 60       | 117   | 145      | 479      |
| 2   | 60       | 103   | 135      | 340      |
| 3   | 45       | 109   | 175      | 282      |
| 4   | 45       | 117   | 148      | 406      |
| 5   | 60       | 102   | 127      | 300      |

Yerel diskinizde bulunan json dosyası dışında, <u>bir websitesindeki **json** dosyasını</u>çalışmanıza dahil etmek isterseniz yine **read_json()** fonksiyonunu kullanabilirsiniz.

```python
url = "https://api.exchangerate-api.com/v4/latest/USD"
df = pd.read_json(url)
print(df)
```

çıktı;

|     | provider                         | WARNING_UPGRADE_TO_V6                      | terms                                  | base | date       | time_last_updated | rates  |
| --- | -------------------------------- | ------------------------------------------ | -------------------------------------- | ---- | ---------- | ----------------- | ------ |
| AED | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 3.67   |
| AFN | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 87.52  |
| ALL | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 114.84 |
| AMD | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 410.21 |
| ANG | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 1.79   |
| ... | ...                              | ...                                        | ...                                    | ...  | ...        | ...               | ...    |
| XPF | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 117.35 |
| YER | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 249.54 |
| ZAR | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 16.85  |
| ZMW | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 16.40  |
| ZWL | https://www.exchangerate-api.com | https://www.exchangerate-api.com/docs/free | https://www.exchangerate-api.com/terms | USD  | 2022-07-09 | 1657324802        | 376.59 |

161 rows × 7 columns

## URL ya da HTML dosyası içe aktarmak

## read_html() Fonksiyonu

**read_html()** fonksiyonu ile web sitelerinde bulunan tabloları ya da htm/html uzantılı dosyalarınızdaki tabloları, çalışmalarınıza dahil edebilirsiniz. Öncelikle veri almak istediğimiz sayfanın içerisinde kaç adet tablo olduğunu bulalım.

```python
url = pd.read_html("https://tr.wikipedia.org/wiki/Van")
print(f"Sayfada bulunan toplam tablo sayısı: {len(url)}")
```

çıktı;

```python
Sayfada bulunan toplam tablo sayısı: 10
```

Hangi tabloyu kullanmak (içe aktarmak) istiyorsak öncelikle o tabloyu, tam olarak belirtmemiz/tanımlamamız gerekiyor. Bunu da **read_html()** fonksiyonunun **match (eşle)** parametresi ile yapmamız gerekir. Benim kullanmak istediğim tablonun içerisinde **Van il nüfus bilgileri** ibaresi bulunduğu için ben bu kelime grubunu koduma dahil ediyorum.

```python
url = pd.read_html("https://tr.wikipedia.org/wiki/Van", match="Van il nüfus bilgileri")
len(url)
```

çıktı;

```python
1
```

Bu demek oluyor ki, sayfa içeriğinde, **Van il nüfus bilgileri** ibaresi bulunan <u>1 adet eşleşmiş tablo</u> var, artık **url** değişkeni sayfadaki tek tabloyu temsil ediyor ve bu tabloya erişmek için ilk indis olan **0 sıfır**'ı kullanmamız gerekir.

```python
print(url[0])
ya da 
iklim = url[0]
print(iklim)
```

çıktı;

|     | Van il nüfus bilgileri |            |          |          |                                     |
| --- | ---------------------- | ---------- | -------- | -------- | ----------------------------------- |
|     | **Yıl**                | **Toplam** | **Sıra** | **Fark** | **Şehir - Kır**                     |
| 0   | 1965[11]               | 266.840    | 48       | NaN      | %23 60.686206.154 %77               |
| 1   | 1970[12]               | 325.763    | 43       | %22      | %27 88.227237.536 %73               |
| 2   | 1975[13]               | 386.314    | 42       | %19      | %30 115.830270.484 %70              |
| 3   | 1980[14]               | 468.646    | 39       | %21      | %33 156.852311.794 %67              |
| 4   | 1985[15]               | 547.216    | 35       | %17      | %35 189.269357.947 %65              |
| 5   | 1990[16]               | 637.433    | 32       | %16      | %41 258.967378.466 %59              |
| 6   | 2000[17]               | 877.524    | 23       | %38      | %51 446.976430.548 %49              |
| 7   | 2007[18]               | 979.671    | 19       | %12      | %52 511.678467.993 %48              |
| 8   | 2008[19]               | 1.004.369  | 19       | %3       | %51 514.481489.888 %49              |
| 9   | 2009[20]               | 1.022.310  | 19       | %2       | %52 527.525494.785 %48              |
| 10  | 2010[21]               | 1.035.418  | 19       | %1       | %52 539.619495.799 %48              |
| 11  | 2011[22]               | 1.022.532  | 19       | -%1      | %52 526.725495.807 %48              |
| 12  | 2012[23]               | 1.051.975  | 19       | %3       | %52 548.717503.258 %48              |
| 13  | 2013[24]               | 1.070.113  | 19       | %2       | Şehir ve kır ayrımı kaldırılmıştır. |
| 14  | 2014[25]               | 1.085.542  | 19       | %1       | Şehir ve kır ayrımı kaldırılmıştır. |
| 15  | 2015[26]               | 1.096.397  | 19       | %1       | Şehir ve kır ayrımı kaldırılmıştır. |
| 16  | 2016[26]               | 1.100.190  | 19       | %0       | Şehir ve kır ayrımı kaldırılmıştır. |
| 17  | 2017[26]               | 1.106.891  | 19       | %1       | Şehir ve kır ayrımı kaldırılmıştır. |
| 18  | 2018[26]               | 1.123.784  | 19       | %2       | Şehir ve kır ayrımı kaldırılmıştır. |
| 19  | 2019[26]               | 1.136.757  | 19       | %1       | Şehir ve kır ayrımı kaldırılmıştır. |
| 20  | 2020[26]               | 1.149.342  | 19       | %1       | Şehir ve kır ayrımı kaldırılmıştır. |
| 21  | 2021[26]               | 1.141.015  | 19       | -%1      | NaN                                 |

Pandas, tabloda okumayı kolaylaştırır ve ayrıca birden çok satıra yayılan (birleştirilmiş hücrelerdeki verileri) sütunu işler, her hücreye aynı değeri kopyalar.

## Panodan İçe Aktarmak

## read_clipboard() Fonksiyonu

**read_clipboard()** fonksiyonu ile panoya kopyaladığınız veriyi (örneğin bir Excel tablosunu) Veri Çerçevesine dönüştürebilirsiniz.

```python
pano = pd.read_clipboard()
print(pano.head())
```

çıktı;

|     | İlçe       | 2020    | 2021    | Fark    | Nüfus art. % | Mah. say. | Alanı km2 | Yoğunluk |
| --- | ---------- | ------- | ------- | ------- | ------------ | --------- | --------- | -------- |
| 0   | Adalar     | 16.033  | 16.372  | 339.000 | 2.11         | 5         | 11        | NaN      |
| 1   | Arnavutköy | 296.709 | 312.023 | 15.314  | 5.16         | 38        | 453       | NaN      |
| 2   | Ataşehir   | 422.594 | 427.217 | 4.623   | 1.09         | 17        | 25        | NaN      |
| 3   | Avcılar    | 436.897 | 457.981 | 21.084  | 4.82         | 10        | 50        | NaN      |
| 4   | Bağcılar   | 737.206 | 744.351 | 7.145   | 0.96         | 22        | 23        | NaN      |