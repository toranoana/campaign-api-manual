# お知らせ

2022年8月1日（月）をもちまして、虎の穴キャンペーンAPIの提供を終了いたします。

ご利用の皆様には、ご不便・ご迷惑をおかけし、大変申し訳ございません。
今後とも虎の穴キャンペーンをよろしくお願いいたします。

# 虎の穴キャンペーンサイトAPIマニュアル
## 本マニュアルについて
本マニュアルでは、虎の穴キャンペーンサイトが提供するAPI（キャンペーンAPI）の仕様をご確認いただけます。

## 機能一覧
キャンペーンAPIには以下のような機能があります。
1. 現在応募可能なキャンペーン一覧を取得する
2. 応募期間を指定してキャンペーン一覧を取得する
3. キャンペーンの詳細画面を取得する

## 共通パラメータ
キャンペーンAPIの利用には共通のAPIキーの設定が必要です。
以下のパラメータをHTTPヘッダーに追加します。
```
x-tapi-key	"gijutsu5"
x-tuser-key	"1008"
```

## 取得情報
キャンペーンAPIで取得できる情報は以下の通りです。取得情報は全機能共通です。

<table>
  <tr>
    <th colspan=2>キー名</th><th>データ型</th><th>説明</th>
  </tr>
  <tr>
  <tr>
    <td>data</td><td></td><td>object</td><td>キャンペーン情報が入ります</td>
  </tr>
  <tr>
    <td></td><td>id</td><td>number</td><td>キャンペーンID</td>
  </tr>
  <tr>
    <td></td><td>title</td><td></td>string<td>キャンペーン名称<td>
  </tr>
  <tr>
    <td></td><td>description</td><td>string</td><td>概要<td>
  </tr>
  <tr>
    <td></td><td>campaign_url</td><td>string</td><td>キャンペーン詳細ページURL<td>
  </tr>
  <tr>
    <td></td><td>image_url</td><td>string</td><td>キャンペーン画像URL<td>
  </tr>
  <tr>
    <td></td><td>publish_at</td><td>string</td><td>公開日（キャンペーンが抽選サイトに表示される日付）※<td>
  </tr>
  <tr>
    <td></td><td>publish_at_unix_timestamp</td><td>number</td><td>公開日UNIXタイムスタンプ<td>
  </tr>
  <tr>
    <td></td><td>start_at</td><td>string</td><td>応募開始日※<td>
  </tr>
  <tr>
    <td></td><td>start_at_unix_timestamp</td><td>number</td><td>応募開始日UNIXタイムスタンプ<td>
  </tr>
  <tr>
    <td></td><td>end_at</td><td>string</td><td>応募終了日※<td>
  </tr>
  <tr>
    <td></td><td>end_at_unix_timestamp</td><td>number</td><td>応募終了日UNIXタイムスタンプ<td>
  </tr>
  <tr>
    <td></td><td>is_adult</td><td>boolean</td><td>成人向けフラグ<td>
  </tr>
</table>
※ string型の日付は"YYYY年MM月DD日 HH時mm分SS秒"の形で取得されます。

## 1. 現在応募可能なキャンペーン一覧を取得する
現在応募可能なキャンペーン一覧を取得します。
### エンドポイント
https://campaign.toranoana.jp/api/v1/campaign/opened

curlコマンドでの呼び出し
```
curl --header "x-tapi-key:gijutsu5" --header "x-tuser-key:1008" "https://campaign.toranoana.jp/api/v1/campaign/opened"
```

## 2. 応募期間を指定してキャンペーン一覧を取得する
特定の応募期間に応募できるキャンペーンの一覧を取得します。
### エンドポイント
https://campaign.toranoana.jp/api/v1/campaign/search?start_at=YYYYMMDD&end_at=YYYYMMDD

curlコマンドでの呼び出し
```
curl --header "x-tapi-key:gijutsu5" --header "x-tuser-key:1008" "https://campaign.toranoana.jp/api/v1/campaign/search?start_at=20180901&end_at=20180930"
```
## 3. キャンペーンの詳細画面を取得する
一意のキャンペーン詳細情報を取得します。
### エンドポイント
https://campaign.toranoana.jp/api/v1/campaign/:id  
※:idは表示させたいキャンペーンのIDです。

curlコマンドでの呼び出し
```
curl --header "x-tapi-key:gijutsu5" --header "x-tuser-key:1008" "https://campaign.toranoana.jp/api/v1/campaign/:id"
```

---
APIへのご意見、ご要望は[虎の穴ラボ公式twitter](https://twitter.com/toranoana_lab)までお願いいたします。
