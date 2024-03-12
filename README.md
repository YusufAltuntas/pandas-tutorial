[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YusufAltuntas/pandas-tutorial/blob/master/pandas-tutorial.ipynb)

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*3GbLagVDPY9QKjjgB_Tfqw.png)

[**1. Pandas Temelleri**](#pandas-temelleri)

  - [**1.1 Kurulum**](#11-kurulum)
    - [Pip Kullanarak Kurulum](#111-pip-kullanarak-kurulum)
    - [Conda Kullanarak Kurulum](#112-conda-kullanarak-kurulum)
   
[**2. Veri Yapıları**](#2-pandas-veri-yapıları)

  - [**Pandas Serileri**](#21-pandas-serileri-series)
      - Seri nedir?
      - [Seri oluşturma](#211-seri-oluşturma)
        - [Listelerden seri oluşturma](#listelerden-seri-oluşturma)
        - [NumPy dizilerinden seri oluşturma](#numpy-dizilerinden-seri-oluşturma)
      - [Seri İndeksleme ve Dilimleme](#212-seri-i̇ndeksleme-ve-dilimleme)
      - [Seri Özellikleri ve Metodları](#213-seri-özellikleri-ve-metodları)
        - `head()` ve `tail()`
        - `describe()`
        - `value_counts()`
        - `unique()`
   
  - [**Pandas DataFrames**](#22-pandas-dataframes-veri-çerçeveleri)
      - Veri çerçevesi nedir?
      - [Veri çerçevesi oluşturma](#221-veri-çerçevesi-oluşturma)
        - [Sözlükten veri çerçevesi oluşturma](#sözlükten-dataframe-oluşturma)
        - [NumPy dizisinden veri çerçevesi oluşturma](#numpy-dizilerinden-seri-oluşturma)
      - [Veri Çerçevesi İndeksleme ve Dilimleme](#222-dataframe-i̇ndeksleme-ve-dilimleme)
      - [Veri Çerçevesi Özellikleri ve Metodları](#223-dataframe-özellikleri-ve-metodları)
        - `info()`
        - `head()` ve `tail()`
        - `describe()`
        - `shape`
        - `columns`
        - `index`

[**3. Veri Okuma ve Yazma**](#3-veri-okuma-ve-yazma)
  - [CSV dosyalarından veri okuma](#csv-dosyalarından-veri-okuma)
  - [Excel dosyalarından veri okuma](#excel-dosyalarından-veri-okuma)
  - [Veri çerçevesini CSV ve Excel formatlarında kaydetme](#veri-çerçevesini-csv-ve-excel-formatlarında-kaydetme)

[**4. Veri Kontrolü**](#4-veri-kontrolü)

  - [İlk ve Son Gözlemleri Görüntüleme](#i̇lk-ve-son-gözlemleri-görüntüleme)
  - [Satır ve Sütun Sayısı Bilgisi Alma: shape](#satır-ve-sütun-sayısı-bilgisi-alma-shape)
  - [Veri Seti Hakkında Detaylı Bilgi Alma: info()](#veri-seti-hakkında-detaylı-bilgi-alma-info)
  - [Sütun ve Satır Gösterimi Ayarları: pd.set_option()](#sütun-ve-satır-gösterimi-ayarları-pdset_option)

[**5. Satır ve Sütunlara Erişim İşlemleri**](#5-satır-ve-sütun-i̇şlemleri)

  - [**Sütunlara Erişme**](#51-sütunlara-erişme)
    - [Tekil Erişim](#511-tekil-erişim)
    - [Çoklu Erişim](#512-çoklu-erişim)

  - [**Satırlara Erişme: iloc ve loc**](#52-satırlara-erişme-iloc-ve-loc)
    - [iloc()](#521-iloc)
    - [loc()](#loc)

  - [**Satır ve Sütunlara Erişme: İki Nokta Kullanımı (indexing)**](#53-satır-ve-sütunlara-erişme-i̇ki-nokta-kullanımı-indexing)
    - [Belirli Bir Satır Aralığına Erişme](#531-belirli-bir-satır-aralığına-erişme)
    - [Belirli Bir Sütun Aralığına Erişme](#532-belirli-bir-sütun-aralığına-erişme)
    - [Belirli Bir Satır ve Sütun Aralığına Erişme](#533-belirli-bir-satır-ve-sütun-aralığına-erişme)
    - [Koşullu Erişim ve Dilimleme](#534-koşullu-erişim-ve-dilimleme)

  - [**Sütuna Ait Değerleri Saydırma: value_counts()**](#54-sütuna-ait-değerleri-saydırma-value_counts)

[**6. İndex İşlemleri**](#6-i̇ndex-i̇şlemleri)

  - [**İndeks nedir?**](#61-i̇ndeks-nedir)

  - [**İndeks Ayarlama: set_index() ve index_col**](#62-i̇ndeks-ayarlama-set_index-ve-index_col)
    - [set_index()](#621-set_index)
    - [index_col Kullanımı](#622-index_col-kullanımı)

  - [**İndeks Aracılığıyla Erişim: loc**](#63-i̇ndeks-aracılığıyla-erişim-loc)
  - [**İndeks Sıfırlama: reset_index()**](#64-i̇ndeks-sıfırlama-reset_index)
  - [**İndekslerin Sıralanması: sort_index()**](#65-i̇ndekslerin-sıralanması-sort_index)

[**7.Filtreleme**](#7-filtreleme)

  - [**Tekli Filtreleme: İç içe ve loc**](#71-tekli-filtreleme-i̇ç-içe-ve-loc)

  - [**Çoklu Filtreleme: &, | ve isin()**](#72-çoklu-filtreleme---ve-isin)
    - [Mantıksal Operatörler](#721-mantıksal-operatörler)
    - [isin() Kullanımı](#722-isin-kullanımı)

  - [**String İçerenleri Filtreleme: str.contains()**](#73-string-i̇çerenleri-filtreleme-strcontains)


[**8. Sütun ve Satır Güncelleme**](#8-sütun-ve-satır-güncelleme)

  - [**Sütun Güncelleme: columns, List Comprehension, str.replace(), rename**](#81-sütun-güncelleme-columns-list-comprehension-strreplace-rename)
    - [columns Kullanımı](#811-columns-kullanımı)
    - [List Comprehension Kullanımı](#812-list-comprehension-kullanımı)
    - [str.replace() Kullanımı](#813-strreplace-kullanımı)
    - [rename() Kullanımı](#814-rename-kullanımı)

  - [**Satır Güncelleme: loc, at, str.lower(), apply(), applymap(), lambda, map() ve replace()**](#82-satır-güncelleme-loc-at-strlower-apply-applymap-lambda-map-ve-replace)
    - [loc Kullanımı](#821-loc-kullanımı)
    - [at Kullanımı](#822-at-kullanımı)
    - [Çoklu Satır Güncellemesi(str.lower(), apply() ve lambda ve map() ve replace() fonksiyonları)](#823-çoklu-satır-güncellemesistrlower-apply-ve-lambda-ve-map-ve-replace-fonksiyonları)
      - [str.lower() Kullanımı](#strlower-kullanımı)
      - [apply() Kullanımı](#apply-kullanımı)
      - [apply() ve lambda Kullanımı](#apply-ve-lambda-kullanımı)
      - [map() ve lambda Kullanımı](#map-ve-lambda-kullanımı)
      - [map() ve replace Yöntemi](#map-ve-replace-yöntemi)


[**9. Sütun ve Satır Ekleme ve Kaldırma**](#9-sütun-ve-satır-ekleme-ve-kaldırma)

  - [**Sütun Ekleme ve Kaldırma: birleştirme, drop(), str.split(), assign(), merge(), join()**](#91-sütun-ekleme-ve-kaldırma-birleştirme-drop-strsplit-assign-merge-join)
    - [Sütunların Birleştirilmesi](#911-sütunların-birleştirilmesi)
    - [drop() Yöntemi](#912-drop-yöntemi)
    - [str.split() Kullanımı](#913-strsplit-kullanımı)
    - [assign() Kullanımı](#914-assign-metodu)
    - [join() Kullanımı](#915-join-metodu)
    - [merge() Kullanımı](#916-merge-metodu)
    
  - [**Satır Ekleme ve Kaldırma: append(), concat() ve drop()**](#92-satır-ekleme-ve-kaldırma-append-concat-ve-drop)
    - [concat() Metodu](#921-concat-metodu)
    - [drop() Metodu](#922-drop-metodu)


[**10. Veri Analizi**](#10-veri-analizi)

  - [**Temel İstatistiksel Hesaplamalar**](#101-temel-i̇statistiksel-hesaplamalar)
    - [describe() Metodu](#1011-describe-metodu)
    - [mean() Metodu](#1012-mean-metodu)
    - [median() Metodu](#1013-median-metodu)
    - [Değerlerin Saydırılması: value_counts()](#1014-değerlerin-saydırılması-value_counts)
    - [min(), max(), sum(), std(), nlargest(), nsmallest()](#1015-min-max-sum-std-nlargest-nsmallest)
    - [Bir Gruba Göre İstatistik: groupby(), agg(), median() ve std()](#1016-bir-gruba-göre-i̇statistik-groupby-agg-median-ve-std)
    - [Bir String İçeriğine Göre Bir İstatistik: groupby(), apply(), lambda, str.contains() ve sum()](#1017-bir-string-i̇çeriğine-göre-bir-i̇statistik-groupby-apply-lambda-strcontains-ve-sum)
    
  - [**Veri Sıralama**](#102-veri-sıralama)
    - [sort_values()](#1021-sort_values)
    - [İndekse Göre Sıralama: sort_index()](#1022-i̇ndekse-göre-sıralama-sort_index)
    - [Serilerin Sıralanması: sort_values()](#1023-serilerin-sıralanması-sort_values)
    - [En Büyüklerin Sıralanması: nlargest()](#1024-en-büyüklerin-sıralanması-nlargest)
    - [En Küçüklerin Sıralanması: nsmallest()](#1025-en-küçüklerin-sıralanması-nsmallest)

  - [**Gruplama ve Özetleme**](#103-gruplama-ve-özetleme)
    - [Gruplayarak Saydırma, Yüzde Alma ve İndeks İnceleme](#1031-gruplayarak-saydırma-yüzde-alma-ve-i̇ndeks-i̇nceleme)

  - [**Veriyi Belirli Aralıklara Bölme**](#104-veriyi-belirli-aralıklara-bölme)
    - [pd.cut() Fonksiyonu](#pdcut-fonksiyonu)
    - [pd.qqut() Fonksiyonu](#pdqcut-fonksiyonu)

[**11. Veri İşleme ve Temizleme**](#11-veri-i̇şleme-ve-temizleme)

  - [**Eksik Verilerle Başa Çıkma**](#111-eksik-verilerle-başa-çıkma)
    - [Eksik Verileri Tespit Etme: isnull() ve notnull()](#111-eksik-verilerle-başa-çıkma)
    - [Eksik Verileri Temizleme: dropna()](#1112-eksik-verileri-temizleme-dropna)
    - [Eksik ""NaN" Değerleri Değiştirme: replace() ve fillna()](#1113-eksik-nan-değerleri-değiştirme-replace-ve-fillna)
    - [NaN Değerleri Kendinden Bir Önceki veya Bir Sonraki Değere Çevirme: ffill() ve bfill()](#1114-nan-değerleri-kendinden-bir-önceki-veya-bir-sonraki-değere-çevirme-ffill-ve-bfill)

  - [**Veri Türü Dönüşümleri**](#112-veri-türü-dönüşümleri)
    - [``astype()`` Metodu](#1-astype-metodu)
    - [``to_numeric()`` Fonksiyonu](#2-to_numeric-fonksiyonu)
    - [``to_datetime()`` Fonksiyonu](#3-to_datetime-fonksiyonu)
    - [``astype()`` ve ``map()`` Kullanımı](#4-astype-ve-map-kullanımı)
    
  - [**Veri Çerçevesinde Tekrar Eden Değerleri Kaldırma**](#113-veri-çerçevesinde-tekrar-eden-değerleri-kaldırma)
    - [`drop_duplicates()` Metodu](#1131-drop_duplicates-metodu)
    - [`unique()` ve `nunique()` Metotları](#1132-unique-ve-nunique-metotları)

[**12. Zaman Serisi Verileri**](#12-zaman-serisi-verileri)

  - [**Tarih ve Saat Veri Türleri**](#121-tarih-ve-saat-veri-türleri)
    - [datetime Sınıfı](#1211-datetime-sınıfı)
    - [timedelta Sınıfı](#1212-timedelta-sınıfı)
    - [strftime() ve strptime() Metodları](#1213-strftime-ve-strptime-metodları)

  - [**Zaman Serisi Oluşturma**](#122-zaman-serisi-oluşturma)
    - [Manuel Olarak Zaman Serisi Oluşturma](#1221-manuel-olarak-zaman-serisi-oluşturma)
    - [Pandas ile Zaman Serisi Oluşturma](#1222-pandas-ile-zaman-serisi-oluşturma)
    - [NumPy ile Zaman Serisi Oluşturma](#1223-numpy-ile-zaman-serisi-oluşturma)

## **Pandas Temelleri**

## **1.1 Kurulum**

Pandas'ı yüklemek için `pip` veya `conda` kullanabiliriz. Bu kurulumlar, Python ortamınıza pandas kütüphanesini ekler.

### **1.1.1 Pip Kullanarak Kurulum:**

Pip, Python paketlerinin yönetiminde sıkça kullanılan bir araçtır. Aşağıdaki komutu kullanarak pandas'ı pip aracılığıyla kurabilirsiniz:

```bash
pip install pandas
```

### **1.1.2 Conda Kullanarak Kurulum:**

Conda, Anaconda veya Miniconda gibi dağıtımlarla birlikte gelen bir paket yöneticisidir. Aşağıdaki komutu kullanarak pandas'ı conda aracılığıyla kurabilirsiniz:

```bash
conda install pandas
```

Bu komutlar, pandas kütüphanesinin en son sürümünü indirir ve yükler.

---


```python
import pandas as pd
```

## **2) Pandas Veri Yapıları**

Pandas kütüphanesi iki ana veri yapısı sunar: Seriler (Series) ve Veri Çerçeveleri (DataFrames).
Bu seri, indekslerle (varsayılan olarak 0'dan başlar) etiketlenmiş değerler içerir.

### **2.1 Pandas Serileri (Series):**

* Pandas'ta Series veri yapısı, tek boyutlu, indekslenmiş ve değiştirilemeyen (immutable) veri dizilerini temsil eder. Her bir eleman, bir indeksle ilişkilendirilmiştir. Örneğin Bu seri, indekslerle (varsayılan olarak 0'dan başlar) etiketlenmiş değerler içerir:


```python
seri = pd.Series([10, 20, 30, 40, 50])
print(seri)
```

    0    10
    1    20
    2    30
    3    40
    4    50
    dtype: int64
    

**Pandas Series Yapısı Özellikleri:**

1) **Tek Boyutlu Veri Yapısı:** Pandas Series, yalnızca tek bir boyutta veri saklar.

2) **Indekslenmiş Veriler:** Her eleman, bir indeksle eşleştirilmiştir. Önceden tanımlı veya özel bir indeks kullanılabilir.

3) **Homojen Veri Tipleri:** Series, herhangi bir veri tipinde veri saklayabilir. Örneğin, tam sayılar, kayan nokta sayıları, dizeler veya diğer Python veri tipleri olabilir.

4) **Değiştirilemeyen (Immutable):** Bir Series oluşturulduktan sonra, içeriği değiştirilemez. Ancak yeni bir Series oluşturularak değişiklik yapılabilir.

#### **2.1.1 Seri Oluşturma**

* Pandas serileri, çeşitli veri tiplerinden oluşturulabilir.

##### **Listelerden Seri Oluşturma**


```python
import pandas as pd

data = [1, 2, 3, 4, 5]
seri = pd.Series(data)
print(seri)
```

    0    1
    1    2
    2    3
    3    4
    4    5
    dtype: int64
    

##### **NumPy Dizilerinden Seri Oluşturma**


```python
import pandas as pd
import numpy as np

data = np.array([1, 2, 3, 4, 5])
seri = pd.Series(data)
print(seri)
```

    0    1
    1    2
    2    3
    3    4
    4    5
    dtype: int32
    

#### **2.1.2 Seri İndeksleme ve Dilimleme**

* Pandas serileri, indeksleme ve dilimleme işlemleri için kullanılabilir.


```python
print(seri[0], "\n")  # İlk eleman
print(seri[1:3], "\n")  # 1. ve 2. elemanlar

# Dilimleme
print(seri[:3], "\n")  # İlk 3 eleman
print(seri[-2:], "\n")  # Son 2 eleman
```

    1 
    
    1    2
    2    3
    dtype: int32 
    
    0    1
    1    2
    2    3
    dtype: int32 
    
    3    4
    4    5
    dtype: int32 
    
    

#### **2.1.3 Seri Özellikleri ve Metodları**

* Pandas serileri, çeşitli özelliklere ve metodlara sahiptir.


```python
# Serinin boyutu
print(seri.size, "\n")

# Serinin indeksleri
print(seri.index, "\n")

# Serinin değerleri
print(seri.values, "\n")

# Serinin istatistiksel özetleri
print(seri.describe(), "\n")
```

    5 
    
    RangeIndex(start=0, stop=5, step=1) 
    
    [1 2 3 4 5] 
    
    count    5.000000
    mean     3.000000
    std      1.581139
    min      1.000000
    25%      2.000000
    50%      3.000000
    75%      4.000000
    max      5.000000
    dtype: float64 
    
    

### **2.2 Pandas DataFrames (Veri Çerçeveleri):**

* DataFrame, Pandas kütüphanesindeki temel veri yapısıdır ve tablo benzeri bir iki boyutlu veri yapısını temsil eder. Veriler, farklı veri tipleri içerebilen sütunlar halinde düzenlenmiştir. DataFrame, verileri etiketli bir şekilde saklamak, işlemek ve analiz etmek için kullanılır. Pandas, Python'da veri analizi ve manipülasyonu için oldukça popüler bir kütüphanedir ve DataFrame, Pandas'ın bu popülerliğinde önemli bir rol oynamaktadır.

DataFrame'in temel özellikleri şunlardır:

1) **İki Boyutlu Yapı:** DataFrame, satırlar ve sütunlar şeklinde iki boyutlu bir yapıya sahiptir. Satırlar genellikle gözlemleri (örnekleri) temsil ederken, sütunlar değişkenleri (özellikleri) temsil eder.

2) **İndeksleme:** DataFrame'in satırları, indeks adı verilen bir etiketle belirlenir. Bu indeks, her bir gözlemin benzersiz bir tanımlayıcısını sağlar.

3) **Farklı Veri Tipleri:** Her bir sütun farklı veri tiplerini içerebilir. Örneğin, bir sütun sayısal değerleri içerebilirken, diğer bir sütun metinsel değerleri içerebilir.

4) **Esnek Boyutlar:** DataFrame'ler, değişken sayısını ve gözlem sayısını dinamik olarak yönetebilir. Yani, DataFrame boyutları veri ekledikçe veya çıkardıkça otomatik olarak genişleyebilir veya küçülebilir.

5) **Veri Manipülasyonu:** Pandas DataFrame, veri analizi, filtreleme, gruplama, birleştirme ve dönüşüm gibi çeşitli işlemleri kolayca gerçekleştirmenizi sağlayan geniş bir metod koleksiyonuna sahiptir.

---

#### **2.2.1 Veri Çerçevesi Oluşturma**

* Pandas veri çerçeveleri, farklı veri kaynaklarından oluşturulabilir.

##### **Sözlükten DAtaFrame Oluşturma**


```python
import pandas as pd

data = {'Name': ['John', 'Anna', 'Peter', 'Linda'],
        'Age': [28, 25, 32, 35]}
df = pd.DataFrame(data)
print(df)
```

        Name  Age
    0   John   28
    1   Anna   25
    2  Peter   32
    3  Linda   35
    

##### **NumPy Dizisinden DataFrame Oluşturma**


```python
import pandas as pd
import numpy as np

data = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
df = pd.DataFrame(data, columns=['A', 'B', 'C'])
print(df)
```

       A  B  C
    0  1  2  3
    1  4  5  6
    2  7  8  9
    

#### **2.2.2 DataFrame İndeksleme ve Dilimleme**

* Veri çerçeveleri, satırları ve sütunları indekslemek ve dilimlemek için kullanılabilir.


```python
import pandas as pd

# Örnek bir veri listesi
data = {'Name': ['Ahmet', 'Ayşe', 'Mehmet', 'Fatma', 'Ali']}

# DataFrame oluşturma
df = pd.DataFrame(data)

# DataFrame'i görüntüleme
print(df, "\n")


# Sütun seçme
print(df['Name'], "\n")

# Satır seçme
print(df.loc[0], "\n")

# Belirli bir hücreye erişme
print(df.at[0, 'Name'], "\n")

# Dilimleme
print(df.iloc[1:3, :])
```

         Name
    0   Ahmet
    1    Ayşe
    2  Mehmet
    3   Fatma
    4     Ali 
    
    0     Ahmet
    1      Ayşe
    2    Mehmet
    3     Fatma
    4       Ali
    Name: Name, dtype: object 
    
    Name    Ahmet
    Name: 0, dtype: object 
    
    Ahmet 
    
         Name
    1    Ayşe
    2  Mehmet
    

#### **2.2.3 DataFrame Özellikleri ve Metodları**

* Pandas veri çerçeveleri, çeşitli özelliklere ve metodlara sahiptir.


```python
# Veri çerçevesinin boyutu
print(df.shape, "\n")

# Veri çerçevesinin indeksleri
print(df.index, "\n")

# Veri çerçevesinin sütunları
print(df.columns, "\n")

# İlk n satırı görüntüleme
print(df.head(), "\n")

# Son n satırı görüntüleme
print(df.tail())
```

    (5, 1) 
    
    RangeIndex(start=0, stop=5, step=1) 
    
    Index(['Name'], dtype='object') 
    
         Name
    0   Ahmet
    1    Ayşe
    2  Mehmet
    3   Fatma
    4     Ali 
    
         Name
    0   Ahmet
    1    Ayşe
    2  Mehmet
    3   Fatma
    4     Ali
    


```python
# Sözlük üzerinden bir Veri Çerçevesi oluşturma
data = {'Name': ['Ali', 'Veli', 'Ayşe', 'Fatma'],
        'Age': [25, 30, 35, 40],
        'City': ['İstanbul', 'Ankara', 'İzmir', 'Bursa']}

df = pd.DataFrame(data)
print(df)
```

        Name  Age      City
    0    Ali   25  İstanbul
    1   Veli   30    Ankara
    2   Ayşe   35     İzmir
    3  Fatma   40     Bursa
    

## **3) Veri Okuma ve Yazma**

Pandas, çeşitli dosya formatlarından veri yüklemek için kullanılabilir. En yaygın kullanılanlar arasında CSV, Excel, SQL ve JSON bulunur.

---

### **CSV Dosyalarından Veri Okuma**

* CSV (Comma Separated Values - Virgülle Ayrılmış Değerler) dosyaları, tablo biçimindeki verileri depolamak için yaygın olarak kullanılır. Pandas, `read_csv()` fonksiyonuyla CSV dosyalarını okuyabilir.

```python
# CSV dosyasından veri okuma
df = pd.read_csv('veri.csv')
print(df)
```

Burada `veri.csv` dosyası, mevcut çalışma dizininizde bulunmalıdır.

---

### **Excel Dosyalarından Veri Okuma**

* Excel dosyaları, sıkça kullanılan bir veri depolama formatıdır. Pandas, `read_excel()` fonksiyonuyla Excel dosyalarını okuyabilir.

```python
# Excel dosyasından veri okuma
df = pd.read_excel('veri.xlsx', sheet_name='Sheet1')
print(df)
```

Bu komut, 'veri.xlsx' Excel dosyasındaki 'Sheet1' sayfasındaki veriyi okur.

---


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx')
```

### **Veri Çerçevesini CSV ve Excel Formatlarında Kaydetme**

* Pandas, veri çerçevesini CSV ve Excel formatlarında kaydetmek için `to_csv()` ve `to_excel()` metodlarını sağlar.

```python
import pandas as pd

# Veri çerçevesini CSV olarak kaydetme
df.to_csv('veri_yeni.csv', index=False)

# Veri çerçevesini Excel olarak kaydetme
df.to_excel('veri_yeni.xlsx', index=False)
```

---

Şimdi gerçek bir veri seti üzerinde işlemleri yapalım

## **4) Veri Kontrolü**

Veri kontrolü, veri kümesinin yapısını anlamak için önemlidir. Başlangıçta veya sonunda bulunan veri örneklerini görüntülemek için `head()` ve `tail()` fonksiyonları kullanılır.

### **İlk ve Son Gözlemleri Görüntüleme:**


```python
# İlk 5 gözlemi görüntüleme
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AEFES</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Son 5 satırı gösterme
df.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>504</th>
      <td>YYAPI</td>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>505</th>
      <td>YYLGD</td>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>506</th>
      <td>ZEDUR</td>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>507</th>
      <td>ZOREN</td>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>508</th>
      <td>ZRGYO</td>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
</div>



### **Satır ve Sütun Sayısı Bilgisi Alma: shape**

`shape` modülünü kullanarak satır ve  sütun sayısı bilgisini elde ederiz.


```python
df.shape
```




    (509, 8)



### **Veri Seti Hakkında Detaylı Bilgi Alma: info()**

Bu metot, veri setinin hakkında bilgileri  döndürmektedir. Bu bilgilere erişim  için
`info()` adını kullanabilirsiniz.

Bu fonksiyon, veri çerçevesindeki her sütunun veri tipini, veri tiplerinin sayısal dağılımını, bellek kullanımını, eksik değerleri ve sütunların ve satırların toplamda kaç olduğu bilgisini gösterir.


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 509 entries, 0 to 508
    Data columns (total 8 columns):
     #   Column                  Non-Null Count  Dtype  
    ---  ------                  --------------  -----  
     0   Kod                     509 non-null    object 
     1   Hisse Adı               509 non-null    object 
     2   Sektör                  509 non-null    object 
     3   Kapanış(TL)             509 non-null    float64
     4   Piyasa Değeri(mn TL)    509 non-null    float64
     5   Piyasa Değeri(mn $)     509 non-null    float64
     6   Halka AçıklıkOranı (%)  509 non-null    float64
     7   Sermaye(mn TL)          509 non-null    float64
    dtypes: float64(5), object(3)
    memory usage: 31.9+ KB
    

### **Sütun ve Satır Gösterimi Ayarları: pd.set_option()**

Bu bölümde, pandas kitaplığında  bulunan `pd.set_option()` işlevinin  nasıl kullanılacağı gösterilecektir.

* df.head() veya df.tail() ile çalıştırdığımızda sütunların eğer sütun sayısı fazla olsaydı sadece bir kısmını görebilirdik. Veri çerçevesindeki sütunların tamamını görmek isteseydik pd.set_option() ile aşağıdaki ayarı yapabilirdik.

```
pd.set_option('display.max_columns', None)
```

None kullanılmasının amacı, display.max_columns seçeneğini sınırlamadan kaldırmaktır.

```
pd.set_option('display.max_columns', 10)
```

* bu kodla sütun sayısını 10 ile sınırlandırırdık.

Aynı şekilde, satır sayısını da aşağıdaki gibi ayarlayabiliriz.

```
pd.set_option('display.max_rows', None)
```

## **5) Satır ve Sütun İşlemleri**

### **5.1 Sütunlara Erişme**

Pandas veri çerçeveleri, farklı sütunlardaki verilere erişmek için çeşitli yöntemler sağlar.

#### **5.1.1 Tekil Erişim**

Son oluşturduğumuz veri çerçevesinden Sektör sütununa erişmek istediğimizi varsayalım.


```python
df["Sektör"]
```




    0           Aracı Kurumlar
    1            Kimyasal Ürün
    2                Kırtasiye
    3      Perakande - Ticaret
    4        Meşrubat / İçecek
                  ...         
    504        İnşaat- Taahhüt
    505                   Gıda
    506               Elektrik
    507               Elektrik
    508                    GYO
    Name: Sektör, Length: 509, dtype: object



* Aynı sütuna ulaşmanın bir başka yolu ise nokta notasyonunu kullanmaktır.


```python
df.Sektör
```




    0           Aracı Kurumlar
    1            Kimyasal Ürün
    2                Kırtasiye
    3      Perakande - Ticaret
    4        Meşrubat / İçecek
                  ...         
    504        İnşaat- Taahhüt
    505                   Gıda
    506               Elektrik
    507               Elektrik
    508                    GYO
    Name: Sektör, Length: 509, dtype: object



Hangi yöntemi tercih etmeliyiz?

* pd_df['Sektör'] ifadesi, DataFrame üzerindeki sütuna doğrudan bir dizi indeksi kullanarak erişim sağlar. Bu yöntem, sütun ismi boşluk veya özel karakterler içerdiğinde veya Python programlama dilinde özel bir kelimeyle çakıştığında daha güvenlidir. Örneğin, eğer sütun ismi sutun ismi veya if gibi bir kelime ise bu ifadeleri kullanarak doğrudan sütuna erişim sağlayabiliriz.

* pd_df.Sektör ifadesi ise, nokta notasyonunu kullanarak sütuna erişim sağlar. Bu ifade daha kısa ve daha okunabilir bir yazım şekli sunar. Ancak bazı durumlarda, sütun ismi boşluk veya özel karakterler içeriyorsa veya Python programlama dilinde özel bir kelimeyle çakışıyorsa hata verebilir.

Daha önce oluşturduğumuz veri çerçevesine sütunlar ekleyip az önce öğrendiklerimizi pekiştirelim.

### **5.1.2 Çoklu Erişim**

Buraya kadar tek bir sütuna erişimi gördük. Birden fazla sütuna erişmek istediğimizde aşağıdaki ifadeyi kullanıyoruz.


```python
df[["Kod", "Hisse Adı"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AEFES</td>
      <td>Anadolu Efes</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>504</th>
      <td>YYAPI</td>
      <td>Yesil Yapi</td>
    </tr>
    <tr>
      <th>505</th>
      <td>YYLGD</td>
      <td>Yayla Agro Gıda</td>
    </tr>
    <tr>
      <th>506</th>
      <td>ZEDUR</td>
      <td>Zedur Enerji</td>
    </tr>
    <tr>
      <th>507</th>
      <td>ZOREN</td>
      <td>Zorlu Enerji</td>
    </tr>
    <tr>
      <th>508</th>
      <td>ZRGYO</td>
      <td>Ziraat GYO</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 2 columns</p>
</div>



Yukarıdaki iki duruma dikkat edelim. Birincisi, tek sütuna tek köşeli parantez ([]) ile ulaşırken çoklu sütunlara çift köşeli parantez ([[]]) ile ulaştık. İkincisi, tek sütuna erişirken çıktıyı bir seri olarak alıyorduk ancak çoklu sütunlara erişmek istediğimizde artık bir seri değil bir veri çerçevesi olarak çıktıyı alıyoruz.

Son olarak, sütun isimlerinin tamamını görmek istiyorsak aşağıdaki ifadeyi kullanabiliriz.


```python
df.columns
```




    Index(['Kod', 'Hisse Adı', 'Sektör', 'Kapanış(TL)', 'Piyasa Değeri(mn TL)',
           'Piyasa Değeri(mn $)', 'Halka AçıklıkOranı (%)', 'Sermaye(mn TL)'],
          dtype='object')



## **5.2 Satırlara Erişme: iloc ve loc**

### **5.2.1 iloc()**

* iloc, integer location anlamına gelir ve DataFrame veya Series üzerinde konum tabanlı indeksleme yapmamıza olanak tanır. İndeksler sıfırdan başlar ve satır veya sütunları belirlemek için tamsayı indekslerini kullanır. iloc kullanırken satır veya sütunların konumunu belirtmek için köşeli parantez içinde tamsayı indeksleri kullanırız.

İlk satıra erişelim


```python
df.iloc[0]
```




    Kod                                A1CAP
    Hisse Adı                     A1 Capital
    Sektör                    Aracı Kurumlar
    Kapanış(TL)                         26.8
    Piyasa Değeri(mn TL)              3618.0
    Piyasa Değeri(mn $)                138.7
    Halka AçıklıkOranı (%)              25.9
    Sermaye(mn TL)                     135.0
    Name: 0, dtype: object



Tek bir satıra erişebileceğimiz gibi birden fazla satıra da erişebiliriz. Tıpkı çoklu sütuna erişimde olduğu gibi ilerleyeceğiz.


```python
df.iloc[[0,1]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
  </tbody>
</table>
</div>



``iloc`` ile sütunlara da erişebiliriz. Örneğin, ilk iki satırın 5. sütununa erişmeye çalışalım.


```python
df.iloc[[0,1],4]
```




    0    3618.0
    1     903.3
    Name: Piyasa Değeri(mn TL), dtype: float64



Çoklu sütunlara da erişebiliriz. Örneğin, 4. ve 5. sütunlara erişelim.


```python
df.iloc[[0,1], [3,4]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>26.80</td>
      <td>3618.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>84.25</td>
      <td>903.3</td>
    </tr>
  </tbody>
</table>
</div>



### **5.2.2 loc()**

``loc``, label location anlamına gelir ve DataFrame veya Series üzerinde etiket tabanlı indeksleme yapmak için kullanılan bir indeksleme yöntemidir.

İlk satıra erişelim. Burada 0 etiketine sahip satırı getireceğiz.


```python
df.loc[0]
```




    Kod                                A1CAP
    Hisse Adı                     A1 Capital
    Sektör                    Aracı Kurumlar
    Kapanış(TL)                         26.8
    Piyasa Değeri(mn TL)              3618.0
    Piyasa Değeri(mn $)                138.7
    Halka AçıklıkOranı (%)              25.9
    Sermaye(mn TL)                     135.0
    Name: 0, dtype: object



Tek bir satıra erişebileceğimiz gibi birden fazla satıra da erişebiliriz. Bu defa örnek olarak 0 ve 1 etiketlerine sahip satırları getireceğiz.


```python
df.loc[[0,1]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
  </tbody>
</table>
</div>



Buraya kadar yaptıklarımız aslında iloc'ta yaptıklarımıza benziyor ancak biz etiket bazlı ilerliyoruz. Son olarak, son sütuna erişelim.


```python
df.loc[[0,1], 'Sermaye(mn TL)']
```




    0    135.0
    1     10.7
    Name: Sermaye(mn TL), dtype: float64



Çoklu sütunlara da erişebiliriz. Örneğin, aşağıdaki iki sütuna erişelim.


```python
df.loc[[0,1], ['Piyasa Değeri(mn TL)','Piyasa Değeri(mn $)']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3618.0</td>
      <td>138.7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>903.3</td>
      <td>34.6</td>
    </tr>
  </tbody>
</table>
</div>



### **5.3 Satır ve Sütunlara Erişme: İki Nokta Kullanımı (indexing)**

Pandas veri çerçeveleri üzerinde, satır ve sütunlara aynı anda erişmek için "İki Nokta Kullanımı" yani "indexing" adı verilen bir yöntem bulunmaktadır. Bu yöntem, hem satırları hem de sütunları indeksleyerek belirli bir aralığa erişmeyi sağlar.

#### **5.3.1 Belirli Bir Satır Aralığına Erişme**

":" kullanarak da ilk 5 satıra erişebiliriz. Burada dikkat etmemiz gereken nokta çift parantez yerine tek parantez kullanacak olmamızdır


```python
df.iloc[0:4, 0] # ilk sütundaki 4. indexe kadar olan değerleri yazdırma (4. index dahil değil)
```




    0    A1CAP
    1    ACSEL
    2     ADEL
    3    ADESE
    Name: Kod, dtype: object




```python
df.loc[0:4, "Kod"] # ilk sütundaki ilk 5 indexi yazdırma
```




    0    A1CAP
    1    ACSEL
    2     ADEL
    3    ADESE
    4    AEFES
    Name: Kod, dtype: object



#### **5.3.2 Belirli Bir Sütun Aralığına Erişme**

"Hisse Adı" ve "Piyasa Değeri(mn TL)" sütunlarının verilerini almak için  aşağıdaki  kod  parçasını kullanırız.


```python
df[["Hisse Adı", "Piyasa Değeri(mn TL)"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Piyasa Değeri(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1 Capital</td>
      <td>3618.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>903.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adel Kalemcilik</td>
      <td>5788.1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adese AVM</td>
      <td>1633.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Anadolu Efes</td>
      <td>41950.7</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>504</th>
      <td>Yesil Yapi</td>
      <td>875.0</td>
    </tr>
    <tr>
      <th>505</th>
      <td>Yayla Agro Gıda</td>
      <td>14801.8</td>
    </tr>
    <tr>
      <th>506</th>
      <td>Zedur Enerji</td>
      <td>1245.0</td>
    </tr>
    <tr>
      <th>507</th>
      <td>Zorlu Enerji</td>
      <td>17500.0</td>
    </tr>
    <tr>
      <th>508</th>
      <td>Ziraat GYO</td>
      <td>21919.2</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 2 columns</p>
</div>



#### **5.3.3 Belirli Bir Satır ve Sütun Aralığına Erişme**

"loc" ve "iloc" kullanarak aşağıdaki şekilde satır ve sütun aralığı verebiliriz.


```python
df.loc[0:4, "Hisse Adı":"Kapanış(TL)"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[0:4, 0:4]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
    </tr>
  </tbody>
</table>
</div>



#### **5.3.4 Koşullu Erişim ve Dilimleme**

"Kapanış(TL)" sütunundaki değeri 100 den büyük olan verilerin "Kod" sütunundaki karşılığını ekrana yazdıralım.


```python
df[df["Kapanış(TL)"] > 100]["Kod"]
```




    2       ADEL
    7      AGHOL
    24     ALCAR
    26     ALFAS
    36     ARCLK
           ...  
    479    UZERB
    486    VERUS
    492    YAPRK
    495    YBTAS
    503    YUNSA
    Name: Kod, Length: 73, dtype: object




```python
df[(df["Kapanış(TL)"] > 100) & (df["Piyasa Değeri(mn TL)"] > 3000)]["Kod"]
```




    2       ADEL
    7      AGHOL
    24     ALCAR
    26     ALFAS
    36     ARCLK
    39     ARMDA
    44     ASUZU
    51     AVHOL
    54     AYCES
    70     BFREN
    73     BIMAS
    89     BRSAN
    90     BRYAT
    99     CCOLA
    104    CIMSA
    105    CLEBI
    113    CVKMD
    114    CWENE
    132     DOAS
    134     DOCO
    142    ECZYT
    145    EGEEN
    148    EGPRO
    161     ERCB
    183    FROTO
    207    GUBRF
    237    INVES
    256    JANTS
    265    KCHOL
    266     KENT
    278    KMPUR
    281    KONTR
    282    KONYA
    326    MGROS
    327    MIATK
    335    MRSHL
    340    NATEN
    346    NUHCM
    355    OTKAR
    366    PAMEL
    377    PGSUS
    380    PKENT
    385    POLTK
    393    QNBFL
    413    SDTTR
    435    SRVGY
    440    TAVHL
    449    THYAO
    456    TOASO
    464    TTRAK
    475    ULUSE
    486    VERUS
    495    YBTAS
    503    YUNSA
    Name: Kod, dtype: object



* "Kapanış(TL)" değeri 100 den büyük ve "Piyasa Değeri(mn TL)" 30000 de büyük olan verilerin "Kod" sütunundaki karşılıkları.


```python
df[(df["Kapanış(TL)"] > 100) & (df["Piyasa Değeri(mn TL)"] > 30000)]["Kod"]
```




    36     ARCLK
    73     BIMAS
    89     BRSAN
    90     BRYAT
    99     CCOLA
    132     DOAS
    134     DOCO
    183    FROTO
    207    GUBRF
    237    INVES
    265    KCHOL
    266     KENT
    281    KONTR
    326    MGROS
    377    PGSUS
    440    TAVHL
    449    THYAO
    456    TOASO
    464    TTRAK
    Name: Kod, dtype: object



### **5.4 Sütuna Ait Değerleri Saydırma: value_counts()**

Pandas'ın value_counts() yöntemi, bir sütundaki benzersiz değerleri ve her bir değerin kaç kez tekrarlandığını saymak için kullanılır. Bu yöntem, veri setindeki dağılımı anlamak için sıklıkla kullanılır.

* "Sektör" sütununu seçip her bir sektörden kaç adet bulunduğunu hesaplayalım.


```python
df["Sektör"].value_counts()
```




    Sektör
    GYO                           41
    Elektrik                      36
    Gıda                          33
    Holdingler                    32
    Tekstil Entegre               25
    Teknoloji                     17
    Turizm                        16
    İnşaat Malzemeleri            16
    Kimyasal Ürün                 16
    Yatırım Ortaklıkları          16
    Çimento                       15
    Bankacılık                    15
    Kağıt Ürünleri                14
    Perakande - Ticaret           13
    Sağlık ve İlaç                12
    Demir-Çelik Temel             12
    Aracı Kurumlar                11
    Otomotiv Parçası              10
    Dayanıklı Tüketim             10
    Fin.Kiralama ve Faktoring      9
    Meşrubat / İçecek              9
    Medya                          8
    Demir-Çelik Döküm              8
    Otomotiv                       8
    Elektrik Makinları Üretimi     7
    Bilgisayar Toptancılığı        7
    Ulaştırma-Lojistik             7
    İnşaat- Taahhüt                6
    Mobilya                        6
    Madencilik                     6
    Sigorta                        6
    Petrol                         6
    Diğer                          5
    Boya                           5
    Havayolları ve Hizm.           4
    Seramik                        4
    Deri Giyim                     4
    İletişim                       4
    Spor                           4
    Tarım Kimyasalları             4
    Endüstriyel Tekstil            4
    İletişim Cihazları             3
    Pazarlama                      3
    Kırtasiye                      2
    Otomotiv Lastiği               2
    Hayvancılık                    2
    Savunma                        2
    Kablo                          2
    Eğlence Hizmetleri             1
    Cam                            1
    Name: count, dtype: int64



## **6) İndex İşlemleri**


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx')
```

###  **6.1. İndeks nedir?**


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AEFES</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



Sol tarafta bir sütunmuş gibi görünen 0, 1, 2, ... değerleri indekstir. İndeksler, bir numaralandırma veya etiketleme mekanizmasıdır. Örneğin, bir liste içindeki elemanların her biri bir indeks değerine sahiptir ve bu indeksler kullanılarak elemanlara erişebiliriz. Örneğimizdeki veri çerçevesinde indeks, satırları etiketlemek veya numaralandırmak için kullanılır. Varsayılan olarak, veri çerçevesinin indeksi sıfırdan başlayan tam sayılarla oluşturulur. Bununla birlikte, indeksler benzersiz olmak zorunda değildir. Yani aynı indeks değeri birden fazla satıra karşılık gelebilir.

### **6.2. İndeks Ayarlama: set_index() ve index_col**

Pandas'ta, veri çerçevesindeki belirli bir sütunu indeks olarak ayarlamak için ``set_index()`` yöntemi kullanılır. Ayrıca, veri çerçevesini okurken, okunan sütunu indeks olarak belirlemek için ``index_col`` parametresi kullanılır.

#### **6.2.1 set_index()**

``set_index()`` yöntemi, belirtilen sütunu indeks olarak ayarlar. Bu, veri çerçevesindeki satırları bu sütuna göre etiketler. `inplace` parametresini "True" olarak ayarlarsak asıl veri seti üzerinde değişiklik yapabiliriz.

* "df2" adlı yeni bir değişken oluşturarak "Kod" sütununu index olarak ayarlayalım.


```python
df2 = df.set_index("Kod")
df2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



#### **6.2.2 index_col Kullanımı**

``index_col`` parametresi, veri çerçevesini okurken belirli bir sütunu indeks olarak belirlemek için kullanılır.


```python
import pandas as pd

df3 = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
df3.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3.index
```




    Index(['A1CAP', 'ACSEL', 'ADEL', 'ADESE', 'AEFES', 'AFYON', 'AGESA', 'AGHOL',
           'AGYO', 'AHGAZ',
           ...
           'YGYO', 'YKBNK', 'YKSLN', 'YONGA', 'YUNSA', 'YYAPI', 'YYLGD', 'ZEDUR',
           'ZOREN', 'ZRGYO'],
          dtype='object', name='Kod', length=509)



### **6.3 İndeks Aracılığıyla Erişim: loc**

Pandas'ta, veri çerçevesindeki satırlara ve sütunlara indeksler aracılığıyla erişmek için ``loc`` yöntemi kullanılır. ``loc``, indeks etiketlerini kullanarak belirli bir satır veya sütunun değerlerine erişmemizi sağlar.

- ``loc`` ile "THYAO" indeksine ulaşalım. Aslında burada iloc ile loc'un ayrımı daha net görmüş olacağız.


```python
df3.loc["THYAO"]
```




    Hisse Adı                    Türk Hava Yolları
    Sektör                    Havayolları ve Hizm.
    Kapanış(TL)                              216.6
    Piyasa Değeri(mn TL)                  298908.0
    Piyasa Değeri(mn $)                    11455.9
    Halka AçıklıkOranı (%)                    50.4
    Sermaye(mn TL)                          1380.0
    Name: THYAO, dtype: object



* Aynı indexin "Piyasa Değeri(mn TL)" değerine bakalım.


```python
df3.loc["THYAO", "Piyasa Değeri(mn TL)"]
```




    298908.0



### **6.4 İndeks Sıfırlama: reset_index()**

Pandas'ta, ``reset_index()`` yöntemi veri çerçevesinin indeksini sıfırlamak için kullanılır. Bu işlem, mevcut indeksi sıfırlar ve bir dizi ardışık sayıyı yeni indeks olarak atar.

* İndexi "kod" sütunu olarak ayarlamıştık. Varsayılan index değerine geri döndürelim. 


```python
df3.reset_index(inplace=True)
df3.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AEFES</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



### **6.5. İndekslerin Sıralanması: sort_index()**

Pandas'ta, veri çerçevesindeki indekslerin sıralanması için sort_index() yöntemi kullanılır. Bu yöntem, indekslerin sıralanmasını belirli bir sıra veya kriter doğrultusunda gerçekleştirir.

Artan sıraya göre aşağıdaki gibi sıralayabiliriz. Azalan sıraya göre sıralamak için `ascending` parametresini "False" olarak belirtmeliyiz.


```python
df.sort_index().head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1CAP</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ACSEL</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ADEL</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ADESE</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AEFES</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_index(ascending=False).head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>508</th>
      <td>ZRGYO</td>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
    <tr>
      <th>507</th>
      <td>ZOREN</td>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>506</th>
      <td>ZEDUR</td>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>505</th>
      <td>YYLGD</td>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>504</th>
      <td>YYAPI</td>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.reset_index(inplace=True)
```

## **7) Filtreleme**

Pandas'ta, veri çerçevesinden belirli bir koşula veya kriterlere uyan verileri seçme işlemine "filtreleme" denir. Bu işlem, veri setinden istenmeyen verileri kaldırmak veya belirli bir şartı sağlayan verileri seçmek için kullanılır.

### **7.1 Tekli Filtreleme: İç içe ve loc**

Pandas'ta, tekli filtreme yapmak için genellikle iç içe geçmiş koşullar veya loc kullanılır. Bu yöntemlerle, birden fazla koşulu tek bir ifadeyle birleştirebiliriz.

* "Sektör" sütununun "Bankacılık" olduğu değerleri filtreleyelim.


```python
df[df["Sektör"] == "Bankacılık"].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Kod</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>AKBNK</td>
      <td>Akbank</td>
      <td>Bankacılık</td>
      <td>20.46</td>
      <td>106392.0</td>
      <td>4077.6</td>
      <td>51.8</td>
      <td>5200.0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>23</td>
      <td>ALBRK</td>
      <td>Albaraka Türk</td>
      <td>Bankacılık</td>
      <td>3.10</td>
      <td>7750.0</td>
      <td>297.0</td>
      <td>38.4</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>184</th>
      <td>184</td>
      <td>GARAN</td>
      <td>Garanti Bankası</td>
      <td>Bankacılık</td>
      <td>33.10</td>
      <td>139020.0</td>
      <td>5328.0</td>
      <td>14.0</td>
      <td>4200.0</td>
    </tr>
    <tr>
      <th>210</th>
      <td>210</td>
      <td>HALKB</td>
      <td>Halkbank</td>
      <td>Bankacılık</td>
      <td>13.08</td>
      <td>93976.9</td>
      <td>3601.7</td>
      <td>8.5</td>
      <td>7184.8</td>
    </tr>
    <tr>
      <th>221</th>
      <td>221</td>
      <td>ICBCT</td>
      <td>ICBC Turkey Bank</td>
      <td>Bankacılık</td>
      <td>8.56</td>
      <td>7361.6</td>
      <td>282.1</td>
      <td>7.2</td>
      <td>860.0</td>
    </tr>
  </tbody>
</table>
</div>



* "Sektör" değeri "Bankacılık" olan verilerin "Kod" sütunundaki değerlerini yazdıralım.


```python
df[df["Sektör"] == "Bankacılık"]["Kod"].head()
```




    10     AKBNK
    23     ALBRK
    184    GARAN
    210    HALKB
    221    ICBCT
    Name: Kod, dtype: object




```python
df.set_index("Kod", inplace=True)
```

* ``loc`` yöntemiyle de tekli filtreme yapabiliriz. "Sektör" değeri "Bankacılık olan verilerin "Halka AçıklıkOranı (%)" değerlerini yazdıralım.


```python
df.loc[df["Sektör"] == "Bankacılık", "Halka AçıklıkOranı (%)"]
```




    Kod
    AKBNK    51.8
    ALBRK    38.4
    GARAN    14.0
    HALKB     8.5
    ICBCT     7.2
    ISATR    23.9
    ISBTR    25.7
    ISCTR    32.6
    ISKUR    28.7
    KLNMA     0.9
    QNBFB     0.1
    SKBNK    48.8
    TSKB     38.8
    VAKBN     6.1
    YKBNK    32.0
    Name: Halka AçıklıkOranı (%), dtype: float64



### **7.2. Çoklu Filtreleme: &, | ve isin()**

Pandas'ta, çoklu filtreme işlemleri için ``&`` (ve), ``|`` (veya) operatörleri ve ``isin()`` yöntemi kullanılır. Bu yöntemlerle birden fazla koşulu birleştirebiliriz ve istenilen verileri seçebiliriz.

#### **7.2.1 Mantıksal Operatörler**

Birden fazla filtreleme yapmak istediğimizde mantıksal operatörleri kullanabiliriz.

* Örneğin, hem Sektör sütunundan Bankacılık değerini hem de Halka AçıklıkOranı (%) sütunundan 10'den büyük olanları alalım ve Hisse Adı sütunundaki değerleri getirelim.


```python
df.loc[(df["Sektör"] == "Bankacılık") & (df["Halka AçıklıkOranı (%)"] > 10), "Hisse Adı"]
```




    Kod
    AKBNK                Akbank
    ALBRK         Albaraka Türk
    GARAN       Garanti Bankası
    ISATR        İş Bankası (A)
    ISBTR        İş Bankası (B)
    ISCTR        İş Bankası (C)
    ISKUR     İş Bankası Kurucu
    SKBNK             Şekerbank
    TSKB                   TSKB
    YKBNK    Yapı Kredi Bankası
    Name: Hisse Adı, dtype: object



* Burada, her bir filtreleme işlemini parantez içerisine aldık. Örnekte, ve anlamına gelen & operatörünü kullandık. Bir de veya anlamına gelen | operatörünü kullanalım.


```python
df.loc[(df['Sektör'] == 'Bankacılık') | (df['Halka AçıklıkOranı (%)'] > 50), 'Hisse Adı']
```




    Kod
    ACSEL    Acıselsan Acıpayam Selüloz
    ADESE                     Adese AVM
    AKBNK                        Akbank
    AKSUE                   Aksu Enerji
    AKYHO       Akdeniz Yatırım Holding
                        ...            
    YESIL         Yeşil Yatırım Holding
    YGGYO                Yeni Gimat GYO
    YGYO                      Yeşil GYO
    YKBNK            Yapı Kredi Bankası
    YYAPI                    Yesil Yapi
    Name: Hisse Adı, Length: 165, dtype: object



* `&` kullandığımız örnekte elde ettiğimiz verinin tam tersini elde etmek için başına ``~`` işareti koyalım. Elde edeceğimiz çıktı "Sektör" değeri "Bankacılık" olmayan ve "Halka AçıklıkOranı (%)" değeri 10 dan küçük olan veriler olacaktır.


```python
df.loc[~(df['Sektör'] == 'Bankacılık') & ~(df['Halka AçıklıkOranı (%)'] > 10), 'Hisse Adı']
```




    Kod
    AKMGY                     Akmerkez GYO
    ARMDA                Armada Bilgisayar
    AYCES                 Altınyunus Çesme
    BANVT                           Banvit
    BASCM    Baştaş Başkent Çimento Sanayi
    CLEBI                           Çelebi
    CMENT                         Çimentaş
    DAPGM                  Dap Gayrimenkul
    DGGYO                     Dogus GE GYO
    DOKTA                Döktaş Dökümcülük
    ENKAI                      Enka İnşaat
    GARFA           Garanti BBVA Faktoring
    ISDMR           İskenderun Demir Çelik
    KENT                         Kent Gıda
    MRSHL                         Marshall
    QNBFL             QNB Finans Fin. Kir.
    RAYSG                      Ray Sigorta
    SNPAM                   Sönmez Pamuklu
    SONME                  Sönmez Filament
    TBORG                           Tuborg
    UFUK          Ufuk Yat.Yön.ve Gay. AŞ.
    ULUSE                  Ulusoy Elektrik
    YBTAS         Yibitaş İnş. Malzemeleri
    Name: Hisse Adı, dtype: object



#### **7.2.2 isin() Kullanımı**

``isin()`` yöntemi, bir sütunun belirli değerlere sahip olup olmadığını kontrol eder.


```python
df_sektor = df.loc[df["Sektör"].isin(['GYO','Bankacılık'])]
df_sektor.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AGYO</th>
      <td>8</td>
      <td>Atakule GYO</td>
      <td>GYO</td>
      <td>5.41</td>
      <td>1424.7</td>
      <td>54.6</td>
      <td>18.3</td>
      <td>263.3</td>
    </tr>
    <tr>
      <th>AKBNK</th>
      <td>10</td>
      <td>Akbank</td>
      <td>Bankacılık</td>
      <td>20.46</td>
      <td>106392.0</td>
      <td>4077.6</td>
      <td>51.8</td>
      <td>5200.0</td>
    </tr>
    <tr>
      <th>AKFGY</th>
      <td>13</td>
      <td>Akfen GYO</td>
      <td>GYO</td>
      <td>4.65</td>
      <td>6045.0</td>
      <td>231.7</td>
      <td>44.5</td>
      <td>1300.0</td>
    </tr>
    <tr>
      <th>AKMGY</th>
      <td>16</td>
      <td>Akmerkez GYO</td>
      <td>GYO</td>
      <td>83.40</td>
      <td>3107.8</td>
      <td>119.1</td>
      <td>8.9</td>
      <td>37.3</td>
    </tr>
    <tr>
      <th>AKSGY</th>
      <td>19</td>
      <td>Akis GYO</td>
      <td>GYO</td>
      <td>6.21</td>
      <td>4999.1</td>
      <td>191.6</td>
      <td>44.7</td>
      <td>805.0</td>
    </tr>
  </tbody>
</table>
</div>



### **7.3 String İçerenleri Filtreleme: str.contains()**

Pandas'ta, bir sütunun içinde belirli bir string'i içeren değerleri seçmek için ``str.contains()`` yöntemi kullanılır. Bu yöntem, veri çerçevesindeki string değerler arasında arama yapmayı sağlar.

* **Hisse Adı** sütununda sadece **Enerji** içerenleri filtreleyelim. Bunun için bir string'i içerip içermediği kontrolü yapmış olacağız.

* İhtiyacımız olmamasına rağmen na parametresini False olacak şekilde ekledik. İlgili sütunda NA / NaN içerdiğini varsayalım. Bu durumda kodu çalıştırdığımızda ValueError: Cannot mask with non-boolean array containing NA / NaN values hatası alırdık. na=False olarak ayarlandığında, contains() fonksiyonu eksik değerleri içeren satırları dikkate almadan sadece Enerji kelimesini içeren satırları filtrelemek için kullanılır. Yani, Hisse Adı sütununda Enerji kelimesini içeren satırları seçerken eksik değerleri göz ardı eder.


```python
df_filtre_enerji = df[df["Hisse Adı"].str.contains("Enerji", na=False)]
df_filtre_enerji.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AKFYE</th>
      <td>14</td>
      <td>Akfen Yenilenebilir Enerji</td>
      <td>Elektrik</td>
      <td>11.99</td>
      <td>12182.2</td>
      <td>466.9</td>
      <td>30.7</td>
      <td>1016.0</td>
    </tr>
    <tr>
      <th>AKSEN</th>
      <td>18</td>
      <td>Aksa Enerji</td>
      <td>Elektrik</td>
      <td>34.86</td>
      <td>42750.2</td>
      <td>1638.4</td>
      <td>20.6</td>
      <td>1226.3</td>
    </tr>
    <tr>
      <th>AKSUE</th>
      <td>20</td>
      <td>Aksu Enerji</td>
      <td>Elektrik</td>
      <td>51.95</td>
      <td>1714.4</td>
      <td>65.7</td>
      <td>81.0</td>
      <td>33.0</td>
    </tr>
    <tr>
      <th>ALMAD</th>
      <td>30</td>
      <td>Altınyağ Madencilik ve Enerji</td>
      <td>Madencilik</td>
      <td>5.69</td>
      <td>1564.8</td>
      <td>60.0</td>
      <td>65.3</td>
      <td>275.0</td>
    </tr>
    <tr>
      <th>ARASE</th>
      <td>35</td>
      <td>Doğu Aras Enerji</td>
      <td>Elektrik</td>
      <td>51.20</td>
      <td>12800.0</td>
      <td>490.6</td>
      <td>17.5</td>
      <td>250.0</td>
    </tr>
    <tr>
      <th>ASTOR</th>
      <td>43</td>
      <td>Astor Enerji</td>
      <td>Elektrik Makinları Üretimi</td>
      <td>77.85</td>
      <td>77694.3</td>
      <td>2977.7</td>
      <td>20.7</td>
      <td>998.0</td>
    </tr>
    <tr>
      <th>AYDEM</th>
      <td>55</td>
      <td>Aydem Enerji</td>
      <td>Elektrik</td>
      <td>16.14</td>
      <td>11378.7</td>
      <td>436.1</td>
      <td>15.7</td>
      <td>705.0</td>
    </tr>
    <tr>
      <th>AYEN</th>
      <td>56</td>
      <td>Ayen Enerji</td>
      <td>Elektrik</td>
      <td>34.00</td>
      <td>9435.0</td>
      <td>361.6</td>
      <td>16.9</td>
      <td>277.5</td>
    </tr>
    <tr>
      <th>BIOEN</th>
      <td>74</td>
      <td>Biotrend Enerji</td>
      <td>Elektrik</td>
      <td>15.40</td>
      <td>7700.0</td>
      <td>295.1</td>
      <td>37.8</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>CONSE</th>
      <td>108</td>
      <td>Consus Enerji</td>
      <td>Elektrik</td>
      <td>6.93</td>
      <td>2671.5</td>
      <td>102.4</td>
      <td>32.0</td>
      <td>385.5</td>
    </tr>
  </tbody>
</table>
</div>



Sadece ilgilendiğimiz **Hisse Adı** sütununu alalım.


```python
df_filtre_enerji = df.loc[df["Hisse Adı"].str.contains("Enerji", na=False), "Hisse Adı"]
df_filtre_enerji
```




    Kod
    AKFYE        Akfen Yenilenebilir Enerji
    AKSEN                       Aksa Enerji
    AKSUE                       Aksu Enerji
    ALMAD     Altınyağ Madencilik ve Enerji
    ARASE                  Doğu Aras Enerji
    ASTOR                      Astor Enerji
    AYDEM                      Aydem Enerji
    AYEN                        Ayen Enerji
    BIOEN                   Biotrend Enerji
    CONSE                     Consus Enerji
    CWENE                         Cw Enerji
    ENJSA                   Enerjisa Enerji
    EUPWR                  Europower Enerji
    GWIND                Galata Wind Enerji
    HUNER                        Hun Enerji
    IEYHO    Işıklar Enerji ve Yapı Holding
    IPEKE                       İpek Enerji
    KARYE        Kartal Yenilenebili Enerji
    MAGEN                     Margün Enerji
    MANAS             Manas Enerji Yönetimi
    NATEN      Naturel Yenilenebilir Enerji
    ORGE               ORGE Enerji Elektrik
    SAYAS          Say Yenilenebilir Enerji
    SMRTG              Smart Güneş Enerjisi
    YAYLA        Yayla Enerji Uretim Turizm
    ZEDUR                      Zedur Enerji
    ZOREN                      Zorlu Enerji
    Name: Hisse Adı, dtype: object



## 8) **Sütun ve Satır Güncelleme**


```python
import pandas as pd
df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



### **8.1 Sütun Güncelleme: columns, List Comprehension, str.replace(), rename**

#### **8.1.1 columns Kullanımı**

``columns`` özelliği, mevcut sütun isimlerini güncellemek için kullanılır.


```python
df.columns = [
    'HisseAdi',
    'Sektor',
    'KapanisTL',
    'PiyasaDegeriMnTL',
    'PiyasaDegeriMnUSD',
    'HalkaAciklikOraniYuzde',
    'SermayeMnTL'
]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>HisseAdi</th>
      <th>Sektor</th>
      <th>KapanisTL</th>
      <th>PiyasaDegeriMnTL</th>
      <th>PiyasaDegeriMnUSD</th>
      <th>HalkaAciklikOraniYuzde</th>
      <th>SermayeMnTL</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



#### **8.1.2 List Comprehension Kullanımı**

List comprehension kullanarak sütun isimlerini güncellemek de mümkündür.

* Aşağıdaki kod, bir Pandas DataFrame'in sütun isimlerini büyük harflere dönüştürmek için kullanılan bir dizi ifadedir. Kod, list comprehension yöntemini kullanarak, DataFrame'in sütunlarını tek tek dolaşarak her bir sütunun ismini büyük harflere dönüştürür ve bu dönüşüm sonucunda oluşan yeni sütun isimlerini DataFrame'in sütunlarına atar.


```python
df.columns = [sutun.upper() for sutun in df.columns]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>HISSEADI</th>
      <th>SEKTOR</th>
      <th>KAPANISTL</th>
      <th>PIYASADEGERIMNTL</th>
      <th>PIYASADEGERIMNUSD</th>
      <th>HALKAACIKLIKORANIYUZDE</th>
      <th>SERMAYEMNTL</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



#### **8.1.3 str.replace() Kullanımı**

``str.replace()`` yöntemi, sütun değerlerini dönüştürmek için kullanılabilir.

* **USD** içeren sütunları **$** ile değiştirelim.


```python
df.columns = df.columns.str.replace("USD", "$")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>HISSEADI</th>
      <th>SEKTOR</th>
      <th>KAPANISTL</th>
      <th>PIYASADEGERIMNTL</th>
      <th>PIYASADEGERIMN$</th>
      <th>HALKAACIKLIKORANIYUZDE</th>
      <th>SERMAYEMNTL</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



* Sütun isimlerini list comprehension kullanarak tekrar küçük yapalım.


```python
df.columns = [sutun.lower() for sutun in df.columns]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hisseadi</th>
      <th>sektor</th>
      <th>kapanistl</th>
      <th>piyasadegerimntl</th>
      <th>piyasadegerimn$</th>
      <th>halkaaciklikoraniyuzde</th>
      <th>sermayemntl</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



#### **8.1.4 rename() Kullanımı**

``rename(``) yöntemi, belirli sütunların adlarını yeniden adlandırmak için kullanılır.


```python
df.rename(columns={
    'hisseadi':'HisseAdi',
    'sektor':'Sektor',
    'kapanistl':'KapanisTL',
    'piyasadegerimntl':'PiyasaDegeriMnTL',
    'piyasadegerimn$':'PiyasaDegeriMnUSD',
    'halkaaciklikoraniyuzde':'HalkaAciklikOraniYuzde',
    'sermayemntl':'SermayeMnTL'
}, inplace=True)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>HisseAdi</th>
      <th>Sektor</th>
      <th>KapanisTL</th>
      <th>PiyasaDegeriMnTL</th>
      <th>PiyasaDegeriMnUSD</th>
      <th>HalkaAciklikOraniYuzde</th>
      <th>SermayeMnTL</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



### **8.2 Satır Güncelleme: loc, at, str.lower(), apply(), applymap(), lambda, map() ve replace()**

Pandas'ta, veri çerçevesindeki satırları güncellemek için çeşitli yöntemler bulunmaktadır. Bu yöntemlerle, mevcut değerleri değiştirebilir veya yeni değerler ekleyebiliriz.


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



#### **8.2.1 loc Kullanımı**

``loc`` yöntemi, belirli satırları ve sütunları indeksleme ve güncelleme için kullanılır.

* **A1CAP** etiketine sahip satırdaki bilgileri güncelleyelim.


```python
df.loc["A1CAP"] = ['A1 Capital (Test)','Aracı Kurumlar (Test)',26.80,3618.0,138.7,25.9,135]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital (Test)</td>
      <td>Aracı Kurumlar (Test)</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



* Burada ilgili satırdaki bazı sütunlara denk gelen değerleri güncelledik. Eğer çok daha fazla sütun olsaydı tek tek hepsini yazmak zor olurdu. 

* Bilgisini değiştirdiğimiz Hisse Adı ve Sektör sütunlarına ait değerleri eski haline getirelim.


```python
df.loc["A1CAP", ["HisseAdi", "Sektör"]] = ['A1 Capital','Aracı Kurumlar']
df.head()
```

    C:\Users\Yusuf Altuntaş\AppData\Local\Temp\ipykernel_32428\1369592462.py:1: FutureWarning: Setting an item of incompatible dtype is deprecated and will raise in a future error of pandas. Value 'A1 Capital' has dtype incompatible with float64, please explicitly cast to a compatible dtype first.
      df.loc["A1CAP", ["HisseAdi", "Sektör"]] = ['A1 Capital','Aracı Kurumlar']
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital (Test)</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



#### **8.2.2 at Kullanımı**

`at` yöntemi, belirli bir hücreyi güncellemek için kullanılır.


```python
df.at['A1CAP', 'Hisse Adı'] = 'A1 Capital Test'
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital Test</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



* Bir filtreleme sonrası da tek bir hücre için güncelleme yapılabilir.


```python
df.loc[df["Sektör"] == "Bankacılık", "HalkaAciklikOraniYuzde"] = 0
df.loc[df['Sektör'] == 'Bankacılık', 'HalkaAciklikOraniYuzde']
```




    Kod
    AKBNK    0.0
    ALBRK    0.0
    GARAN    0.0
    HALKB    0.0
    ICBCT    0.0
    ISATR    0.0
    ISBTR    0.0
    ISCTR    0.0
    ISKUR    0.0
    KLNMA    0.0
    QNBFB    0.0
    SKBNK    0.0
    TSKB     0.0
    VAKBN    0.0
    YKBNK    0.0
    Name: HalkaAciklikOraniYuzde, dtype: float64



#### **8.2.3 Çoklu Satır Güncellemesi(str.lower(), apply() ve lambda ve map() ve replace() fonksiyonları)**

Çoklu satır güncellemesi yapmak istediğimiz zaman birkaç farklı yolu kullanabiliriz. 


##### **str.lower() Kullanımı**

* Örneğin, Hisse Adı sütunundaki tüm değerleri küçük yapalım. Bunun için str.lower() fonksiyonunu kullanabiliriz.


```python
df["Hisse Adı"] = df["Hisse Adı"].str.lower()
df["Hisse Adı"]
```




    Kod
    A1CAP               a1 capital test
    ACSEL    acıselsan acıpayam selüloz
    ADEL                adel kalemcilik
    ADESE                     adese avm
    AEFES                  anadolu efes
                        ...            
    YYAPI                    yesil yapi
    YYLGD               yayla agro gıda
    ZEDUR                  zedur enerji
    ZOREN                  zorlu enerji
    ZRGYO                    ziraat gyo
    Name: Hisse Adı, Length: 509, dtype: object



##### **apply() Kullanımı**

* İkinci bir yol olan apply() ile Hisse Adı sütunundaki tüm değerleri büyük harfli yapalım. Bunun için önce bir fonksiyon yazıp ardından bu fonksiyonu apply() ile uygulayacağız.


```python
def hisse_adi_guncelle(hisse_Adi):
    return hisse_Adi.upper()

df["Hisse Adı"] = df["Hisse Adı"].apply(hisse_adi_guncelle)
df["Hisse Adı"]
```




    Kod
    A1CAP               A1 CAPITAL TEST
    ACSEL    ACISELSAN ACIPAYAM SELÜLOZ
    ADEL                ADEL KALEMCILIK
    ADESE                     ADESE AVM
    AEFES                  ANADOLU EFES
                        ...            
    YYAPI                    YESIL YAPI
    YYLGD               YAYLA AGRO GIDA
    ZEDUR                  ZEDUR ENERJI
    ZOREN                  ZORLU ENERJI
    ZRGYO                    ZIRAAT GYO
    Name: Hisse Adı, Length: 509, dtype: object



##### **apply() ve lambda Kullanımı**

* Üçüncü bir yol olan apply() ve lambda ile Hisse Adı sütunundaki tüm değerlerin yalnızca ilk harflerini büyük bırakalım.


```python
df['Hisse Adı'] = df['Hisse Adı'].apply(lambda x: x.capitalize())
df["Hisse Adı"]
```




    Kod
    A1CAP               A1 capital test
    ACSEL    Aciselsan acipayam selüloz
    ADEL                Adel kalemcilik
    ADESE                     Adese avm
    AEFES                  Anadolu efes
                        ...            
    YYAPI                    Yesil yapi
    YYLGD               Yayla agro gida
    ZEDUR                  Zedur enerji
    ZOREN                  Zorlu enerji
    ZRGYO                    Ziraat gyo
    Name: Hisse Adı, Length: 509, dtype: object



##### **map() ve lambda Kullanımı**

* Dördüncü bir yol olan map() ve lambda ile Hisse Adı ve Sektör sütunlarındaki harfleri küçük yapalım.


```python
df[["Hisse Adı", "Sektör"]] = df[["Hisse Adı", "Sektör"]].map(lambda x:x.lower())
df[["Hisse Adı", "Sektör"]].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>a1 capital test</td>
      <td>aracı kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>aciselsan acipayam selüloz</td>
      <td>kimyasal ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>adel kalemcilik</td>
      <td>kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>adese avm</td>
      <td>perakande - ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>anadolu efes</td>
      <td>meşrubat / i̇çecek</td>
    </tr>
  </tbody>
</table>
</div>



##### **map() ve replace Yöntemi**

* Beşinci bir yol olan map() veya replace() ile seriler üzerinde güncelleme işlemleri yapabiliriz.


```python
df["Hisse Adı"].map({'a1 capital test':'a1 capital'})
```




    Kod
    A1CAP    a1 capital
    ACSEL           NaN
    ADEL            NaN
    ADESE           NaN
    AEFES           NaN
                ...    
    YYAPI           NaN
    YYLGD           NaN
    ZEDUR           NaN
    ZOREN           NaN
    ZRGYO           NaN
    Name: Hisse Adı, Length: 509, dtype: object



* Ancak map() yönteminde eşleştirme sözlüğünde yer almayan değerler dönüşüm sırasında NaN olarak kabul edilir. Bu noktada replace() fonksiyonunu kullanabiliriz.


```python
df["Hisse Adı"].replace({'a1 capital test':'a1 capital'})
```




    Kod
    A1CAP                    a1 capital
    ACSEL    aciselsan acipayam selüloz
    ADEL                adel kalemcilik
    ADESE                     adese avm
    AEFES                  anadolu efes
                        ...            
    YYAPI                    yesil yapi
    YYLGD               yayla agro gida
    ZEDUR                  zedur enerji
    ZOREN                  zorlu enerji
    ZRGYO                    ziraat gyo
    Name: Hisse Adı, Length: 509, dtype: object



## **9) Sütun ve Satır Ekleme ve Kaldırma**


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>



### **9.1 Sütun Ekleme ve Kaldırma: birleştirme, drop(), str.split(), assign(), merge(), join()**

#### **9.1.1 Sütunların Birleştirilmesi**

Pandas'ta, veri çerçevesindeki mevcut sütunlardan alınan değerlerin birleştirilerek yeni bir sütun oluşturulması işlemine "sütunların birleştirilmesi" denir. Bu işlem, genellikle farklı sütunlardaki bilgilerin birleştirilerek daha anlamlı veya yeni bir bilgi elde etmek amacıyla yapılır. Pandas'ta bu işlem, mevcut sütunlardaki değerlerin toplanması, birleştirilmesi veya işaretlerle ayrılması gibi yöntemlerle gerçekleştirilebilir

* Sütunların birleştirilmesi işlemi, mevcut sütunlardaki değerlerin belirli bir işaretle veya metinle birleştirilerek yeni bir sütun oluşturulmasıdır. Örneğin, **Hisse Adı** ve **Sektör** sütunlarındaki değerlerin "@" işaretiyle birleştirilerek yeni bir **HisseAdi@Sektor** sütunu oluşturalım.


```python
df["HisseAdi@Sektor"] = df["Hisse Adı"] + "@" + df["Sektör"]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi@Sektor</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital@Aracı Kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>Acıselsan Acıpayam Selüloz@Kimyasal Ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>Adel Kalemcilik@Kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>Adese AVM@Perakande - Ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>Anadolu Efes@Meşrubat / İçecek</td>
    </tr>
  </tbody>
</table>
</div>



#### **9.1.2 drop() Yöntemi**

``drop()`` yöntemi, belirli sütunları veya satırları kaldırmak için kullanılır.

* **Hisse Adı** ve **Sektör** sütunlarına ihtiyacımız olmadığını düşünelim. Bunları drop() yardımıyla kaldırabiliriz. Değişiklikleri de aynı veri çerçevesine inplace parametresini True yapıp kaydedelim.


```python
df.drop(columns=["Hisse Adı", "Sektör"], inplace=True)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi@Sektor</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital@Aracı Kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>Acıselsan Acıpayam Selüloz@Kimyasal Ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>Adel Kalemcilik@Kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>Adese AVM@Perakande - Ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>Anadolu Efes@Meşrubat / İçecek</td>
    </tr>
  </tbody>
</table>
</div>



#### **9.1.3 str.split() Kullanımı**

``str.split()`` yöntemi, bir sütunu belirli bir ayırıcıya göre bölerek yeni sütunlar oluşturmak için kullanılır. 

* Kaldırdığımız **Hisse Adı** ve **Sektör** sütunlarını tekrar yerine koyalım. Bunun için **str.split()** fonksiyonunu kullanacağız.


```python
df["HisseAdi@Sektor"].str.split("@")
```




    Kod
    A1CAP                   [A1 Capital, Aracı Kurumlar]
    ACSEL    [Acıselsan Acıpayam Selüloz, Kimyasal Ürün]
    ADEL                    [Adel Kalemcilik, Kırtasiye]
    ADESE               [Adese AVM, Perakande - Ticaret]
    AEFES              [Anadolu Efes, Meşrubat / İçecek]
                                ...                     
    YYAPI                  [Yesil Yapi, İnşaat- Taahhüt]
    YYLGD                        [Yayla Agro Gıda, Gıda]
    ZEDUR                       [Zedur Enerji, Elektrik]
    ZOREN                       [Zorlu Enerji, Elektrik]
    ZRGYO                              [Ziraat GYO, GYO]
    Name: HisseAdi@Sektor, Length: 509, dtype: object



* Sonucu yeni sütunlar olarak genişletelim. Bunu, **expand** parametresi ile yapacağız. ``expand=True`` argümanı, bu listeyi DataFrame olarak genişletir, yani her bir bölünmüş değeri ayrı bir sütun olarak ekler.


```python
df["HisseAdi@Sektor"].str.split("@", expand=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 2 columns</p>
</div>



* Yeni oluşan sütunları veri çerçevesine ekleyelim.


```python
df[["Hisse Adı", "Sektör"]] = df["HisseAdi@Sektor"].str.split("@", expand=True)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi@Sektor</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital@Aracı Kurumlar</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>Acıselsan Acıpayam Selüloz@Kimyasal Ürün</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>Adel Kalemcilik@Kırtasiye</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>Adese AVM@Perakande - Ticaret</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>Anadolu Efes@Meşrubat / İçecek</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
    </tr>
  </tbody>
</table>
</div>



#### **9.1.4 assign() Metodu**

``assign()`` metodu, yeni sütunlar eklemek için kullanılır. Bu metod, mevcut bir veri çerçevesine yeni sütunlar ekler ve orijinal veri çerçevesini değiştirmez.


```python
import numpy as np
import pandas as pd

# DataFrame'e yeni bir sütun ekleyelim ve sıfırları NaN ile değiştirelim
yenidf = df.assign(SermayeYüzde=df["Sermaye(mn TL)"].apply(lambda x: np.nan if x == 0 else (df["Sermaye(mn TL)"].sum() / x) * 100))

# Yeni DataFrame'i yazdıralım
yenidf
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HalkaAciklikOraniGrup</th>
      <th>SermayeYüzde</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>&lt;=50</td>
      <td>1.759824e+05</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>&gt;50</td>
      <td>2.220338e+06</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>&lt;=50</td>
      <td>1.006679e+06</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>&gt;50</td>
      <td>2.356907e+04</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>&lt;=50</td>
      <td>4.012434e+04</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
      <td>&gt;50</td>
      <td>7.385023e+04</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
      <td>&lt;=50</td>
      <td>5.027004e+04</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
      <td>&lt;=50</td>
      <td>9.503048e+05</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
      <td>&lt;=50</td>
      <td>4.751524e+03</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
      <td>&lt;=50</td>
      <td>5.061705e+03</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 9 columns</p>
</div>



#### **9.1.5 `join()` Metodu**

`join()` metodu, iki veri çerçevesini birleştirmek için kullanılır. Bu metod, sütunlar veya indeksler üzerinde birleştirme yapabilir.

**Kullanımı**

```python
DataFrame.join(other, on=None, how='left', lsuffix='', rsuffix='', sort=False)
```

- `other`: Birleştirilecek diğer veri çerçevesi.
- `on`: Birleştirme sütunu. Varsayılan olarak, indekslere göre birleştirme yapılır.
- `how`: Birleştirme türü. 'left', 'right', 'outer' veya 'inner'. Varsayılan olarak 'left'.
- `lsuffix` ve `rsuffix`: İki veri çerçevesinde aynı sütun adları varsa, eklenen soneklerin adlarını belirtmek için kullanılır.
- `sort`: Birleştirme sonucunun sıralanıp sıralanmayacağını belirtir.

**Örnek Kullanım**

```python
import pandas as pd

# İlk veri çerçevesi
data1 = {'A': [1, 2, 3],
         'B': [4, 5, 6]}
df1 = pd.DataFrame(data1)

# İkinci veri çerçevesi
data2 = {'C': [7, 8, 9],
         'D': [10, 11, 12]}
df2 = pd.DataFrame(data2)

# Birleştirme işlemi
result = df1.join(df2)

print(result)
```
---

#### **9.1.6 `merge()` Metodu**

`merge()` metodu, iki veri çerçevesini birleştirmek için kullanılır. Bu metod, sütunlar veya indeksler üzerinde birleştirme yapabilir.

**Kullanımı**

```python
pd.merge(left, right, how='inner', on=None, left_on=None, right_on=None, left_index=False, right_index=False, sort=False)
```

- `left` ve `right`: Birleştirilecek veri çerçeveleri.
- `how`: Birleştirme türü. 'left', 'right', 'outer' veya 'inner'. Varsayılan olarak 'inner'.
- `on`: Birleştirme sütunu.
- `left_on` ve `right_on`: Sol ve sağ veri çerçevelerinde birleştirme sütunlarını belirtmek için kullanılır.
- `left_index` ve `right_index`: İndekslere göre birleştirme yapılıp yapılmayacağını belirtir.
- `sort`: Birleştirme sonucunun sıralanıp sıralanmayacağını belirtir.

**Örnek Kullanım**

```python
import pandas as pd

# İlk veri çerçevesi
data1 = {'A': [1, 2, 3],
         'B': [4, 5, 6]}
df1 = pd.DataFrame(data1)

# İkinci veri çerçevesi
data2 = {'A': [1, 2, 3],
         'C': [7, 8, 9]}
df2 = pd.DataFrame(data2)

# Birleştirme işlemi
result = pd.merge(df1, df2, on='A')

print(result)
```

Yukarıdaki örneklerde, `assign()`, `join()` ve `merge()` metodları kullanılarak sütun ve satır eklemesi işlemleri gerçekleştirilmiştir. Bu metodlar, veri çerçevelerini birleştirmek ve yeni sütunlar eklemek için kullanışlı araçlardır.

### **9.2 Satır Ekleme ve Kaldırma: append(), concat() ve drop()**


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HisseAdi@Sektor</th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>A1 Capital@Aracı Kurumlar</td>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>Acıselsan Acıpayam Selüloz@Kimyasal Ürün</td>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>Adel Kalemcilik@Kırtasiye</td>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>Adese AVM@Perakande - Ticaret</td>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>Anadolu Efes@Meşrubat / İçecek</td>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
    </tr>
  </tbody>
</table>
</div>



#### **9.2.1 concat() Metodu**

Pandas'ta, concat() metodu, bir veya daha fazla veri çerçevesini birleştirmek için kullanılır. Bu metot, sütunlar veya satırlar boyunca birleştirme işlemi yapabilir ve esnek bir şekilde veri çerçevelerini bir araya getirebilir.

* İki veri çerçevesini birleştirelim. Bunun için bir veri çerçevesi daha oluşturalım. İlk veri çerçevesini de ilk hali ile kullanalım.


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")

df2 = {
    'Kod':['TST'],
    'Hisse Adı':['TEST'],
    'Sektör':['Bankacılık'],
    'Kapanış(TL)':[0],
    'Piyasa Değeri(mn TL)':[0],
    'Piyasa Değeri(mn $)':[0],
    'Halka AçıklıkOranı (%)':[0],
    'Sermaye(mn TL)':[0],
    'USDTRY':26
}

df2 = pd.DataFrame(df2)
df2.set_index("Kod", inplace=True)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>USDTRY</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>TST</th>
      <td>TEST</td>
      <td>Bankacılık</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>26</td>
    </tr>
  </tbody>
</table>
</div>



* İkinci veri çerçevesinde bir sütun fazla. Bu durumda birleştirme sırasında `ignore_index=True` parametresini kullanarak bunu görmezden geleceğiz.


```python
df3 = pd.concat([df,df2], ignore_index=True)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>USDTRY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>505</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>506</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>507</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>508</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>509</th>
      <td>TEST</td>
      <td>Bankacılık</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>26.0</td>
    </tr>
  </tbody>
</table>
<p>510 rows × 8 columns</p>
</div>



#### **9.2.2 drop() Metodu**

``drop()`` metodu, Pandas'ta veri çerçevesinden belirli satırları veya sütunları kaldırmak için kullanılır. Bu metod, orijinal veri çerçevesini değiştirmek yerine, belirtilen satırları veya sütunları kaldırılmış yeni bir veri çerçevesi döndürür.

* 509 numaralı indeksi kaldırmak istediğimizi varsayalım. Daha önce kullandığımız drop() fonksiyonunun içine index parametresini ekleyerek kaldırma işlemini gerçekleştirebiliriz.


```python
df3.drop(index=509, inplace=True)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>USDTRY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>504</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>505</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>506</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>507</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>508</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 8 columns</p>
</div>



* Yukarıda sadece bir adet indeks belirtip onu kaldırdık. Sadece **Aracı Kurumlar** içeren satırları indeks ile kaldırmak istediğimizi varsayalım. Önce koşulu belirteceğiz ardından da bu koşulun indekslerini alacağız.


```python
df3.drop(index=df3[df3["Sektör"] == "Aracı Kurumlar"].index, inplace=True)
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>USDTRY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Afyon Çimento</td>
      <td>Çimento</td>
      <td>9.33</td>
      <td>3732.0</td>
      <td>143.0</td>
      <td>48.6</td>
      <td>400.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>504</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>505</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>506</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>507</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>508</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>498 rows × 8 columns</p>
</div>



# **10) Veri Analizi**

## **10.1 Temel İstatistiksel Hesaplamalar**

Pandas, veri çerçeveleri üzerinde temel istatistiksel hesaplamaları gerçekleştirmek için bir dizi yöntem sunar. Bu yöntemlerle, veri çerçevesinin farklı sütunlarına veya satırlarına ilişkin istatistiksel özetler elde edebiliriz.

### **10.1.1 describe() Metodu**

``describe()`` yöntemi, veri çerçevesinin sayısal sütunlarına ilişkin temel istatistiksel bilgileri özetler.

İstatistiksel özet:

* count: Sütundaki non-null (boş olmayan) değerlerin sayısı.
* mean: Sütundaki değerlerin ortalaması.
* std: Sütundaki değerlerin standart sapması.
* min: Sütundaki en küçük değer.
* 25%: Alt çeyrek yüzdesi, sütundaki değerlerin %25'inin altında olan değer.
* 50%: Medyan veya ortanca, sütundaki değerlerin yarısından küçük ve yarısından büyük olan değer.
* 75%: Üst çeyrek yüzdesi, sütundaki değerlerin %75'inin altında olan değer.
* max: Sütundaki en büyük değer.


```python
df_istatiktiksel_ozet = df.drop(["Hisse Adı", "Sektör"], axis=1)
df_istatiktiksel_ozet.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>509.000000</td>
      <td>509.000000</td>
      <td>509.000000</td>
      <td>509.000000</td>
      <td>509.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2796.021513</td>
      <td>13682.732024</td>
      <td>524.398821</td>
      <td>40.691945</td>
      <td>466.750884</td>
    </tr>
    <tr>
      <th>std</th>
      <td>45015.419482</td>
      <td>35616.304707</td>
      <td>1365.022129</td>
      <td>24.011865</td>
      <td>1084.563219</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.820000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>8.760000</td>
      <td>981.600000</td>
      <td>37.600000</td>
      <td>22.400000</td>
      <td>42.800000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>22.940000</td>
      <td>2800.000000</td>
      <td>107.300000</td>
      <td>33.100000</td>
      <td>129.900000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>54.750000</td>
      <td>8760.000000</td>
      <td>335.700000</td>
      <td>54.100000</td>
      <td>375.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>968000.000000</td>
      <td>307430.500000</td>
      <td>11782.500000</td>
      <td>100.000000</td>
      <td>10000.000000</td>
    </tr>
  </tbody>
</table>
</div>



### **10.1.2 mean() Metodu**

``mean()`` yöntemi, belirli bir sütunun ortalamasını hesaplar.


```python
df["Piyasa Değeri(mn $)"].mean()
```




    524.3988212180747



### **10.1.3 median() Metodu**

``median()`` yöntemi, belirli bir sütunun medyanını hesaplar.

* **Piyasa Değeri(mn $)** sütununun medyan değerine bakalım.


```python
df["Piyasa Değeri(mn $)"].median()
```




    107.3



* **Piyasa Değeri(mn TL)** ve **Piyasa Değeri(mn $)** sütunlarının medyan değerine bakalım.


```python
df[['Piyasa Değeri(mn TL)','Piyasa Değeri(mn $)']].median()
```




    Piyasa Değeri(mn TL)    2800.0
    Piyasa Değeri(mn $)      107.3
    dtype: float64



### **10.1.4 Değerlerin Saydırılması: value_counts()**

``value_counts()`` metodu, bir Pandas Serisi veya veri çerçevesindeki benzersiz değerlerin sayısını hesaplamak için kullanılır. Bu metod, özellikle kategorik verilerin dağılımını anlamak veya bir sütundaki değerlerin frekansını bulmak için sıkça kullanılır.

* Sektör sütunundaki benzersiz değerleri saydıralım.


```python
df["Sektör"].value_counts()
```




    Sektör
    GYO                           41
    Elektrik                      36
    Gıda                          33
    Holdingler                    32
    Tekstil Entegre               25
    Teknoloji                     17
    Turizm                        16
    İnşaat Malzemeleri            16
    Kimyasal Ürün                 16
    Yatırım Ortaklıkları          16
    Çimento                       15
    Bankacılık                    15
    Kağıt Ürünleri                14
    Perakande - Ticaret           13
    Sağlık ve İlaç                12
    Demir-Çelik Temel             12
    Aracı Kurumlar                11
    Otomotiv Parçası              10
    Dayanıklı Tüketim             10
    Fin.Kiralama ve Faktoring      9
    Meşrubat / İçecek              9
    Medya                          8
    Demir-Çelik Döküm              8
    Otomotiv                       8
    Elektrik Makinları Üretimi     7
    Bilgisayar Toptancılığı        7
    Ulaştırma-Lojistik             7
    İnşaat- Taahhüt                6
    Mobilya                        6
    Madencilik                     6
    Sigorta                        6
    Petrol                         6
    Diğer                          5
    Boya                           5
    Havayolları ve Hizm.           4
    Seramik                        4
    Deri Giyim                     4
    İletişim                       4
    Spor                           4
    Tarım Kimyasalları             4
    Endüstriyel Tekstil            4
    İletişim Cihazları             3
    Pazarlama                      3
    Kırtasiye                      2
    Otomotiv Lastiği               2
    Hayvancılık                    2
    Savunma                        2
    Kablo                          2
    Eğlence Hizmetleri             1
    Cam                            1
    Name: count, dtype: int64



* **Sektör** sütunundaki değerleri saydırmıştık. Bunların yüzde paylarını **normalize** parametresini **True** yaparak alabiliriz.


```python
df["Sektör"].value_counts(normalize=True)
```




    Sektör
    GYO                           0.080550
    Elektrik                      0.070727
    Gıda                          0.064833
    Holdingler                    0.062868
    Tekstil Entegre               0.049116
    Teknoloji                     0.033399
    Turizm                        0.031434
    İnşaat Malzemeleri            0.031434
    Kimyasal Ürün                 0.031434
    Yatırım Ortaklıkları          0.031434
    Çimento                       0.029470
    Bankacılık                    0.029470
    Kağıt Ürünleri                0.027505
    Perakande - Ticaret           0.025540
    Sağlık ve İlaç                0.023576
    Demir-Çelik Temel             0.023576
    Aracı Kurumlar                0.021611
    Otomotiv Parçası              0.019646
    Dayanıklı Tüketim             0.019646
    Fin.Kiralama ve Faktoring     0.017682
    Meşrubat / İçecek             0.017682
    Medya                         0.015717
    Demir-Çelik Döküm             0.015717
    Otomotiv                      0.015717
    Elektrik Makinları Üretimi    0.013752
    Bilgisayar Toptancılığı       0.013752
    Ulaştırma-Lojistik            0.013752
    İnşaat- Taahhüt               0.011788
    Mobilya                       0.011788
    Madencilik                    0.011788
    Sigorta                       0.011788
    Petrol                        0.011788
    Diğer                         0.009823
    Boya                          0.009823
    Havayolları ve Hizm.          0.007859
    Seramik                       0.007859
    Deri Giyim                    0.007859
    İletişim                      0.007859
    Spor                          0.007859
    Tarım Kimyasalları            0.007859
    Endüstriyel Tekstil           0.007859
    İletişim Cihazları            0.005894
    Pazarlama                     0.005894
    Kırtasiye                     0.003929
    Otomotiv Lastiği              0.003929
    Hayvancılık                   0.003929
    Savunma                       0.003929
    Kablo                         0.003929
    Eğlence Hizmetleri            0.001965
    Cam                           0.001965
    Name: proportion, dtype: float64



### **10.1.5 min(), max(), sum(), std(), nlargest(), nsmallest()**

* **min():** ``min()`` metodu, bir Pandas Serisi veya veri çerçevesindeki en küçük değeri bulmak için kullanılır. Bu metod, sayısal değerlerin yanı sıra dizelerin alfabetik olarak en küçük değerini de bulabilir.

* **max():** ``max()`` metodu, bir Pandas Serisi veya veri çerçevesindeki en büyük değeri bulmak için kullanılır. min() metodu gibi, sayısal değerlerin yanı sıra dizelerin alfabetik olarak en büyük değerini de bulabilir.

* **sum():** ``sum()`` metodu, bir Pandas Serisi veya veri çerçevesindeki tüm değerlerin toplamını hesaplamak için kullanılır. Sayısal veriler için kullanıldığında, tüm değerlerin toplamını verir.

* **std():** ``std()`` metodu, bir Pandas Serisi veya veri çerçevesindeki değerlerin standart sapmasını hesaplamak için kullanılır. Standart sapma, bir veri kümesinin yayılma derecesini gösterir.

* **nlargest():** ``nlargest()`` metodu, bir Pandas Serisi veya veri çerçevesindeki en büyük n değeri döndürmek için kullanılır. Özellikle, serideki veya veri çerçevesindeki en büyük değerlere göre sıralanmış ilk n satırı döndürür.

* **nsmallest():** ``nsmallest()`` metodu, bir Pandas Serisi veya veri çerçevesindeki en küçük n değeri döndürmek için kullanılır. Özellikle, serideki veya veri çerçevesindeki en küçük değerlere göre sıralanmış ilk n satırı döndürür.

### **10.1.6 Bir Gruba Göre İstatistik: groupby(), agg(), median() ve std()**

* **Sektör** sütununa göre sektörlerin piyasa değerlerinin medyanını **Piyasa Değeri(mn $)** sütununu kullanarak alalım.


```python
df.groupby(["Sektör"])["Piyasa Değeri(mn $)"].median()
```




    Sektör
    Aracı Kurumlar                  92.90
    Bankacılık                    1200.60
    Bilgisayar Toptancılığı        180.80
    Boya                            78.20
    Cam                           5482.60
    Dayanıklı Tüketim              113.00
    Demir-Çelik Döküm               52.80
    Demir-Çelik Temel              391.50
    Deri Giyim                      32.75
    Diğer                           36.20
    Elektrik                       368.85
    Elektrik Makinları Üretimi      84.30
    Endüstriyel Tekstil            787.85
    Eğlence Hizmetleri              92.90
    Fin.Kiralama ve Faktoring      116.10
    GYO                            152.00
    Gıda                            84.20
    Havayolları ve Hizm.          2055.25
    Hayvancılık                    179.55
    Holdingler                     150.35
    Kablo                          161.90
    Kağıt Ürünleri                  73.90
    Kimyasal Ürün                   30.60
    Kırtasiye                      129.65
    Madencilik                     187.75
    Medya                           43.60
    Meşrubat / İçecek               81.20
    Mobilya                         73.30
    Otomotiv                      1313.80
    Otomotiv Lastiği               481.65
    Otomotiv Parçası               185.10
    Pazarlama                       99.30
    Perakande - Ticaret            122.90
    Petrol                         486.50
    Savunma                       2695.80
    Sağlık ve İlaç                 148.55
    Seramik                         86.50
    Sigorta                        271.85
    Spor                           198.10
    Tarım Kimyasalları            1616.05
    Teknoloji                       40.20
    Tekstil Entegre                 62.00
    Turizm                          84.95
    Ulaştırma-Lojistik             114.60
    Yatırım Ortaklıkları            13.95
    Çimento                        294.80
    İletişim                      1545.80
    İletişim Cihazları             138.00
    İnşaat Malzemeleri              54.20
    İnşaat- Taahhüt                436.15
    Name: Piyasa Değeri(mn $), dtype: float64



* **Sektör** sütununa göre sektörlerin piyasa değerlerinin medyanını **Piyasa Değeri(mn $)** sütununu kullanarak alalım. Bunun yanına bir de standart sapma ekleyelim.


```python
df.groupby(["Sektör"])["Piyasa Değeri(mn $)"].agg(["median", "std"]).head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>median</th>
      <th>std</th>
    </tr>
    <tr>
      <th>Sektör</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Aracı Kurumlar</th>
      <td>92.90</td>
      <td>290.963678</td>
    </tr>
    <tr>
      <th>Bankacılık</th>
      <td>1200.60</td>
      <td>2351.133754</td>
    </tr>
    <tr>
      <th>Bilgisayar Toptancılığı</th>
      <td>180.80</td>
      <td>158.379538</td>
    </tr>
    <tr>
      <th>Boya</th>
      <td>78.20</td>
      <td>86.639194</td>
    </tr>
    <tr>
      <th>Cam</th>
      <td>5482.60</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Dayanıklı Tüketim</th>
      <td>113.00</td>
      <td>1096.187345</td>
    </tr>
    <tr>
      <th>Demir-Çelik Döküm</th>
      <td>52.80</td>
      <td>120.470278</td>
    </tr>
    <tr>
      <th>Demir-Çelik Temel</th>
      <td>391.50</td>
      <td>1676.347230</td>
    </tr>
    <tr>
      <th>Deri Giyim</th>
      <td>32.75</td>
      <td>47.669723</td>
    </tr>
    <tr>
      <th>Diğer</th>
      <td>36.20</td>
      <td>41.722979</td>
    </tr>
  </tbody>
</table>
</div>



* Sütun isimlerini güncelleyebiliriz.


```python
df.groupby(["Sektör"])["Piyasa Değeri(mn $)"].agg(Medyan="median", StandartSapma="std").head(15)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Medyan</th>
      <th>StandartSapma</th>
    </tr>
    <tr>
      <th>Sektör</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Aracı Kurumlar</th>
      <td>92.90</td>
      <td>290.963678</td>
    </tr>
    <tr>
      <th>Bankacılık</th>
      <td>1200.60</td>
      <td>2351.133754</td>
    </tr>
    <tr>
      <th>Bilgisayar Toptancılığı</th>
      <td>180.80</td>
      <td>158.379538</td>
    </tr>
    <tr>
      <th>Boya</th>
      <td>78.20</td>
      <td>86.639194</td>
    </tr>
    <tr>
      <th>Cam</th>
      <td>5482.60</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Dayanıklı Tüketim</th>
      <td>113.00</td>
      <td>1096.187345</td>
    </tr>
    <tr>
      <th>Demir-Çelik Döküm</th>
      <td>52.80</td>
      <td>120.470278</td>
    </tr>
    <tr>
      <th>Demir-Çelik Temel</th>
      <td>391.50</td>
      <td>1676.347230</td>
    </tr>
    <tr>
      <th>Deri Giyim</th>
      <td>32.75</td>
      <td>47.669723</td>
    </tr>
    <tr>
      <th>Diğer</th>
      <td>36.20</td>
      <td>41.722979</td>
    </tr>
    <tr>
      <th>Elektrik</th>
      <td>368.85</td>
      <td>444.925170</td>
    </tr>
    <tr>
      <th>Elektrik Makinları Üretimi</th>
      <td>84.30</td>
      <td>1092.344980</td>
    </tr>
    <tr>
      <th>Endüstriyel Tekstil</th>
      <td>787.85</td>
      <td>5562.638314</td>
    </tr>
    <tr>
      <th>Eğlence Hizmetleri</th>
      <td>92.90</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Fin.Kiralama ve Faktoring</th>
      <td>116.10</td>
      <td>140.352863</td>
    </tr>
  </tbody>
</table>
</div>



### **10.1.7 Bir String İçeriğine Göre Bir İstatistik: groupby(), apply(), lambda, str.contains() ve sum()**

* **Hisse Ad**ı** sütununda **Enerji** içeren hisseleri **HalkaAciklikOraniGrup** sütununa göre saydıralım.


```python
df["HalkaAciklikOraniGrup"] = df["Halka AçıklıkOranı (%)"].apply(lambda x: ">50" if x > 50 else "<=50")

df.groupby(['HalkaAciklikOraniGrup']).apply(lambda x: x['Hisse Adı'].str.contains('Enerji').sum())
# veya
df.groupby(['HalkaAciklikOraniGrup'])['Hisse Adı'].apply(lambda x: x.str.contains('Enerji').sum())
```




    HalkaAciklikOraniGrup
    <=50    21
    >50      6
    Name: Hisse Adı, dtype: int64



## **10.2 Veri Sıralama**

1) **sort_values() Metodu:**
* Syntax: 
            ```
            DataFrame.sort_values(by, axis=0, ascending=True, inplace=False, na_position='last', ignore_index=False)
            ```
    * Parametreler:
        - **by**: Sıralama yapılacak sütunun adı veya sütunların listesi.
        - **axis**: Sıralama işleminin sütunlar (axis=0) veya satırlar (axis=1) boyunca yapılacağını belirten bir sayı veya etiket. Varsayılan değeri 0'dır.
        - **ascending**: Sıralama sırasının artan (True) veya azalan (False) olacağını belirleyen bir boolean değer. Varsayılan değeri True'dur.
        - **inplace**: Değişikliklerin orijinal DataFrame üzerinde yapılmasını sağlayan bir boolean değer. Varsayılan değeri False'dur.
        - **na_position**: NaN değerlerin nereye yerleştirileceğini belirleyen bir string. "first" veya "last" olabilir. Varsayılan değeri "last"tir.
        - **ignore_index**: Yeniden indeksleme yapılıp yapılmayacağını belirleyen bir boolean değer. Varsayılan değeri False'dur.

2) **sort_index() Metodu:**

* Syntax:
    ```
    DataFrame.sort_index(axis=0, level=None, ascending=True, inplace=False, kind='quicksort', na_position='last', sort_remaining=True, ignore_index=False)
    ```             
    * Parametreler:

        * **level**: İndekslerin hiyerarşik indekslenmesi durumunda, hangi seviyede sıralama yapılacağını belirten bir sayı veya etiket.
        * **kind**: Sıralama algoritmasını belirleyen bir string. "quicksort", "mergesort", "heapsort" veya "stable" olabilir. Varsayılan değeri "quicksort"tir.
        * **sort_remaining**: Hiçbir seviyede sıralama yapılmayan indekslerin sıralanıp sıralanmayacağını belirleyen bir boolean değer. Varsayılan değeri True'dur.

### **10.2.1 sort_values()**

* Veri çerçevesini **Piyasa Değeri(mn $)** sütununa göre sıralayalım.


```python
df.sort_values(by="Piyasa Değeri(mn $)", inplace=True)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ISKUR</th>
      <td>İş Bankası Kurucu</td>
      <td>Bankacılık</td>
      <td>968000.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>28.7</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>MMCAS</th>
      <td>MMC San.ve Tic. Yatırımlar A.Ş</td>
      <td>Ulaştırma-Lojistik</td>
      <td>4.90</td>
      <td>65.4</td>
      <td>2.5</td>
      <td>92.9</td>
      <td>13.3</td>
    </tr>
    <tr>
      <th>DIRIT</th>
      <td>Diriteks Diriliş Tekstil</td>
      <td>Tekstil Entegre</td>
      <td>7.35</td>
      <td>78.3</td>
      <td>3.0</td>
      <td>93.9</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>BRMEN</th>
      <td>Birlik Mensucat</td>
      <td>Tekstil Entegre</td>
      <td>2.17</td>
      <td>96.8</td>
      <td>3.7</td>
      <td>71.4</td>
      <td>44.6</td>
    </tr>
    <tr>
      <th>ETYAT</th>
      <td>Euro Trend Yatırım</td>
      <td>Yatırım Ortaklıkları</td>
      <td>6.43</td>
      <td>128.6</td>
      <td>4.9</td>
      <td>93.4</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>ENKAI</th>
      <td>Enka İnşaat</td>
      <td>İnşaat- Taahhüt</td>
      <td>30.16</td>
      <td>180960.0</td>
      <td>6935.4</td>
      <td>8.9</td>
      <td>6000.0</td>
    </tr>
    <tr>
      <th>KCHOL</th>
      <td>Koç Holding</td>
      <td>Holdingler</td>
      <td>108.90</td>
      <td>276159.3</td>
      <td>10584.0</td>
      <td>26.4</td>
      <td>2535.9</td>
    </tr>
    <tr>
      <th>FROTO</th>
      <td>Ford Otosan</td>
      <td>Otomotiv</td>
      <td>837.70</td>
      <td>293957.3</td>
      <td>11266.1</td>
      <td>17.8</td>
      <td>350.9</td>
    </tr>
    <tr>
      <th>THYAO</th>
      <td>Türk Hava Yolları</td>
      <td>Havayolları ve Hizm.</td>
      <td>216.60</td>
      <td>298908.0</td>
      <td>11455.9</td>
      <td>50.4</td>
      <td>1380.0</td>
    </tr>
    <tr>
      <th>SASA</th>
      <td>Sasa Polyester Sanayi A.Ş.</td>
      <td>Endüstriyel Tekstil</td>
      <td>58.05</td>
      <td>307430.5</td>
      <td>11782.5</td>
      <td>24.2</td>
      <td>5296.0</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



* Yukarıda küçükten büyüğe doğru sıraladık. Şimdi ise büyükten küçüğe doğru sıralayalım.


```python
df.sort_values(by="Piyasa Değeri(mn $)", ascending=False, inplace=True)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>SASA</th>
      <td>Sasa Polyester Sanayi A.Ş.</td>
      <td>Endüstriyel Tekstil</td>
      <td>58.05</td>
      <td>307430.5</td>
      <td>11782.5</td>
      <td>24.2</td>
      <td>5296.0</td>
    </tr>
    <tr>
      <th>THYAO</th>
      <td>Türk Hava Yolları</td>
      <td>Havayolları ve Hizm.</td>
      <td>216.60</td>
      <td>298908.0</td>
      <td>11455.9</td>
      <td>50.4</td>
      <td>1380.0</td>
    </tr>
    <tr>
      <th>FROTO</th>
      <td>Ford Otosan</td>
      <td>Otomotiv</td>
      <td>837.70</td>
      <td>293957.3</td>
      <td>11266.1</td>
      <td>17.8</td>
      <td>350.9</td>
    </tr>
    <tr>
      <th>KCHOL</th>
      <td>Koç Holding</td>
      <td>Holdingler</td>
      <td>108.90</td>
      <td>276159.3</td>
      <td>10584.0</td>
      <td>26.4</td>
      <td>2535.9</td>
    </tr>
    <tr>
      <th>ENKAI</th>
      <td>Enka İnşaat</td>
      <td>İnşaat- Taahhüt</td>
      <td>30.16</td>
      <td>180960.0</td>
      <td>6935.4</td>
      <td>8.9</td>
      <td>6000.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>ETYAT</th>
      <td>Euro Trend Yatırım</td>
      <td>Yatırım Ortaklıkları</td>
      <td>6.43</td>
      <td>128.6</td>
      <td>4.9</td>
      <td>93.4</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>BRMEN</th>
      <td>Birlik Mensucat</td>
      <td>Tekstil Entegre</td>
      <td>2.17</td>
      <td>96.8</td>
      <td>3.7</td>
      <td>71.4</td>
      <td>44.6</td>
    </tr>
    <tr>
      <th>DIRIT</th>
      <td>Diriteks Diriliş Tekstil</td>
      <td>Tekstil Entegre</td>
      <td>7.35</td>
      <td>78.3</td>
      <td>3.0</td>
      <td>93.9</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>MMCAS</th>
      <td>MMC San.ve Tic. Yatırımlar A.Ş</td>
      <td>Ulaştırma-Lojistik</td>
      <td>4.90</td>
      <td>65.4</td>
      <td>2.5</td>
      <td>92.9</td>
      <td>13.3</td>
    </tr>
    <tr>
      <th>ISKUR</th>
      <td>İş Bankası Kurucu</td>
      <td>Bankacılık</td>
      <td>968000.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>28.7</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



* **Sektör** sütununa göre artan ve **Piyasa Değeri(mn $)** sütununa göre azalan şekilde sıralayalım.


```python
df.sort_values(by=["Sektör", "Piyasa Değeri(mn $)"], ascending=[True, False], inplace=True)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ISMEN</th>
      <td>İş Yatırım</td>
      <td>Aracı Kurumlar</td>
      <td>69.35</td>
      <td>24619.3</td>
      <td>943.6</td>
      <td>29.2</td>
      <td>355.0</td>
    </tr>
    <tr>
      <th>OYYAT</th>
      <td>Oyak Yatırım</td>
      <td>Aracı Kurumlar</td>
      <td>53.20</td>
      <td>15960.0</td>
      <td>611.7</td>
      <td>30.3</td>
      <td>300.0</td>
    </tr>
    <tr>
      <th>GEDIK</th>
      <td>Gedik Yatırım</td>
      <td>Aracı Kurumlar</td>
      <td>8.97</td>
      <td>4529.9</td>
      <td>173.6</td>
      <td>14.0</td>
      <td>505.0</td>
    </tr>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>GLCVY</th>
      <td>Gelecek Varlık Yön.</td>
      <td>Aracı Kurumlar</td>
      <td>25.40</td>
      <td>3548.4</td>
      <td>136.0</td>
      <td>18.9</td>
      <td>139.7</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>BIENY</th>
      <td>Bien Yapı</td>
      <td>İnşaat- Taahhüt</td>
      <td>44.72</td>
      <td>16143.9</td>
      <td>618.7</td>
      <td>20.0</td>
      <td>361.0</td>
    </tr>
    <tr>
      <th>TKFEN</th>
      <td>Tekfen Holding</td>
      <td>İnşaat- Taahhüt</td>
      <td>39.90</td>
      <td>14763.0</td>
      <td>565.8</td>
      <td>49.4</td>
      <td>370.0</td>
    </tr>
    <tr>
      <th>YEOTK</th>
      <td>YEO Teknoloji</td>
      <td>İnşaat- Taahhüt</td>
      <td>83.30</td>
      <td>7996.8</td>
      <td>306.5</td>
      <td>30.3</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>KUYAS</th>
      <td>Kuyas Yatırım AŞ</td>
      <td>İnşaat- Taahhüt</td>
      <td>38.26</td>
      <td>3826.0</td>
      <td>146.6</td>
      <td>99.7</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



### **10.2.2 İndekse Göre Sıralama: sort_index()**

* İndekse göre artan bir şekilde sıralayalım.


```python
df.sort_index(inplace=True)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



* İndekse göre azalan bir şekilde de sıralayalım.


```python
df.sort_index(ascending=False, inplace=True)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>4.67</td>
      <td>21919.2</td>
      <td>840.1</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



### **10.2.3 Serilerin Sıralanması: sort_values()**

* **Sektör** sütununu alıp seri olacak şekilde bir sıralama yapabiliriz.


```python
df["Sektör"].sort_values()
```




    Kod
    A1CAP     Aracı Kurumlar
    BRKVY     Aracı Kurumlar
    GEDIK     Aracı Kurumlar
    GLBMD     Aracı Kurumlar
    GLCVY     Aracı Kurumlar
                  ...       
    YYAPI    İnşaat- Taahhüt
    YEOTK    İnşaat- Taahhüt
    BIENY    İnşaat- Taahhüt
    KUYAS    İnşaat- Taahhüt
    TKFEN    İnşaat- Taahhüt
    Name: Sektör, Length: 509, dtype: object



### **10.2.4 En Büyüklerin Sıralanması: nlargest()**

* **Piyasa Değeri(mn $)** sütununa göre piyasa değeri dolar cinsinden en yüksek 10'a bakalım.


```python
df.nlargest(10, "Piyasa Değeri(mn $)")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>SASA</th>
      <td>Sasa Polyester Sanayi A.Ş.</td>
      <td>Endüstriyel Tekstil</td>
      <td>58.05</td>
      <td>307430.5</td>
      <td>11782.5</td>
      <td>24.2</td>
      <td>5296.0</td>
    </tr>
    <tr>
      <th>THYAO</th>
      <td>Türk Hava Yolları</td>
      <td>Havayolları ve Hizm.</td>
      <td>216.60</td>
      <td>298908.0</td>
      <td>11455.9</td>
      <td>50.4</td>
      <td>1380.0</td>
    </tr>
    <tr>
      <th>FROTO</th>
      <td>Ford Otosan</td>
      <td>Otomotiv</td>
      <td>837.70</td>
      <td>293957.3</td>
      <td>11266.1</td>
      <td>17.8</td>
      <td>350.9</td>
    </tr>
    <tr>
      <th>KCHOL</th>
      <td>Koç Holding</td>
      <td>Holdingler</td>
      <td>108.90</td>
      <td>276159.3</td>
      <td>10584.0</td>
      <td>26.4</td>
      <td>2535.9</td>
    </tr>
    <tr>
      <th>ENKAI</th>
      <td>Enka İnşaat</td>
      <td>İnşaat- Taahhüt</td>
      <td>30.16</td>
      <td>180960.0</td>
      <td>6935.4</td>
      <td>8.9</td>
      <td>6000.0</td>
    </tr>
    <tr>
      <th>TUPRS</th>
      <td>Tüpraş</td>
      <td>Petrol</td>
      <td>88.05</td>
      <td>169654.4</td>
      <td>6502.1</td>
      <td>46.5</td>
      <td>1926.8</td>
    </tr>
    <tr>
      <th>QNBFB</th>
      <td>QNB Finansbank</td>
      <td>Bankacılık</td>
      <td>48.50</td>
      <td>162475.0</td>
      <td>6227.0</td>
      <td>0.1</td>
      <td>3350.0</td>
    </tr>
    <tr>
      <th>SISE</th>
      <td>Şişecam</td>
      <td>Cam</td>
      <td>46.70</td>
      <td>143052.1</td>
      <td>5482.6</td>
      <td>48.9</td>
      <td>3063.2</td>
    </tr>
    <tr>
      <th>ISCTR</th>
      <td>İş Bankası (C)</td>
      <td>Bankacılık</td>
      <td>13.92</td>
      <td>139199.6</td>
      <td>5334.9</td>
      <td>32.6</td>
      <td>10000.0</td>
    </tr>
    <tr>
      <th>GARAN</th>
      <td>Garanti Bankası</td>
      <td>Bankacılık</td>
      <td>33.10</td>
      <td>139020.0</td>
      <td>5328.0</td>
      <td>14.0</td>
      <td>4200.0</td>
    </tr>
  </tbody>
</table>
</div>



### **10.2.5 En Küçüklerin Sıralanması: nsmallest()**

* **Piyasa Değeri(mn $)** sütununa göre piyasa değeri dolar cinsinden en düşük 10'a bakalım.


```python
df.nsmallest(10, "Piyasa Değeri(mn $)")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ISKUR</th>
      <td>İş Bankası Kurucu</td>
      <td>Bankacılık</td>
      <td>968000.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>28.7</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>MMCAS</th>
      <td>MMC San.ve Tic. Yatırımlar A.Ş</td>
      <td>Ulaştırma-Lojistik</td>
      <td>4.90</td>
      <td>65.4</td>
      <td>2.5</td>
      <td>92.9</td>
      <td>13.3</td>
    </tr>
    <tr>
      <th>DIRIT</th>
      <td>Diriteks Diriliş Tekstil</td>
      <td>Tekstil Entegre</td>
      <td>7.35</td>
      <td>78.3</td>
      <td>3.0</td>
      <td>93.9</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>BRMEN</th>
      <td>Birlik Mensucat</td>
      <td>Tekstil Entegre</td>
      <td>2.17</td>
      <td>96.8</td>
      <td>3.7</td>
      <td>71.4</td>
      <td>44.6</td>
    </tr>
    <tr>
      <th>ETYAT</th>
      <td>Euro Trend Yatırım</td>
      <td>Yatırım Ortaklıkları</td>
      <td>6.43</td>
      <td>128.6</td>
      <td>4.9</td>
      <td>93.4</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>EUKYO</th>
      <td>Euro Kapital Yatırım Ortaklığı</td>
      <td>Yatırım Ortaklıkları</td>
      <td>6.97</td>
      <td>139.4</td>
      <td>5.3</td>
      <td>99.5</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>EUYO</th>
      <td>Euro Menkul</td>
      <td>Yatırım Ortaklıkları</td>
      <td>7.76</td>
      <td>155.2</td>
      <td>5.9</td>
      <td>99.2</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>EKIZ</th>
      <td>Ekiz Yağ ve Sabun</td>
      <td>Gıda</td>
      <td>17.25</td>
      <td>160.2</td>
      <td>6.1</td>
      <td>62.1</td>
      <td>9.3</td>
    </tr>
    <tr>
      <th>SNKRN</th>
      <td>Senkron Güvenlik</td>
      <td>Teknoloji</td>
      <td>22.40</td>
      <td>175.8</td>
      <td>6.7</td>
      <td>88.4</td>
      <td>7.8</td>
    </tr>
    <tr>
      <th>MARKA</th>
      <td>Marka Yatırım Holding</td>
      <td>Holdingler</td>
      <td>9.35</td>
      <td>196.3</td>
      <td>7.5</td>
      <td>99.2</td>
      <td>21.0</td>
    </tr>
  </tbody>
</table>
</div>



### **10.3 Gruplama ve Özetleme**

#### **10.3.1 Gruplayarak Saydırma, Yüzde Alma ve İndeks İnceleme**

Pandas'ta, veri çerçevesindeki değerleri gruplayarak saydırma, yüzde alma ve indeks inceleme gibi işlemler yapmak için `groupby()`, `value_counts()`, `normalize` ve `loc` gibi metodlar kullanılır.

**1) groupby() Metodu**

* `groupby()` metodu, belirli bir sütuna göre veriyi gruplayarak analiz etmeyi sağlar. Bu metod, bir sütuna göre gruplandırılan veri kümeleri üzerinde işlem yapmamıza olanak tanır.

**2) value_counts() Metodu**

* `value_counts()` metodu, belirli bir sütundaki benzersiz değerlerin sayısını bulmak için kullanılır. Bu metod, özellikle kategorik verilerin dağılımını analiz etmek için kullanılır.

**3) normalize Parametresi**

* `normalize` parametresi, `value_counts()` metodunda kullanılarak sonuçların normalize edilmesini sağlar. Bu parametre sayesinde, sonuçlar yüzdelik olarak elde edilir.

**4) loc Metodu**

* `loc` metodu, belirli bir satır veya sütun etiketine göre veriye erişmek için kullanılır. Bu metod, etiket tabanlı indeksleme yapmamıza olanak tanır.


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
```

* **Halka AçıklıkOranı (%)** sütununa göre yeni bir sütun oluşturalım. 50'den büyüksek >50; küçük veya eşitse <=50 yazsın.


```python
df["HalkaAciklikOraniGrup"] = df["Halka AçıklıkOranı (%)"].apply(lambda x: ">50" if x > 50 else "<=50")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
      <th>HalkaAciklikOraniGrup</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
      <td>&lt;=50</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
      <td>&gt;50</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>245.00</td>
      <td>5788.1</td>
      <td>221.8</td>
      <td>27.7</td>
      <td>23.6</td>
      <td>&lt;=50</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
      <td>&gt;50</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
      <td>&lt;=50</td>
    </tr>
  </tbody>
</table>
</div>



* Şimdi **Sektör** sütununa göre **HalkaAciklikOraniGrup** sütununu saydıralım.


```python
df.groupby(["Sektör"])["HalkaAciklikOraniGrup"].value_counts()
```




    Sektör                   HalkaAciklikOraniGrup
    Aracı Kurumlar           <=50                     10
                             >50                       1
    Bankacılık               <=50                     14
                             >50                       1
    Bilgisayar Toptancılığı  <=50                      5
                                                      ..
    İletişim Cihazları       <=50                      3
    İnşaat Malzemeleri       <=50                      9
                             >50                       7
    İnşaat- Taahhüt          <=50                      4
                             >50                       2
    Name: count, Length: 90, dtype: int64



* İstediğimizi elde ettik. Son olarak örneğin, **Teknoloji** sektörüne bakalım.


```python
df.groupby(["Sektör"])["HalkaAciklikOraniGrup"].value_counts().loc["Teknoloji"]
```




    HalkaAciklikOraniGrup
    <=50    9
    >50     8
    Name: count, dtype: int64



* Görüldüğü üzere, ilgilendiğimiz sektördeki halka açıklık dağılımı bilgisine gruplandırılmış olarak ulaştık. Aynı bilgiye yüzde olarak da erişebiliriz.


```python
df.groupby(["Sektör"])["HalkaAciklikOraniGrup"].value_counts(normalize=True).loc["Teknoloji"]
```




    HalkaAciklikOraniGrup
    <=50    0.529412
    >50     0.470588
    Name: proportion, dtype: float64



### **10.4 Veriyi Belirli Aralıklara Bölme**

#### **pd.cut() Fonksiyonu**

`pd.cut()` fonksiyonu, belirli bir veri serisini kullanarak, belirli aralıklara bölerek kategorik bir değişken oluşturmanızı sağlar. Bu fonksiyon, özellikle sürekli bir değişkeni kategorik bir değişkene dönüştürmek için kullanışlıdır. Örneğin, yaş verilerini kullanarak farklı yaş grupları oluşturabilirsiniz.

`
pd.cut(x, bins, right=True, labels=None, retbins=False, precision=3, include_lowest=False, duplicates='raise')
`
##### **Parametreler:**

- **`x`**: Bölünecek olan veri serisi.
- **`bins`**: Veri serisini bölecek aralıkları belirten bir sayı, liste veya dizin. Aralıkların sayısını belirtmek için bir sayı, aralık sınırlarını belirtmek için bir liste veya dizin kullanabilirsiniz.
- **`labels`**: Oluşturulan kategorik değişkenler için etiketleri belirten bir liste. Bu parametre, belirtilmezse, otomatik olarak aralık sınırlarının ortalamalarını kullanır.
- **`right`**: True veya False değer alır. True ise aralık sınırları dahil, False ise aralık sınırları dahil değil olarak hesaplanır. Varsayılan değeri True'dur.
- **`include_lowest`**: True veya False değer alır. True ise en düşük aralık sınırı dahil, False ise dahil değil olarak hesaplanır. Varsayılan değeri False'dur.
- **`precision`**: Aralıkların sayısal hassasiyetini belirler.
- **`duplicates`**: Aralık sınırları arasında

#### **pd.qcut()** Fonksiyonu

`pd.qcut()` fonksiyonu, veri serisini belirli sayıda eşit boyutlu kategoriye böler. Bu bölmeyi yaparken, her kategori içinde aynı sayıda gözlem olacak şekilde böler. Bu fonksiyon, verilerin dağılımına göre eşit büyüklükte kategorilere ayırmanızı sağlar.

`
pd.qcut(x, q, labels=None, retbins=False, precision=3, duplicates='raise')
`

##### Parametreler:

- **`x`**: Bölünecek olan veri serisi.
- **`q`**: Bölünme işlemi sırasında oluşturulacak kategori sayısı veya kategori boyutlarını belirleyen kesim noktaları.
- **`labels`**: Oluşturulan kategorik değişkenler için etiketleri belirten bir liste. Bu parametre, belirtilmezse, otomatik olarak kesim noktalarının ortalamalarını kullanır.
- **`retbins`**: True veya False değer alır. True ise kesim noktalarını ve sınırlarını döndürür, False ise sadece kesim noktalarını döndürür. Varsayılan değeri False'dur.
- **`precision`**: Kesim noktalarının sayısal hassasiyetini belirler.
- **`duplicates`**: Kesim noktaları arasında çakışan değerler olması durumunda nasıl davranılacağını belirler. "raise" (varsayılan), "drop" veya "raise" değerlerini alır.


```python
import pandas as pd

# Örnek bir veri serisi oluşturalım
notlar = [60, 75, 80, 85, 90, 95, 100]

# Veri serisini belirli sayıda eşit boyutlu kategoriye bölelim
not_gruplari = pd.qcut(x=notlar, q=3, labels=['Düşük', 'Orta', 'Yüksek'])

print(not_gruplari)
```

    ['Düşük', 'Düşük', 'Düşük', 'Orta', 'Orta', 'Yüksek', 'Yüksek']
    Categories (3, object): ['Düşük' < 'Orta' < 'Yüksek']
    

# **11) Veri İşleme ve Temizleme**

## **11.1 Eksik Verilerle Başa Çıkma**

Pandas'ta, eksik verilerle başa çıkmak için çeşitli metodlar bulunmaktadır. Bunlar arasında en sık kullanılanlar ``isnull()`` ve ``notnull()`` fonksiyonları, ``dropna()`` , ``fillna()`` ve ``replace()`` metodlarıdır.

### **11.1.1 Eksik Verileri Tespit Etme: isnull() ve notnull()**

* ``isnull()`` metodu, veri çerçevesindeki her hücredeki değerin eksik (NaN) olup olmadığını kontrol eder. Eksik bir değer varsa, True; aksi takdirde False döndürür.

* ``notnull()`` metodu ise isnull() metodunun tam tersidir. Eksik olmayan (NaN olmayan) değerler için True, eksik değerler için False döndürür.


```python
import pandas as pd

df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/repolarim/pandas-tutorial/pandas-tutorial/temelozet.xlsx', index_col="Kod")
```


```python
import numpy as np

np.random.seed(34)
random_satirlar = df.sample(n=200)
df2 = df
df2.loc[random_satirlar.index, ['Kapanış(TL)','Piyasa Değeri(mn $)']] = np.nan
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>NaN</td>
      <td>5788.1</td>
      <td>NaN</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>NaN</td>
      <td>21919.2</td>
      <td>NaN</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



* 1) **np.random.seed(34):** Bu satır, rastgele sayı üretirken kullanılan seed'in belirlenmesini sağlar. Böylece, aynı seed ile çalışıldığında her seferinde aynı rastgele sayılar elde edilir.

* 2) **random_satirlar = df.sample(n=200):** Bu satır, DataFrame içinden rastgele 200 satırı seçer ve random_satirlar adlı yeni bir DataFrame'e atar. sample() fonksiyonunun n parametresi, kaç tane rastgele satır seçileceğini belirler.

* 3) **df2 = df:** Bu satır, df DataFrame'inin bir kopyasını oluşturur ve bu kopyayı df2 adlı yeni bir değişkene atar. Bu, df ve df2 değişkenlerinin aynı DataFrame'i göstermesine neden olur.

* 4) **df2.loc[random_satirlar.index, ['Kapanış(TL)','Piyasa Değeri(mn $)']] = np.nan:**

        Bu satır, df2 DataFrame'inin belirli satır ve sütunlarını NaN (Not a Number) değerlerine atar. loc[] yöntemi, belirli satır ve sütunları seçmek için kullanılır.        random_satirlarindex, random_satirlar DataFrame'indeki rastgele seçilmiş satırların indekslerini temsil eder. Bu indekslerle seçilen satırların "Kapanış(TL)" ve "Piyasa Değeri(mn $)   " sütunlarına np.nan değerleri atanır. Böylece, bu satırlardaki veriler silinmiş olur.

* 5) **df2:** Bu satır, değişikliklerin uygulandığı df2 DataFrame'ini gösterir. Bu DataFrame, orijinal DataFrame'in bir kopyası olup, belirli satırlardaki veriler NaN değerleriyle değiştirilmiştir.

* Her bir sütunda kaç adet **NaN** değer olduğunu bulalım.


```python
df2.isnull().sum()
```




    Hisse Adı                   0
    Sektör                      0
    Kapanış(TL)               200
    Piyasa Değeri(mn TL)        0
    Piyasa Değeri(mn $)       200
    Halka AçıklıkOranı (%)      0
    Sermaye(mn TL)              0
    dtype: int64



Eğer yukarıda bir sum() daha eklersek toplam **NaN** sayısını alırız.


```python
df2.isnull().sum().sum()
```




    400



### **11.1.2 Eksik Verileri Temizleme: dropna()**

``dropna()`` metodu, veri çerçevesindeki eksik değerleri (NaN) içeren satırları veya sütunları kaldırmak için kullanılır. **axis** parametresiyle satır veya sütun bazında kaldırma seçeneği bulunur. **axis** değeri 1 iken sütun bazında, 0 ken satır bazında işlem yapılır.

* **dropna()** kullanarak **NaN** içeren satırları kaldıralım.


```python
df2.dropna()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>AFYON</th>
      <td>Afyon Çimento</td>
      <td>Çimento</td>
      <td>9.33</td>
      <td>3732.0</td>
      <td>143.0</td>
      <td>48.6</td>
      <td>400.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YUNSA</th>
      <td>Yünsa</td>
      <td>Tekstil Entegre</td>
      <td>137.90</td>
      <td>4021.2</td>
      <td>154.1</td>
      <td>42.1</td>
      <td>29.2</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
  </tbody>
</table>
<p>309 rows × 7 columns</p>
</div>



509 satırlık veri çerçevesinin iki sütununa 200 adet NaN atamıştık. 200'ünü de kaldırıp 309 satırlık bir veri çerçevesi bıraktı.

* **dropna()** fonksiyonunu aşağıdaki gibi özelleştirerek de kullanabilirdik.


```python
df2.dropna(axis='index', how='all', subset=['Kapanış(TL)','Piyasa Değeri(mn $)'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>AFYON</th>
      <td>Afyon Çimento</td>
      <td>Çimento</td>
      <td>9.33</td>
      <td>3732.0</td>
      <td>143.0</td>
      <td>48.6</td>
      <td>400.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YUNSA</th>
      <td>Yünsa</td>
      <td>Tekstil Entegre</td>
      <td>137.90</td>
      <td>4021.2</td>
      <td>154.1</td>
      <td>42.1</td>
      <td>29.2</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
  </tbody>
</table>
<p>309 rows × 7 columns</p>
</div>



* **df2.dropna(axis='index', how='all', subset=['Kapanış(TL)','Piyasa Değeri(mn $)']):** Bu satır, df2 DataFrame'inden NaN (boş) değerlere sahip satırları kaldırmak için kullanılır.

* **axis='index':** Bu parametre, işlemin satırlar boyunca (axis=0) veya sütunlar boyunca (axis=1) yapılacağını belirtir. Burada, satırlar boyunca işlem yapılacağını belirtmek için 'index' değeri kullanılmıştır.

* **how='all':** Bu parametre, satırda tüm değerlerin NaN olması durumunda satırın kaldırılıp kaldırılmayacağını belirler. 'all' değeri, satırın tüm değerleri NaN ise satırın kaldırılacağını belirtir.

* **subset=['Kapanış(TL)','Piyasa Değeri(mn $)']:**

    Bu parametre, işlemin hangi sütunlarda yapılacağını belirtir. Yalnızca belirtilen sütunlardaki NaN değerlere sahip satırlar işleme alınır. Burada, "Kapanış(TL)" ve "Piyasa Değeri (mn $)" sütunlarında NaN değerlere sahip satırlar işleme alınacaktır.

### **11.1.3 Eksik ""NaN" Değerleri Değiştirme: replace() ve fillna()**

**replace():** 
* replace() metodu, eksik değerleri başka bir değerle değiştirmek için kullanılabilir. Özellikle, belirli bir değeri başka bir değerle değiştirmek için kullanılır. Eksik değerler de bu şekilde değiştirilebilir

**fillna():**
* fillna() metodu, eksik değerleri belirli bir değerle doldurmak için kullanılır. Bu metot, eksik değerleri istenilen bir değerle (örneğin 0 veya bir ortalama değer) doldurarak veri setindeki eksik değerleri doldurmak için kullanılır.

* Bazı sütunların bazı değerlerini **NaN** değil de **Veri Yok** yazdığımızı düşünelim. Sonra **Veri Yok** yazan değerleri **NaN** ile değiştirelim.


```python
import pandas as pd
df = pd.read_excel('C:/Users/Yusuf Altuntaş/Desktop/pandasv2/temelozet.xlsx', index_col="Kod")
```


```python
import numpy as np

np.random.seed(34)
random_satirlar = df.sample(n=200)
df2 = df
df2.loc[random_satirlar.index, ['Kapanış(TL)','Piyasa Değeri(mn $)']] = 'Veri Yok'
df2
```

    C:\Users\Yusuf Altuntaş\AppData\Local\Temp\ipykernel_26912\53941387.py:6: FutureWarning: Setting an item of incompatible dtype is deprecated and will raise in a future error of pandas. Value 'Veri Yok' has dtype incompatible with float64, please explicitly cast to a compatible dtype first.
      df2.loc[random_satirlar.index, ['Kapanış(TL)','Piyasa Değeri(mn $)']] = 'Veri Yok'
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.8</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>Veri Yok</td>
      <td>5788.1</td>
      <td>Veri Yok</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.8</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.5</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>Veri Yok</td>
      <td>21919.2</td>
      <td>Veri Yok</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>




```python
df2.replace(to_replace='Veri Yok', value=np.nan, inplace=True)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>NaN</td>
      <td>5788.1</td>
      <td>NaN</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>NaN</td>
      <td>21919.2</td>
      <td>NaN</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



df2.replace(to_replace='Veri Yok', value=np.nan, inplace=True): Bu satır, DataFrame'deki "Veri Yok" değerlerini NaN (boş) değerlere dönüştürmek için kullanılır.

* **to_replace='Veri Yok':** Bu parametre, değiştirilecek değeri belirtir. Burada, "Veri Yok" değerleri değiştirilecek.

* **value=np.nan:** Bu parametre, değiştirme işleminde kullanılacak yeni değeri belirtir. np.nan, NaN (boş) değeri temsil eder. Yani, "Veri Yok" değerleri NaN değerleriyle değiştirilir.

* **inplace=True:** Bu parametre, değişikliklerin orijinal DataFrame üzerinde yapılmasını sağlar. Yani, değiştirme işlemi orijinal DataFrame üzerinde gerçekleşir.

* Şimdi de **NaN** içeren değerleri bizim belirlediğimiz bir string ifadeye çevirelim. Bunu da ``fillna()`` fonksiyonuyla yapalım.


```python
df2.fillna(value="Veri Yok")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.8</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>Veri Yok</td>
      <td>5788.1</td>
      <td>Veri Yok</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.8</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.5</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>Veri Yok</td>
      <td>21919.2</td>
      <td>Veri Yok</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



### **11.1.4 NaN Değerleri Kendinden Bir Önceki veya Bir Sonraki Değere Çevirme: ffill() ve bfill()**

##### **ffill() Metodu**

`ffill()`, "forward fill" olarak da bilinen bir Pandas metodu olan "ileri doldurma" işlemini gerçekleştirir. Bu metod, bir veri çerçevesindeki eksik değerleri bir önceki geçerli değerle doldurur. Eksik değerlerin olduğu yerlerde, bu yöntem bir önceki satır veya sütundaki değeri kullanarak eksik değerleri doldurur.


**Kullanımı**

```python
DataFrame.ffill(axis=None, inplace=False, limit=None, downcast=None)
```

- `axis`: İleri doldurma işleminin satır (0) veya sütun (1) bazında yapılacağını belirtir. Varsayılan değeri None'dir ve eksik değerlerin her iki yönde de doldurulmasını sağlar.
- `inplace`: Değişikliklerin orijinal DataFrame üzerinde yapılıp yapılmayacağını belirtir. Varsayılan değeri False'dur.
- `limit`: İleri doldurma işleminin maksimum kaç adımda yapılacağını belirtir.
- `downcast`: İleri doldurma işlemi sonucunda veri türlerinin küçültülüp küçültülmeyeceğini belirtir.





##### **bfill() Metodu**

`bfill()`, "backward fill" olarak da bilinen bir Pandas metodu olan "geri doldurma" işlemini gerçekleştirir. Bu metod, bir veri çerçevesindeki eksik değerleri bir sonraki geçerli değerle doldurur. Eksik değerlerin olduğu yerlerde, bu yöntem bir sonraki satır veya sütundaki değeri kullanarak eksik değerleri doldurur.

**Kullanımı**

```python
DataFrame.bfill(axis=None, inplace=False, limit=None, downcast=None)
```

- `axis`: Geri doldurma işleminin satır (0) veya sütun (1) bazında yapılacağını belirtir. Varsayılan değeri None'dir ve eksik değerlerin her iki yönde de doldurulmasını sağlar.
- `inplace`: Değişikliklerin orijinal DataFrame üzerinde yapılıp yapılmayacağını belirtir. Varsayılan değeri False'dur.
- `limit`: Geri doldurma işleminin maksimum kaç adımda yapılacağını belirtir.
- `downcast`: Geri doldurma işlemi sonucunda veri türlerinin küçültülüp küçültülmeyeceğini belirtir.


```python
import numpy as np

np.random.seed(34)
random_satirlar = df.sample(n=200)
df2 = df
df2.loc[random_satirlar.index, ['Kapanış(TL)','Piyasa Değeri(mn $)']] = np.nan
df2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>NaN</td>
      <td>5788.1</td>
      <td>NaN</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.ffill()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Hisse Adı</th>
      <th>Sektör</th>
      <th>Kapanış(TL)</th>
      <th>Piyasa Değeri(mn TL)</th>
      <th>Piyasa Değeri(mn $)</th>
      <th>Halka AçıklıkOranı (%)</th>
      <th>Sermaye(mn TL)</th>
    </tr>
    <tr>
      <th>Kod</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A1CAP</th>
      <td>A1 Capital</td>
      <td>Aracı Kurumlar</td>
      <td>26.80</td>
      <td>3618.0</td>
      <td>138.7</td>
      <td>25.9</td>
      <td>135.0</td>
    </tr>
    <tr>
      <th>ACSEL</th>
      <td>Acıselsan Acıpayam Selüloz</td>
      <td>Kimyasal Ürün</td>
      <td>84.25</td>
      <td>903.3</td>
      <td>34.6</td>
      <td>51.8</td>
      <td>10.7</td>
    </tr>
    <tr>
      <th>ADEL</th>
      <td>Adel Kalemcilik</td>
      <td>Kırtasiye</td>
      <td>84.25</td>
      <td>5788.1</td>
      <td>34.6</td>
      <td>27.7</td>
      <td>23.6</td>
    </tr>
    <tr>
      <th>ADESE</th>
      <td>Adese AVM</td>
      <td>Perakande - Ticaret</td>
      <td>1.62</td>
      <td>1633.0</td>
      <td>62.6</td>
      <td>92.9</td>
      <td>1008.0</td>
    </tr>
    <tr>
      <th>AEFES</th>
      <td>Anadolu Efes</td>
      <td>Meşrubat / İçecek</td>
      <td>70.85</td>
      <td>41950.7</td>
      <td>1607.8</td>
      <td>32.9</td>
      <td>592.1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>YYAPI</th>
      <td>Yesil Yapi</td>
      <td>İnşaat- Taahhüt</td>
      <td>2.72</td>
      <td>875.0</td>
      <td>33.5</td>
      <td>72.2</td>
      <td>321.7</td>
    </tr>
    <tr>
      <th>YYLGD</th>
      <td>Yayla Agro Gıda</td>
      <td>Gıda</td>
      <td>31.32</td>
      <td>14801.8</td>
      <td>567.3</td>
      <td>15.0</td>
      <td>472.6</td>
    </tr>
    <tr>
      <th>ZEDUR</th>
      <td>Zedur Enerji</td>
      <td>Elektrik</td>
      <td>49.80</td>
      <td>1245.0</td>
      <td>47.7</td>
      <td>38.6</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>ZOREN</th>
      <td>Zorlu Enerji</td>
      <td>Elektrik</td>
      <td>3.50</td>
      <td>17500.0</td>
      <td>670.7</td>
      <td>30.0</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>ZRGYO</th>
      <td>Ziraat GYO</td>
      <td>GYO</td>
      <td>3.50</td>
      <td>21919.2</td>
      <td>670.7</td>
      <td>18.9</td>
      <td>4693.6</td>
    </tr>
  </tbody>
</table>
<p>509 rows × 7 columns</p>
</div>



## **11.2 Veri Türü Dönüşümleri**

### **Veri Türü Dönüşümleri**

Veri analizi sırasında, veri çerçevesinde bulunan sütunların veri tiplerini dönüştürmek gerekebilir. Pandas, bu tür dönüşümleri gerçekleştirmek için çeşitli fonksiyonlar ve metodlar sunar. Bu dönüşümler, veri işleme ve analiz süreçlerinde veri uyumluluğunu sağlamak, hesaplama ve analiz yapmak için uygun veri türlerini kullanmak ve veri manipülasyonunu kolaylaştırmak için önemlidir. İşte yaygın olarak kullanılan bazı veri türü dönüşüm yöntemleri:

---

#### **1. `astype()` Metodu**

* `astype()` metodu, belirli bir sütunun veri tipini değiştirmek için kullanılır. Bu metot, belirli bir sütunu farklı bir veri tipine dönüştürmek için kullanılır.

```python
# Örnek bir DataFrame oluşturalım
import pandas as pd

data = {'A': [1, 2, 3],
        'B': [4.0, 5.0, 6.0],
        'C': ['7', '8', '9']}

df = pd.DataFrame(data)

# 'C' sütununun veri tipini string'den integer'a dönüştürme
df['C'] = df['C'].astype(int)

print(df.dtypes)
```

---

#### **2. `to_numeric()` Fonksiyonu**

* `to_numeric()` fonksiyonu, belirli bir sütunu sayısal veri tipine dönüştürmek için kullanılır. Bu fonksiyon, özellikle bir sütunda hem sayısal hem de non-sayısal değerler varsa kullanışlıdır.

```python
# 'C' sütununu sayısal veri tipine dönüştürme
df['C'] = pd.to_numeric(df['C'], errors='coerce')

print(df.dtypes)
```

---

#### **3. `to_datetime()` Fonksiyonu**

* `to_datetime()` fonksiyonu, belirli bir sütunu tarih/zaman veri tipine dönüştürmek için kullanılır.

```python
# 'D' sütununu tarih/zaman veri tipine dönüştürme
df['D'] = pd.to_datetime(df['D'])

print(df.dtypes)
```

---

#### **4. `astype()` ve `map()` Kullanımı**

* `astype()` metodu ve `map()` fonksiyonu birlikte kullanılarak kategorik bir sütunu kategorik veri tipine dönüştürebiliriz.

```python
# 'E' sütununu kategorik veri tipine dönüştürme
df['E'] = df['E'].astype(str)
df['E'] = df['E'].map({'dog': 1, 'cat': 2})

print(df.dtypes)
```

Bu örneklerde, `astype()`, `to_numeric()`, `to_datetime()` ve `map()` fonksiyonlarının kullanımıyla veri türü dönüşümlerini gerçekleştirebiliriz. Bu yöntemler, veri analizi ve işlemlerinde veri uyumluluğunu sağlamak için önemlidir.

## **11.3 Veri Çerçevesinde Tekrar Eden Değerleri Kaldırma**


Veri analizi sırasında, bir veri çerçevesindeki tekrar eden değerlerin kaldırılması genellikle önemlidir çünkü bu tür değerlerin analiz sonuçlarını yanıltabileceği ve gereksiz bilgi yükü oluşturabileceği görülür. Pandas, veri çerçevesindeki tekrar eden değerleri kaldırmak için çeşitli yöntemler sunar.

### **11.3.1 `drop_duplicates()` Metodu**

`drop_duplicates()` metodu, veri çerçevesindeki tekrar eden satırları kaldırmak için kullanılır. Bu metot, belirtilen sütunlar arasında tekrar eden satırları kaldırabilir veya tüm sütunlar dikkate alınarak tekrar eden satırları kaldırabilir.

**Kullanımı**

```python
DataFrame.drop_duplicates(subset=None, keep='first', inplace=False, ignore_index=False)
```

- `subset`: Tekrar eden satırları kontrol etmek için belirli sütunları belirtir. Varsayılan değeri None'dır ve tüm sütunlar dikkate alınır.
- `keep`: Tekrar eden satırlardan hangisinin tutulacağını belirtir. 'first' (varsayılan) ilk tekrar eden satırı, 'last' son tekrar eden satırı tutar.
- `inplace`: Değişikliklerin orijinal DataFrame üzerinde yapılıp yapılmayacağını belirtir. Varsayılan değeri False'dur.
- `ignore_index`: Yeniden dizinleme yapılıp yapılmayacağını belirtir. Varsayılan değeri False'dur.


```python
import pandas as pd

# Örnek bir veri çerçevesi oluşturalım
data = {'A': [1, 2, 2, 3, 4],
        'B': ['a', 'b', 'b', 'c', 'c']}
örnekveri = pd.DataFrame(data)

# Tekrar eden satırları kaldırma
unique_df = örnekveri.drop_duplicates()

print(unique_df)
```

       A  B
    0  1  a
    1  2  b
    3  3  c
    4  4  c
    

### **11.3.2 `unique()` ve `nunique()` Metotları**

`unique()` ve `nunique()` metotları, belirli bir sütunda veya veri çerçevesindeki benzersiz değerleri ve bu değerlerin sayısını bulmak için kullanılabilir.

**Kullanımı**

```python
Series.unique()
Series.nunique(dropna=True)
```

- `dropna`: NaN değerlerin dahil edilip edilmeyeceğini belirtir. Varsayılan değeri True'dur.


```python
import pandas as pd

# Örnek bir veri çerçevesi oluşturalım
data = {'A': [1, 2, 2, 3, 4],
        'B': ['a', 'b', 'b', 'c', 'c']}
örnekveri = pd.DataFrame(data)

# 'A' sütunundaki benzersiz değerler
unique_values = örnekveri['A'].unique()
print("Benzersiz Değerler:", unique_values)

# 'B' sütunundaki benzersiz değerlerin sayısı
num_unique_values = örnekveri['B'].nunique()
print("Benzersiz Değerlerin Sayısı:", num_unique_values)
```

    Benzersiz Değerler: [1 2 3 4]
    Benzersiz Değerlerin Sayısı: 3
    

# **12) Zaman Serisi Verileri**

## Zaman Serisi Verileri Nedir?

Zaman serisi verileri, zamanla değişen bir veya birden fazla değişkenin düzenli aralıklarla ölçüldüğü veri türüdür. Genellikle zaman serileri, zamana göre düzenlenmiş bir gözlem dizisi şeklinde temsil edilir ve veri analizinde zaman boyunca değişen desenleri, trendleri ve ilişkileri analiz etmek için kullanılır.

Zaman serisi verileri genellikle aşağıdaki özelliklere sahiptir:

- **Zaman bileşeni**: Veriler, belirli bir zaman aralığında toplanmış veya ölçülmüş olmalıdır. Örneğin, saatlik, günlük, aylık veya yıllık zaman aralıklarında olabilir.
  
- **Zaman sırası**: Gözlemler, zaman sırasına göre düzenlenmiştir. Yani, bir gözlem bir sonraki gözlemden önce veya sonra gerçekleşmiştir.

- **Zamana bağlı değişkenlik**: Zaman serisi verilerinde, zamanla değişen bir veya daha fazla değişken bulunur. Bu değişkenler genellikle belirli bir olayın veya koşulun zaman içinde nasıl değiştiğini gösterir.

Zaman serisi verileri, birçok farklı alanda yaygın olarak kullanılır. Örneğin:

- Ekonomi ve finans: Hisse senedi fiyatları, döviz kurları, enflasyon oranları gibi ekonomik verilerin zaman serisi analizi.
  
- Hava durumu: Sıcaklık, nem, rüzgar hızı gibi meteorolojik verilerin zaman serisi analizi.
  
- Üretim ve endüstri: Üretim miktarları, tüketim eğilimleri gibi endüstriyel verilerin zaman serisi analizi.
  
- Sağlık: Hastalık yayılımı, ilaç etkileri gibi sağlık verilerinin zaman serisi analizi.

Zaman serisi verilerinin analizi, gelecekteki trendleri tahmin etmek, geçmiş performansı değerlendirmek, anormallikleri tespit etmek ve karar alma süreçlerini desteklemek için önemlidir. Bu nedenle, zaman serisi verileri, istatistiksel ve makine öğrenimi tekniklerinin kullanıldığı birçok analiz ve modelleme yöntemine konu olmuştur.


```python
from datetime import datetime

# Tarih ve saat oluşturma
dt = datetime(2023, 12, 31, 23, 59, 59)
print(dt)
```

    2023-12-31 23:59:59
    

* Yukarıdaki örnekte, 31 Aralık 2023 tarihini ve 23:59:59 saatini temsil eden bir `datetime` nesnesi oluşturulmuştur.

## **12.1 Tarih ve Saat Veri Türleri**

Tarih ve saat veri türleri, zaman serisi verilerinin temel yapı taşlarıdır. Python'da, tarih ve saat verilerini temsil etmek için datetime modülü kullanılır. Bu modül, datetime ve timedelta gibi birçok sınıfı içerir ve tarihleri oluşturmak, manipüle etmek ve aritmetik işlemler yapmak için kullanılır.

### **12.1.1 datetime Sınıfı**

``datetime`` sınıfı, tarih ve saati temsil etmek için kullanılır. Tarih ve saat bilgileri, yıl, ay, gün, saat, dakika, saniye ve milisaniye cinsinden saklanabilir.


```python
from datetime import datetime

# Tarih ve saat oluşturma
dt = datetime(2023, 12, 31, 23, 59, 59)
print(dt)
```

    2023-12-31 23:59:59
    

* Yukarıdaki örnekte, 31 Aralık 2023 tarihini ve 23:59:59 saatini temsil eden bir datetime nesnesi oluşturulmuştur.

### **12.1.2 timedelta Sınıfı**

`timedelta` sınıfı, iki tarih arasındaki zaman farkını temsil etmek için kullanılır. Bu fark, gün, saat, dakika, saniye ve milisaniye cinsinden ifade edilebilir.


```python
from datetime import timedelta

# Zaman farkı oluşturma
diff = timedelta(days=5, hours=3, minutes=30)
print(diff)
```

    5 days, 3:30:00
    

* Yukarıdaki örnekte, 5 gün 3 saat 30 dakika sürecek bir `timedelta` nesnesi oluşturulmuştur.

### **12.1.3 strftime() ve strptime() Metodları**

`strftime()` metodu, bir `datetime` nesnesini belirli bir biçimde biçimlendirmek için kullanılırken, `strptime()` metodu ise bir tarih ve saat dizesini bir `datetime` nesnesine dönüştürmek için kullanılır.


```python
from datetime import datetime

# Tarih ve saat dönüşümü
dt_str = "2023-12-31 23:59:59"
dt = datetime.strptime(dt_str, "%Y-%m-%d %H:%M:%S")
print(dt)

# Tarih ve saat biçimlendirme
dt_formatted = dt.strftime("%d/%m/%Y %I:%M %p")
print(dt_formatted)
```

    2023-12-31 23:59:59
    31/12/2023 11:59 PM
    

* Yukarıdaki örnekte, bir tarih ve saat dizesi bir `datetime` nesnesine dönüştürülmüş ve ardından biçimlendirilmiştir.

## **12.2 Zaman Serisi Oluşturma**

Zaman serisi verileri, zamanla değişen bir veya birden fazla değişkenin düzenli aralıklarla ölçüldüğü veri türüdür. Python'da, zaman serisi verilerini oluşturmak için birkaç farklı yöntem bulunmaktadır. Bu yöntemlerden bazıları şunlardır:

### **12.2.1 Manuel Olarak Zaman Serisi Oluşturma**

Zaman serisi verilerini manuel olarak oluşturmak için `datetime` modülünden yararlanabiliriz. Bu yöntemde, belirli bir zaman aralığı boyunca düzenli aralıklarla ölçümler yaparak zaman serisini oluştururuz.


```python
from datetime import datetime, timedelta

# Başlangıç tarihi
start_date = datetime(2022, 1, 1)

# Zaman serisini oluşturma
time_series = []
for i in range(10):
    time_series.append(start_date + timedelta(days=i))

print(time_series)
```

    [datetime.datetime(2022, 1, 1, 0, 0), datetime.datetime(2022, 1, 2, 0, 0), datetime.datetime(2022, 1, 3, 0, 0), datetime.datetime(2022, 1, 4, 0, 0), datetime.datetime(2022, 1, 5, 0, 0), datetime.datetime(2022, 1, 6, 0, 0), datetime.datetime(2022, 1, 7, 0, 0), datetime.datetime(2022, 1, 8, 0, 0), datetime.datetime(2022, 1, 9, 0, 0), datetime.datetime(2022, 1, 10, 0, 0)]
    

* Yukarıdaki örnekte, başlangıç tarihinden itibaren 10 gün boyunca her günün tarihini içeren bir zaman serisi oluşturulmuştur.

### **12.2.2 Pandas ile Zaman Serisi Oluşturma**

Pandas kütüphanesi, zaman serisi verilerini oluşturmak için kullanışlı bir araçtır. `pd.date_range()` fonksiyonu, belirli bir tarih aralığında veya frekansta zaman serisi oluşturmak için kullanılabilir.

* Örneğin, bir zaman serisi oluşturmak için 2024 yılının Ocak ayındaki günlerin bir listesini kullanalım:


```python
import pandas as pd

# Zaman serisini oluşturma
time_series = pd.date_range(start='2024-01-01', end='2024-01-31', freq='D')
print(time_series)
```

    DatetimeIndex(['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04',
                   '2024-01-05', '2024-01-06', '2024-01-07', '2024-01-08',
                   '2024-01-09', '2024-01-10', '2024-01-11', '2024-01-12',
                   '2024-01-13', '2024-01-14', '2024-01-15', '2024-01-16',
                   '2024-01-17', '2024-01-18', '2024-01-19', '2024-01-20',
                   '2024-01-21', '2024-01-22', '2024-01-23', '2024-01-24',
                   '2024-01-25', '2024-01-26', '2024-01-27', '2024-01-28',
                   '2024-01-29', '2024-01-30', '2024-01-31'],
                  dtype='datetime64[ns]', freq='D')
    

* Burada, start parametresi başlangıç tarihini, end parametresi bitiş tarihini, ve freq parametresi tarihler arasındaki adımı belirtir. D frekansı günlük olarak adım atılacağını belirtir.

### **12.2.3 NumPy ile Zaman Serisi Oluşturma**

NumPy kütüphanesi de zaman serisi verilerini oluşturmak için kullanılabilir. `np.arange()` veya `np.linspace()` gibi fonksiyonlarla belirli bir aralıkta veya belirli adımlarla zaman serisi oluşturulabilir.


```python
tarihler = np.arange('2024-01-01', '2024-01-11', dtype='datetime64[D]')
tarihler
```




    array(['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04',
           '2024-01-05', '2024-01-06', '2024-01-07', '2024-01-08',
           '2024-01-09', '2024-01-10'], dtype='datetime64[D]')



* Burada, ``'2024-01-01'`` başlangıç tarihi, ``2024-01-11`` ise bitiş tarihidir. ``dtype='datetime64[D]'`` ifadesi, tarihlerin günlük olarak depolanacağını belirtir.
