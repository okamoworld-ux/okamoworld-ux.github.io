# 臨床班調査「耳鳴」— 手段 A4：PubMed 検索

**結果：未実施（PubMed に届かず、指示どおり 1 回の試行で停止）**

- 実施日：2026-10-09
- 試したこと：`https://eutils.ncbi.nlm.nih.gov/entrez/eutils/einfo.fcgi?db=pubmed&retmode=json` に 1 回 GET
- 結果：`curl: (56) CONNECT tunnel failed, response 403`
- プロキシの記録：`eutils.ncbi.nlm.nih.gov:443 — connect_rejected`（gateway が CONNECT に 403 を返した＝この環境のネットワーク方針で拒否）
- このセッションでも、ネット設定で eutils.ncbi.nlm.nih.gov は許可されていない。

## CQ ごとの検索式／ヒット数／採った本数

| CQ | 検索式 | ヒット数 | 採った本数 |
|---|---|---|---|
| CQ1 慢性耳鳴の薬物療法（GL・薬ごとの SR）（指定 50） | 未作成（到達せず停止） | — | 0 |
| CQ2 薬物療法の効果の時間経過（指定 30） | 未作成 | — | 0 |
| CQ3 加齢性難聴＋耳鳴：補聴器・人工内耳・SG と薬（指定 30） | 未作成 | — | 0 |
| CQ4 新薬・神経調節（二刺激・rTMS・tDCS・VNS・Kv7）（指定 30） | 未作成 | — | 0 |
| CQ5 急性／慢性でエビデンスを分けているか（指定 30） | 未作成 | — | 0 |

## 本文（CQ ごとの文献表）

PubMed に届かなかったため、PMID・書誌は 1 件も取得していない。代わりの手段（Consensus など）で補ったり、記憶から PMID を書いたりはしていない（手段 A4 は他の手段から独立させるため）。

## 再実行に必要なこと

クラウド環境の設定（セッションのタイトルバーの環境メニュー → Edit → Network access）で、`eutils.ncbi.nlm.nih.gov` を Allowed domains に足す（「Allow package managers」のチェックは付けたまま）か、もっと広いアクセスレベルにする。手順：https://code.claude.com/docs/en/cloud-environments#network-access 。設定を保存した後に始めた新しいセッションで出し直す。

---

かかった時間：約 1 分（試行は 13 秒）／eutils 呼び出し回数：1 回（einfo 1 回、失敗）
