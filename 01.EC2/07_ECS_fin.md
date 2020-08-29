# ECS
- Dockerコンテナを提供する
- Docker環境に必要な設定が含まれた、`EC2インスタンス`が起動
- セキュリティ面の特徴として、`Task`ごとに`IAMロール`を割り当てる
- EC2は`インスタンス単位`だが、`ECS`は同じCluster上で起動する`Task`ごとに別のIAMロールを付与できる
    
    例：
    - Webサーバ用のTaskにはSQSへのSendMessage権限のみ
    - 同じCluster上で動くバッチサーバTaskにはSQSからのReceiveMessageとS3からのGetObject権限のみ付与
  
## その他コンテナサービス
### AWS Fargate
ECSではCluster用のEC2が必要だが、AWSFargateは`EC2を使わずに動かすことができる`サービス。  
ECSでTaskを定義するときはEC2かFargateか選択できる。

> Clusterの管理が不要

> 利用料は各タスクに割り当てるCPUとメモリに応じて決まる

### EKS (Amazon Elastic container service for KuberneteS)
コンテナ管理の自動化のためのオープンソフトプラットフォーム。  
マスター用のEC2インスタンスを管理する必要がなくなる。

### ECR (Amazon Elastic Container Registry)
Dockerのコンテナイメージを管理するレジストリを提供。  
レジストリへのPull/Push権限をIAMで管理可能。
