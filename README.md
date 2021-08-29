# utaupy中文文档
本仓库为[utaupy](https://github.com/oatsu-gh/utaupy)文档的中文翻译。

由于我不会日文，该翻译是在机翻的基础上修改得到的，可能有错误，欢迎提出[Issue](https://github.com/oxygen-dioxide/utaupy-zh-docs/issues)和[Pull Request](https://github.com/oxygen-dioxide/utaupy-zh-docs/pulls)

以下是[utaupy仓库](https://github.com/oatsu-gh/utaupy)的readme.md中文翻译，[原文链接](https://github.com/oatsu-gh/utaupy/blob/master/README.md)

# utaupy
[![PyPI](https://img.shields.io/pypi/v/utaupy.svg)](https://pypi.python.org/pypi/utaupy)

utaupy是处理UTAU相关文件的Python库。

如果需要用Python开发UTAU插件，**[pyUtau](https://github.com/UtaUtaUtau/pyUtau)** 可能是一个更好的选择，它是 **[utauPlugin](https://github.com/delta-kimigatame/utauPlugin)** 的Python实现，为处理颤音和音高提供了方便的接口。

## 用户协议
参见LICENSE文件。

## 支持的文件类型
- .ust (UTAU工程文件)
- .txt (UTAU插件声明)
- .txt (录音表)
- .ini (原音设定)
- .lab (歌唱データベース用音素ラベル)
- .table (ローマ字かな対応表)
- .svp (Synthesizer V R2)
- .csv (REAPER リージョン・マーカー用)

## 功能
- 解析 INI, UST, LAB 文件，并表示为python对象
- INI, UST, LAB 文件互转（但有很多不可逆过程）

# Methods
---
## utaupy.ust
---
### Ust(collections.UserList)
UST 文件类

### load(path)
读取UST文件，返回Ust对象
```Python
ustobj = utaupy.ust.load(path)
print(type(ustobj))
# <class 'utaupy.ust.Ust'>
```
---

## utaupy.otoini
UTAUの原音設定ファイルを扱うモジュール。setParamでの利用を想定。

---

### class utaupy.otoini.OtoIni(collections.UserList)

oto.ini ファイルを扱うためのクラス。

---

### class utaupy.otoini.Oto(collections.UserDict)

oto.ini に含まれる各原音のパラメータを扱うクラス。

---

## utaupy.table

かなローマ字変換表などを扱うモジュール。

## utaupy.convert

Ust オブジェクト、OtoIni オブジェクト、Label オブジェクトなどを変換するモジュール。

## utaupy.reaper

REAPER (DAW) のリージョン・マーカー用CSVファイルを扱うモジュール。

## utaupy.utau

UTAUエディタで行う操作の代替と、UTAU音源の原音値取得などをするモジュール。「パラメータ自動調整」などができる。

## utaupy.utauplugin

UTAUプラグインをつくるためのモジュール。utaupy.utauplugin.UtauPlugin クラスは utaupy.ust.Ust を継承し、プラグイン用に最適化した子クラス。

示例（将每个音符身高一个半音）

```Python
import utaupy

def notenum_plus1(utauplugin):
    """
    utauplugin: utaupy.utauplugin.UtauPlugin class object
    全てのノートを半音上げる
    """
    # 全ノートを取得
    notes = utauplugin.notes
    # 半音上げ
    for note in notes:
        note.notenum += 1

if __name__ == '__main__':
    # automatically
    # read the utau plugin script
    # load as utaupy.utauplugin.UtauPlugin class object
    # overwrite the utau plugin script
    utaupy.utauplugin.run(notenum_plus1)
```

## 联系方式

- Twitter: @oatsu_c

- GitHub: oatsu-gh
