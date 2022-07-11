# Veri Çerçevesi (Data Frame)

Bu bölümde sıfırdan **Veri Çerçevesi** (**Data Frame**) oluşturmayı ya da harici kaynaktan verileri okuyarak veri çerçevesine dönüştürmeyi öğreneceğiz.

## import Fonksiyonu

Öncelikle **Pandas** Kütüphanesini çalışmamıza dahil edip (içe aktarıp), kodlama esnasında kolay sağlaması ve hızlı olması adına bu kütüphaneye **pd** adını atayalım;

```python
import pandas as pd
```

## DataFrame() Fonksiyonu

Veri Çerçevesi (Data Frame) Oluşturmak/Dönüştürmek için **DataFrame()** fonksiyonunu kullanıyoruz.  Veri Çerçevesine dönüştürmek istediğimiz veriyi, parantez içine, parametre olarak yazmalıyız.

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

# Veri Çerçevesi Temel Fonksiyonları

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

**head()** fonksiyonunda parantez içine parametre olarak bir değer yazmazsak, veri çerçevesinin **ilk 5 değeri** görüntülenir. Değer belirtirsek belirttiğimiz değer kadar veri görüntülenir.

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

## len() Fonksiyonu

**len()** foknsiyonu, Veri Çerçevesinin kaç satırdan oluştuğunu bildirir.

```python
print(len(veri))
```

çıktı;

```python
10
```

Çıktıdan anladığımız kadarıyla, **veri** isimli veri çerçevesi, 10 satırlık bir yapıdan oluşuyor.

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
print(veri.describe())
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

## shape Metodu

Veri Çerçevesinin yapısını yani satır ve sütun bilgisini öğrenmek için shape metodunu kullanabiliriz.

```python
print(veri.shape)
```

çıktı;

```python
(10,3)
```

Çıktıdan anladığımıza göre veri isimli veri çerçevesi, 10 satır ve 3 sütundan oluşan bir yapıdır.

## iloc Metodu

Veri Çerçevesindeki istenilen satırı görüntülemek için **iloc** metodu kullanılır. **iloc** kelimesini unutmamak için **İndex Location** yani, **Konum İndeksi/numarası** gibi düşünebilir, kafanıza kodlayabilirsiniz.

```python
print(veri.iloc[5])
```

çıktı;

```python
isim           Sertaç
yaş                52
iş-meslek    mühendis
Name: 5, dtype: object
```

## loc Metodu

**iloc** metoduna benzer bir metottur ancak **loc** metodunda, görüntülemek istediğimiz satırın indeks ismi yazmalıyız. Elimizde aşağıdaki gibi bir veri çerçevesi olduğunu düşünürsek;

|               | Team           | Number | Position | Age  | Height | Weight | College           | Salary    |
| ------------- | -------------- | ------ | -------- | ---- | ------ | ------ | ----------------- | --------- |
| Name          |                |        |          |      |        |        |                   |           |
| ---           | ---            | ---    | ---      | ---  | ---    | ---    | ---               | ---       |
| Avery Bradley | Boston Celtics | 0.0    | PG       | 25.0 | 6-2    | 180.0  | Texas             | 7730337.0 |
| Jae Crowder   | Boston Celtics | 99.0   | SF       | 25.0 | 6-6    | 235.0  | Marquette         | 6796117.0 |
| John Holland  | Boston Celtics | 30.0   | SG       | 27.0 | 6-5    | 205.0  | Boston University | NaN       |
| R.J. Hunter   | Boston Celtics | 28.0   | SG       | 22.0 | 6-5    | 185.0  | Georgia State     | 1148640.0 |
| Jonas Jerebko | Boston Celtics | 8.0    | PF       | 29.0 | 6-10   | 231.0  | NaN               | 5000000.0 |

**John Holland** isimli satır verisine ulaşmak için **loc** metoduna **John Holland** metinsel (string) ibaresini eklemeliyiz.

```python
print(nba_csv.loc["John Holland"])
```

çıktı;

```python
Team           Boston Celtics
Number                   30.0
Position                   SG
Age                      27.0
Height                    6-5
Weight                  205.0
College     Boston University
Salary                    NaN
Name: John Holland, dtype: object
```

# Harici Dosyaları İçe Aktar

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

## index_col Parametresi

