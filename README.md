# article-template2
破壊的な変更しかし変わらない成果物

# WORD記事の雛形実験版

これはhidarumaが個人的に実験中の、WORD記事の雛形です。

## 使い方

### macOS・Linux

1. `git clone https://github.com/hidaruma/article-template2.git`
2. `cd ./article-template2`
3. `git submodule update --init`
4. `cd ./articles`
5. `cp -r ./hinagata ./my-article-name`
6. `cd ./my-article-name`
7. `autoconf`
8. `./configure`
9. `make`

## 「文　編集部」の消し方

WORD編集部の人間ではない場合、著者の前に付く「文　編集部」を削除したくなると思います。そういう場合は`makearticletitle`の前に
次のようなコマンドを追加してください。

```TeX
\authormark{}
```

## 偶数頁

レイアウトの問題で、偶数頁から開始していただくことがあります。その場合、クラスファイルオプションを以下のようにしてください。

```TeX
\documentclass[evenstart]{word}
```

## 何か良く分からないけどフォントがヒラギノにならない
ヒラギノフォントが入っていない場合はmacOSにしてヒラギノフォントを入手する、ヒラギノ書体を買うなどをしてください。
フォントがtexliveに認識されているがヒラギノにならない場合、先ず`kanji-config-updmap hiragino-pron`を打ってください。
LuaLaTeX、XeLaTeXで上記コマンドを打ってもヒラギノ書体で出力されない場合、`kpsewhich updmap.cfg`で表示されたupdmap.cfg
に`kanjiEmbed hiragino-pron`を追記してください。

OSのバージョンがEl Capitanである、などの場合はGoogle検索をするなどをしてください（後日追記の可能性有り）。

## 質問

@hidarumaへ。

## ライセンス

see LICENSE