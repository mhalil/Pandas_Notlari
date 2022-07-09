# PANDAS KOMUTLARI

# Veri Çerçevesi Oluşturmak ya da İçe Aktarmak

## import Fonksiyonu

Pandas Kütüphanesini içe aktarıp kodlamada kolay ve hızlı olması adına bu kütüphaneye **pd** adını atayalım;

```python
import pandas as pd
```

## DataFrame() Fonksiyonu

Veri Çerçevesi Oluşturmak için **DataFrame()** fonksiyonunu kullanıyoruz. Parantez içine parametre yazmalıyız

```python
pd.DataFrame()
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

## head() Fonksiyonu

Oluşturduğumuz ya da çalışmamıza dahil ettiğimiz Veri Çerçevelerinin ilk satırlarını görüp içerik hakkında bilgi edinmek istersek **head()** fonksiyonunu kullanabiliriz.

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

**head()** fonksiyonunu içine parametre olarak bir değer yazmazsak, veri çerçevesinin **ilk 5** değerini görüntüler. Değer belirtirsek belirttiğimiz değer kadar veri görüntüler.

```python
print(veri.head(3))
```

|     | isim    | yaş | iş-meslek   |
| --- | ------- | --- | ----------- |
| 0   | Mustafa | 25  | mühendis    |
| 1   | Halil   | 38  | programcı   |
| 2   | Burak   | 41  | akademisyen |

## tail() Fonksiyonu

**head()** fonksiyonuna benzer bir fonksiyondur. Oluşturduğumuz ya da çalışmamıza dahil ettiğimiz Veri Çerçevelerinin son satırlarını görüp içerik hakkında bilgi edinmek istersek **tail()** fonksiyonunu kullanabiliriz.

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

## CSV Dosyasını İçe Aktarmak

## read_csv() Fonksiyonu

**nba.csv** isimli dosyasınının içeriğini çalışmamıza aktaralım;

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

**read_table()** fonksiyonu ile **csv** uzantılı dosyalar içe aktarıldığında, dosyanın her satırı, tablonun bir sütünuna yazılır. Yani tabloda 2 sütun oluşturulur birinde index bilgisi, ikinci sütunda ise **csv** dosyasının satırlarındaki bilgiler bulunur.

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

CSV dosyalarını **read_table()** fonksiyonu ile içe aktarırken **delimiter = ","** parametresi kullanılırsa parametresi eklenirse, dosya içeriği, read_csv fonksiyonu ile aynı çıktıyı verir.

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

**xls** ya da **xlsx** uzantılı Excel dosyalarının içeriğini çalışmamıza dahil etmek için **read_excel()** fonksiyonunu kullanmalıyız.

```python
pd.read_excel(dosya_adi)
```

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
