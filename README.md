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
- INI, UST, LAB 文件互转（但这些文件类型不完全兼容，转换很可能是不可逆的）

# Methods
## utaupy.ust
### Ust(collections.UserList)
UST文件类
### load(path)
读取UST文件，返回Ust对象
```Python
ustobj = utaupy.ust.load(path)
print(type(ustobj))
# <class 'utaupy.ust.Ust'>
```

## utaupy.otoini
处理UTAU原音设定的模块
### class utaupy.otoini.OtoIni(collections.UserList)
oto.ini文件类
### class utaupy.otoini.Oto(collections.UserDict)
oto.ini原音设定条目类
## utaupy.table
假名与罗马音转换模块

## utaupy.convert
Ust オブジェクト、OtoIni オブジェクト、Label オブジェクトなどを変換するモジュール。

## utaupy.reaper
处理Reaper CSV文件的模块

## utaupy.utau
实现了UTAU编辑器从音源库中调取音频和原音设定的功能，支持自动参数调整

## utaupy.utauplugin
用于编写UTAU插件。utaupy.utauplugin.UtauPlugin继承自utaupy.ust.Ust，为插件开发优化

示例（将每个音符升高一个半音）

```Python
import utaupy

def notenum_plus1(utauplugin):
    """
    utauplugin: utaupy.utauplugin.UtauPlugin class object
    全てのノートを半音上げる
    """
    # 获取所有音符
    notes = utauplugin.notes
    # 升高一个半音
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