Harici kaynaktan veri alarak oluşturulan veri çerçevesinin indeks değerini, istediğimiz sütuna eşitleyebiliriz. Bunu yapmak için **index_col** parametresini kullanmalıyız. Örneğin NBA oyuncularının verileri barındıran CSV uzantılı dosyanın Name Sütununu, veri çerçevemizin indeks sütunu haline getirip veri çerçevemize göz atalım.

```python
nba_csv = pd.read_csv("nba.csv", index_col="Name")
nba_csv.head()
```

çıktı;

|               | Team           | Number | Position | Age  | Height | Weight | College           | Salary    |
| ------------- | -------------- | ------ | -------- | ---- | ------ | ------ | ----------------- | --------- |
| Name          |                |        |          |      |        |        |                   |           |
| Avery Bradley | Boston Celtics | 0.0    | PG       | 25.0 | 6-2    | 180.0  | Texas             | 7730337.0 |
| Jae Crowder   | Boston Celtics | 99.0   | SF       | 25.0 | 6-6    | 235.0  | Marquette         | 6796117.0 |
| John Holland  | Boston Celtics | 30.0   | SG       | 27.0 | 6-5    | 205.0  | Boston University | NaN       |
| R.J. Hunter   | Boston Celtics | 28.0   | SG       | 22.0 | 6-5    | 185.0  | Georgia State     | 1148640.0 |
| Jonas Jerebko | Boston Celtics | 8.0    | PF       | 29.0 | 6-10   | 231.0  | NaN               | 5000000.0 |

Gördüğünüz gibi artık indeks bilgileri, Oyuncu isimlerine dönüşmüş oldu.

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

**Excel** ve **Calc (Libre Ofis)** programlarıyla oluşturulmuş tabloları çalışmamıza dahil etmek için **read_excel()** fonksiyonunu kullanmalıyız.

<u>Bu fonksiyon;</u>

* **xls, xlsx, xlsm, xlsb, odf, ods** ve odt **uzantılı** dosyaları destekler

* Yerel bir dosya sisteminde veya bir URL'den depolanan excel, calc dosyalarını yükleyebilir.

* Bir tek çalışma sayfasından veya bir sayfa listesinden içerik okumayı da destekler.

* İki sayfa okunurken, **DataFrame**'i bir Sözluk yapısına (Dict) dönüşür.

```python
pd.read_excel(dosya_adi)
```

Bu fonksiyon kullanıldığında, varsayılan olarak, excel dosyasının ilk çalışma sayfası yüklenir ve ilk satır bir Veri Çerçevesi (DataFrame) başlığı (sütun adı) olarak ayarlanır.

```python
df = pd.read_excel("AyaGöreDoğumlar.xlsx")
df.head()
```

çıktı;

|     | Yıl  | Toplam  | Ocak   | Şubat  | Mart   | Nisan  | Mayıs  | Haziran | Temmuz | Ağustos | Eylül  | Ekim   | Kasım | Aralık |
| --- | ---- | ------- | ------ | ------ | ------ | ------ | ------ | ------- | ------ | ------- | ------ | ------ | ----- | ------ |
| 0   | 2001 | 1323341 | 170397 | 103476 | 107912 | 102585 | 110391 | 111722  | 119752 | 120963  | 109590 | 103662 | 92554 | 70337  |
| 1   | 2002 | 1229555 | 155065 | 103446 | 102175 | 95976  | 99501  | 102627  | 109747 | 108061  | 99701  | 96216  | 89285 | 67755  |
| 2   | 2003 | 1198927 | 138670 | 89548  | 101046 | 92574  | 99531  | 104644  | 109225 | 109159  | 98766  | 94838  | 89542 | 71384  |
| 3   | 2004 | 1222484 | 141538 | 94596  | 100696 | 100801 | 102214 | 105728  | 111102 | 110425  | 98492  | 94840  | 90833 | 71219  |
| 4   | 2005 | 1244041 | 142311 | 94234  | 100529 | 97441  | 106833 | 108536  | 111066 | 111430  | 103273 | 103310 | 92364 | 72714  |

Excel ve Calc tabloları ile çalışma konusunu daha detaylı olarak inceleyeceğiz. İlgili bağlantıya [buradan](02_read_excel.md) erişebilirsiniz.

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