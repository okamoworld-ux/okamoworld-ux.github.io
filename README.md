# 患者さん向け資料サイト

耳鼻咽喉科の患者さん向け資料を、QRコード経由で配布するためのサイト。

## サイトの仕組み

- ルート（資料一覧）: `https://ユーザー名.github.io/`
- 各資料の個別ページ: `https://ユーザー名.github.io/トピック名/`
- すべてのページに `noindex` を設定済み + `robots.txt` でサイト全体を検索除外
- → 検索結果には出ないが、URLを直接知っていれば誰でも閲覧可能

## ファイル構成

```
/
├── index.html          ← 資料一覧（トップページ）
├── robots.txt          ← 検索クローラー除外設定
├── README.md           ← このファイル
└── nosebleed/          ← 1つ目の資料
    ├── index.html
    └── leaflet.png
```

## 新しい資料を追加する手順

### 1. フォルダを作る

ローカルなら、新しいトピック名のフォルダを作成（英数字・ハイフンのみ。例: `dizziness`, `post-op-tonsil`）。

GitHub のWeb UI で作る場合は、「Add file → Create new file」でファイル名に `dizziness/index.html` のように `/` を含めて入力するとフォルダが自動的に作られる。

### 2. ファイルを置く

新フォルダに以下の2つを置く：

- `index.html` — `nosebleed/index.html` をコピーして編集（タイトル・本文・改訂日を差し替え）
- `leaflet.png` — リーフレット画像

### 3. トップに項目を追加

ルートの `index.html` を開き、`<ul class="list">` の中に新しい `<li>` を追加：

```html
<li>
  <a href="./dizziness/">
    <span class="title">めまいが出たときの過ごし方</span>
    <span class="arrow">VIEW &rarr;</span>
  </a>
</li>
```

### 4. QRコード化

- URL（例: `https://ユーザー名.github.io/dizziness/`）を確定
- [qr.io](https://qr.io) などに貼ってQRコードを生成
- リーフレットの右下スペース（約2cm × 2cm）に印刷

## 改訂時

- 該当ページの `index.html` の改訂日を更新
- `leaflet.png` を新しいバージョンに差し替え
- GitHub上で commit すれば改訂履歴が自動で残る（誰がいつ何を変えたか追跡可能）

## 監修者の表示について

現状は無記名（「耳鼻咽喉科」のみ）にしてある。所属組織名（大学・病院）を載せる場合は、組織側の許可を得てから記載すること。

## 注意事項

- 公開リポジトリなので、患者個人情報・症例情報を含めないこと
- 一般的な指導内容のみ掲載
- 医療上の判断を促すような記述は避け、「主治医に相談を」を必ず添える
