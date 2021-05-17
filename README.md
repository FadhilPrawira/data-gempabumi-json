# data-gempabumi-json
Konversi tipe data gempa bumi BMKG dari XML ke JSON

Sumber data dari https://data.bmkg.go.id/gempabumi 

Berikut ini kode Python 3 untuk mengolah data XML dan data JSON
1. Function (`function.py`)
2. Gempabumi Terbaru (`autogempa.py`)
3. Daftar 15 Gempabumi M 5.0+ (`gempaterkini.py`)
4. Daftar 15 Gempabumi Dirasakan (`gempadirasakan.py`)

Parameter (key)
* Tanggal dan Jam dalam WIB
* DateTime sesuai ISO 8601 dalam UTC (+00:00)
* Magnitude atau magnitudo merupakan kekuatan gempa
* Kedalaman dalam kilometer (km)
* Koordinat Lintang dan Bujur
* Susunan key coordinates adalah latitude kemudian longitude
* Wilayah terdekat dengan lokasi episenter gempabumi
* Potensi tsunami atau tidak, dan status gempa dirasakan
* Dirasakan merupakan wilayah yang merasakan gempa dalam skala MMI
* Gambar Shakemap (peta guncangan) diawali dengan URL https://data.bmkg.go.id/DataMKG/TEWS/

### Kode Baris Python 3 untuk Mengolah Data `autogempa.py` dari JSON `function.py`
```python
import function
import json
result = json.loads(function.autogempa())
mapURL = result["Shakemap"]
result.pop("Shakemap")
print("")
for x in result:
    print("{:<15} : ".format(x) + result[x])

print("{:<15} :".format("Shakemap"))
import IPython
IPython.display.Image(mapURL)

```
### Kode Baris Python 3 untuk Mengolah Data `gempaterkini.py` dari JSON `function.py`
```python
import function
import json
result = json.loads(function.gempaterkini())
for x in result:
    for y in result[x]:
        print("{:<15} : ".format(y) + result[x][y])
    print("\n")

```
### Kode Baris Python 3 untuk Mengolah Data `gempadirasakan.py` dari JSON `function.py`
```python
import function
import json
result = json.loads(function.gempadirasakan())
for x in result:
    for y in result[x]:
        print("{:<15} : ".format(y) + result[x][y])
    print("\n")

```
