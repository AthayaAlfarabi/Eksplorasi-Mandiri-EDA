# Assignment IPSD

## Eksplorasi-Mandiri-EDA

- Exploratory Data Analysis (EDA) adalah pendekatan untuk analisis data dengan menggunakan berbagai teknik untuk memahami karakteristik dan pola dalam dataset sebelum melakukan analisis lebih lanjut. EDA melibatkan penggunaan berbagai teknik statistik dan visualisasi untuk menggali informasi yang terkandung dalam data.
- Metode yang sering digunakan dalam EDA meliputi visualisasi data (seperti grafik batang, histogram, dan scatter plot) serta statistik deskriptif (seperti mean, median, dan standar deviasi). Dengan melakukan EDA, analisis data menjadi lebih terarah dan informatif.

## Daftar Isi
1. [Load Data](#load-data)
2. [Information About Dataset](#information-about-dataset)
3. [Cek Nilai Duplicate](#cek-nilai-duplicate)
4. [Vidualisasikan](#visualisasikan)
5. [Null Values](#null-values)
6. [Replace semua Null Values](#replace-semua-null-values )
7. [Mengetahui Tipe Data](#mengetahui-tipe-data)
8. [Filter Data](#filter-data)
9. [Boxplot](#boxplot)
10. [Correlation](#correlation)
---

## 1. Load Data
Langkah pertama merupakan load/impor dataset kedalam platform coding, disini menggunakan VSCode dan dataset diperoleh dari kaggle

### Contoh Kode
```python
mba = pd.read_csv('C:/Users/Ruby/Downloads/MBA Admission/MBA.csv')
mba
```
<div>
output yang dikeluarkan :
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>application_id</th>
      <th>gender</th>
      <th>international</th>
      <th>gpa</th>
      <th>major</th>
      <th>race</th>
      <th>gmat</th>
      <th>work_exp</th>
      <th>work_industry</th>
      <th>admission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Female</td>
      <td>False</td>
      <td>3.30</td>
      <td>Business</td>
      <td>Asian</td>
      <td>620.0</td>
      <td>3.0</td>
      <td>Financial Services</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Male</td>
      <td>False</td>
      <td>3.28</td>
      <td>Humanities</td>
      <td>Black</td>
      <td>680.0</td>
      <td>5.0</td>
      <td>Investment Management</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Female</td>
      <td>True</td>
      <td>3.30</td>
      <td>Business</td>
      <td>NaN</td>
      <td>710.0</td>
      <td>5.0</td>
      <td>Technology</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Male</td>
      <td>False</td>
      <td>3.47</td>
      <td>STEM</td>
      <td>Black</td>
      <td>690.0</td>
      <td>6.0</td>
      <td>Technology</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Male</td>
      <td>False</td>
      <td>3.35</td>
      <td>STEM</td>
      <td>Hispanic</td>
      <td>590.0</td>
      <td>5.0</td>
      <td>Consulting</td>
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
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>6189</th>
      <td>6190</td>
      <td>Male</td>
      <td>False</td>
      <td>3.49</td>
      <td>Business</td>
      <td>White</td>
      <td>640.0</td>
      <td>5.0</td>
      <td>Other</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6190</th>
      <td>6191</td>
      <td>Male</td>
      <td>False</td>
      <td>3.18</td>
      <td>STEM</td>
      <td>Black</td>
      <td>670.0</td>
      <td>4.0</td>
      <td>Consulting</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6191</th>
      <td>6192</td>
      <td>Female</td>
      <td>True</td>
      <td>3.22</td>
      <td>Business</td>
      <td>NaN</td>
      <td>680.0</td>
      <td>5.0</td>
      <td>Health Care</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>6192</th>
      <td>6193</td>
      <td>Male</td>
      <td>True</td>
      <td>3.36</td>
      <td>Business</td>
      <td>NaN</td>
      <td>590.0</td>
      <td>5.0</td>
      <td>Other</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6193</th>
      <td>6194</td>
      <td>Male</td>
      <td>False</td>
      <td>3.23</td>
      <td>STEM</td>
      <td>Hispanic</td>
      <td>650.0</td>
      <td>4.0</td>
      <td>Consulting</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>6194 rows × 10 columns</p>
</div>

## 2. Basic Information About Datasets
Setelah impor dataset, langkah selanjutnya adalah memahami data melalui eksaminasi informasi-informasi dasar yang dipunyai dataset
```python
mba.head(10)
```
<div>
output yang dikeluarkan :
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>application_id</th>
      <th>gender</th>
      <th>international</th>
      <th>gpa</th>
      <th>major</th>
      <th>race</th>
      <th>gmat</th>
      <th>work_exp</th>
      <th>work_industry</th>
      <th>admission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Female</td>
      <td>False</td>
      <td>3.30</td>
      <td>Business</td>
      <td>Asian</td>
      <td>620.0</td>
      <td>3.0</td>
      <td>Financial Services</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Male</td>
      <td>False</td>
      <td>3.28</td>
      <td>Humanities</td>
      <td>Black</td>
      <td>680.0</td>
      <td>5.0</td>
      <td>Investment Management</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Female</td>
      <td>True</td>
      <td>3.30</td>
      <td>Business</td>
      <td>NaN</td>
      <td>710.0</td>
      <td>5.0</td>
      <td>Technology</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Male</td>
      <td>False</td>
      <td>3.47</td>
      <td>STEM</td>
      <td>Black</td>
      <td>690.0</td>
      <td>6.0</td>
      <td>Technology</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Male</td>
      <td>False</td>
      <td>3.35</td>
      <td>STEM</td>
      <td>Hispanic</td>
      <td>590.0</td>
      <td>5.0</td>
      <td>Consulting</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>Male</td>
      <td>False</td>
      <td>3.18</td>
      <td>Business</td>
      <td>White</td>
      <td>610.0</td>
      <td>6.0</td>
      <td>Consulting</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>Female</td>
      <td>False</td>
      <td>2.93</td>
      <td>STEM</td>
      <td>Other</td>
      <td>590.0</td>
      <td>3.0</td>
      <td>Technology</td>
      <td>Admit</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>Male</td>
      <td>True</td>
      <td>3.02</td>
      <td>Business</td>
      <td>NaN</td>
      <td>630.0</td>
      <td>6.0</td>
      <td>Financial Services</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>Male</td>
      <td>False</td>
      <td>3.24</td>
      <td>Business</td>
      <td>White</td>
      <td>590.0</td>
      <td>2.0</td>
      <td>Nonprofit/Gov</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>Male</td>
      <td>False</td>
      <td>3.27</td>
      <td>Humanities</td>
      <td>Asian</td>
      <td>690.0</td>
      <td>3.0</td>
      <td>Consulting</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
Code tersebut akan menampilkan sepuluh baris pertama pada dataset

### Contoh Kode
```python
mba.describe()
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>application_id</th>
      <th>gpa</th>
      <th>gmat</th>
      <th>work_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6194.000000</td>
      <td>6194.000000</td>
      <td>6194.000000</td>
      <td>6194.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3097.500000</td>
      <td>3.250714</td>
      <td>651.092993</td>
      <td>5.016952</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1788.198115</td>
      <td>0.151541</td>
      <td>49.294883</td>
      <td>1.032432</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>2.650000</td>
      <td>570.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1549.250000</td>
      <td>3.150000</td>
      <td>610.000000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3097.500000</td>
      <td>3.250000</td>
      <td>650.000000</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4645.750000</td>
      <td>3.350000</td>
      <td>680.000000</td>
      <td>6.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>6194.000000</td>
      <td>3.770000</td>
      <td>780.000000</td>
      <td>9.000000</td>
    </tr>
  </tbody>
</table>
</div>
Code tersebut berfungsi untuk memunculkan statistika deskriptif dataset tersebut

## 3. Cek Nilai duplikat dan nilai unik
Disini kita akan mengecek apakah ada nilai yang terduplikat dalam dataframe dan juga menemukan nilai unik pada setiap kolom pada dataframe

### Contoh Kode
```python
mba.duplicated().sum()
```
output yang dikeluarkan :
0, dikarenakan tidak ada data yang terduplikat

### Contoh Kode
```python
# Loop untuk menampilkan value counts pada setiap kolom
for column in mba.columns:
    print(f"Value counts pada kolom '{column}':")
    print(mba[column].value_counts(), "\n")
```
output yang dikeluarkan :
Value counts pada kolom 'application_id':
application_id
1       1
4162    1
4136    1
4135    1
4134    1
       ..
2063    1
2062    1
2061    1
2060    1
6194    1
Name: count, Length: 6194, dtype: int64 

Value counts pada kolom 'gender':
gender
Male      3943
Female    2251
Name: count, dtype: int64 

Value counts pada kolom 'international':
international
False    4352
True     1842
Name: count, dtype: int64 

Value counts pada kolom 'gpa':
gpa
3.24    192
3.21    170
3.26    165
3.27    165
3.29    162
       ... 
2.73      1
2.81      1
2.79      1
3.69      1
2.65      1
Name: count, Length: 101, dtype: int64 

Value counts pada kolom 'major':
major
Humanities    2481
STEM          1875
Business      1838
Name: count, dtype: int64 

Value counts pada kolom 'race':
race
White       3298
Asian       1147
Black        916
Hispanic     596
Other        237
Name: count, dtype: int64 

Value counts pada kolom 'gmat':
gmat
660.0    483
670.0    454
650.0    451
640.0    444
620.0    439
570.0    422
630.0    417
680.0    399
610.0    381
690.0    329
600.0    313
700.0    280
590.0    260
710.0    251
580.0    212
720.0    193
730.0    125
740.0    107
750.0     78
780.0     65
760.0     60
770.0     31
Name: count, dtype: int64 

Value counts pada kolom 'work_exp':
work_exp
5.0    2419
6.0    1528
4.0    1437
3.0     369
7.0     367
8.0      38
2.0      32
9.0       2
1.0       2
Name: count, dtype: int64 

Value counts pada kolom 'work_industry':
work_industry
Consulting               1619
PE/VC                     907
Technology                716
Nonprofit/Gov             651
Investment Banking        580
Financial Services        451
Other                     421
Health Care               334
Investment Management     166
CPG                       114
Real Estate               111
Media/Entertainment        59
Retail                     33
Energy                     32
Name: count, dtype: int64 

Value counts pada kolom 'admission':
admission
decline     5194
Admit        900
Waitlist     100
Name: count, dtype: int64 

### Memvisualisasikan Nilai Unik Pada Kolom Race dan Gender
```python
# Visualisasi nilai unik pada kolom 'race' menggunakan count plot
plt.figure(figsize=(8, 6))
sns.countplot(x='race', data=mba, palette='viridis')
plt.title('Frekuensi Nilai Unik pada Kolom "Race"')
plt.xlabel('Nilai Unik')
plt.ylabel('Jumlah')
plt.show()

# Visualisasi nilai unik pada kolom 'gender'
plt.figure(figsize=(8, 6))
sns.countplot(x='gender', data=mba, palette='viridis')
plt.title('Frekuensi Nilai Unik pada Kolom "gender"')
plt.xlabel('Nilai Unik')
plt.ylabel('Jumlah')
plt.show()
```
output yang dikeluarkan : 
![image](https://github.com/user-attachments/assets/658ef3a5-3a71-43eb-b81e-0738defbb07d)
![image](https://github.com/user-attachments/assets/1687dfac-b670-4015-b98c-d9323185b4d6)

## Menemukan null values

```python
mba.isnull().sum()
```
## Output yang dikeluarkan : 
### application_id       0
### gender               0
### international        0
### gpa                  0
### major                0
### race              1842
### gmat                 0
### work_exp             0
### work_industry        0
### admission         5194
### dtype: int64

### kolom dengan nilai kosong ada 2, yaitu Race dan Admission

