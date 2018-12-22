# THE@TER BOOST! 得票数推移データ

[![CC BY-NC-SA 4.0](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode.ja)

シアターデイズにて開催されていたアイドル投票イベント、「THE@TER BOOST!」の **非公式な** 得票状況推移データです。

## データ利用における注意点について

- 当データはシアターデイズ非公式ポータルサイト、 [@TheaterGate](https://github.com/TheaterGate) が収集した非公式なデータです。データの信頼性は保証できません。
- このデータにはイベント開始1時間後の `2017-12-16T01:00:00+09:00` からイベント終了10分前 `2018-01-22T23:50:00+09:00` までのデータが含まれています。 **最終結果は含まれていません。**
- イベント終了30分前からデータ取得頻度を10分毎に変更したため、終了時刻付近のデータには頻度にばらつきがあります。
- ライセンスは [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode.ja) です。ライセンスを確認し、それに従い利用してください。
  - 広告が掲載されているサイトにおける利用は **営利目的** と見なします。そのようなサイトではライセンス違反となり、当データの利用はできません。
- 「利用方法が違反に値するかどうかわからない」、「他のフォーマットを追加してほしい」などの要望は [Issueを立てる](https://github.com/theaterdays-diary/theater-boost/issues) か、 [TheaterGate@Twitter](https://twitter.com/TheaterGate) または [CrescentApricot](https://crescentapricot.github.io) に記載の連絡先までご連絡ください。

## ファイル一覧

ファイル名|形式|エンコーディング|備考
---|---|---|---
theater-boost.ap.csv|csv|utf-8|
theater-boost.ap.excel.csv|csv|shift_jis|Excelで読み込めそうな形に加工
theater-boost.ap.dt.int.json|json|utf-8|
theater-boost.ap.dt.str.json|json|utf-8| `int` を `str` に置換
theater-boost.metadata.json|json|utf-8|おまけのメタデータです。

各フォーマットにおける仕様を以下に示します。

### `.csv` 形式について

- 1行目はヘッダーになっており、`datetime,subject,idol,rank,score` という具合で各列の内容を示しています。
- 対応表を以下に示します。

項目|意味
---|---
datetime|集計時刻が `ISO 8601` の拡張形式で入っています。<br>フォーマット: `YYYY-MM-DDThh:mm:ss+09:00`<br>サンプル: `2017-12-16T01:00:00+09:00`
subject|役の名前が入っています。<br>サンプル: `新入生`
idol|アイドルの名前が入っています。名字と名前の間に区切りはありません。<br>サンプル: `春日未来`
rank|順位が入っています。<br>サンプル: `1`
score|得票数が入っています。<br>サンプル: `765`

#### `.excel.csv` について

Excelとかで使う人もいそうなので、タイムスタンプを `YYYY-MM-DD hh:mm:ss` にしてエンコーディングを `shift_jis` にしたものも用意しました。使わないので、開いて文字化けしないぐらい程度しか確認していません。

### `.json` 形式について

多分少しjsonらしいフォーマットからは外れてしまっています。<br>
時刻ごとの辞書がリストになっています。<br>
idがそのままになっているものと、日本語に置き換えてあるものの2種用意しています。

- そのまま (`.int.json`)

```json
[
  {
    "1": {
      "1": {
        "idol": 29,
        "score": 342
      },
    },
    "datetime": "2017-12-16T01:00:00"
  },
]
```

- 置き換え (`.str.json`)

```json
[
  {
    "新入生": {
      "1": {
        "idol": "高坂海美",
        "score": 342
      },
    },
    "datetime": "2017-12-16T01:00:00"
  },
]
```

## ダウンロード

本リポジトリの [Releases](https://github.com/theaterdays-diary/theater-boost/releases) からダウンロードできます。
