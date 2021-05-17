# data-gempabumi-json
Konversi tipe data gempa bumi BMKG dari XML ke JSON

Sumber data dari https://data.bmkg.go.id/gempabumi 

Berikut ini kode Python 3 untuk mengolah data XML dan data JSON
1. Function (`function.py`)
2. Gempabumi Terbaru (`autogempa.py`)
3. Daftar 15 Gempabumi M 5.0+ (`gempaterkini.py`)
4. Daftar 15 Gempabumi Dirasakan (`gempadirasakan.py`)

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
