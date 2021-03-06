# Glacier
## 概要
- S3と同様の`耐久性`を持つ
- 容量あたりの`コスト減`のアーカイブストレージ
- データの取り出しに時間がかかる
- 自動採番のアーカイブIDで管理
- APIでの操作か、S3の`ライフサイクル管理`でデータ保存

## ユースケース
- 長期保存
- アクセス頻度が低い
- 取り出し時間が長い
  
## Glacierの構成要素
- ボールト
> アーカイブの保存ん領域。`S3のバケット`に相当。
- アーカイブ
> 格納されるデータ自身。S3のオブジェクトに相当。  
> 一位のアーカイブIDとオプションの説明が割当。  
> 138バイトのランダムな文字列
- インベントリ
> 書くボールトのアーカイブ情報を収集。  
> 更新頻度は1日1回程度。  
> マネジメントコンソールか、`ListVaultsAPI`でリアルタムに確認。
- ジョブ
> アーカイブやインベントリに対して、検索やダウンロードなどの`要求を処理・実行・管理`する。

## データの取り出しオプション
- 高速・標準・バルクの3種のリクエストオプションがある。
- 待ち時間が短いほど費用が高くなる。
  
## Glacier Select
アーカイブに対してSQLを実行して、データを抽出する。  
対象は`非圧縮のCSV形式のみ`などの条件がある。

## データ暗号化
データを保存するときには、SSLを使った転送が行われる。  
データは標準で暗号化される。  
独自の暗号化は保存前に実施する。


