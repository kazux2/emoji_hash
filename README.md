# emoji_hash


## サンプルコード

```python
import pickle

pickled_hash = 'twemoji/hash/alpha/step20_type_top10_emojis.pickle'
with open(pickled_hash, 'rb') as f:
    hash_dict = pickle.load(f)

rgb = '020240040'  # g:020 b:240 r:040 に対応する絵文字を引っ張ってくる。str型。

print(hash_dict[rgb])
```

以下が得られる。
```
['w_1f1e8-1f1e8.png',
 'w_1f1ff-1f1f2.png',
 'w_1f1e7-1f1f7.png',
 'w_1f4d7.png',
 'w_1f1f8-1f1e6.png',
 'w_2705.png',
 'w_1f1ef-1f1f2.png',
 'w_1f1f8-1f1f9.png',
 'w_1f922.png',
 'w_1f22f.png']
```

## ファイルについて

twemoji: twitterのオープンソース絵文字

notomoji: googleのオープンソース絵文字

それぞれに対応したフォルダの中にstep数(rgbの刻み)の異なるpickleファイルがある。
pickle.loadするとpythonのdict型になり、構造は以下のようになっている。

```python
"""
{
'000000000':["emoji_1230.png","emoji_0453.png", ...],
...
'255255255':["_white.png", "emoji_0453.png", ...]
}
"""
```


## お知らせ
emojineerでは、絵文字にindexを振って、`rgb対index → index対emoji` のように参照していたが、今回はrgbから直接絵文字のfile_nameを参照できるように作成。
