# 04. Kubernetesオブジェクトを使った作業

## Pod, Deployment, Service

* Pod = "クジラの群れ"
    * Kubernetesのタスクの基本単位
    * 一緒にスケジュールされている単一のコンテナーまたは相互に通信可能なコンテナグループを指定
* Deployment
    * Podを宣言的に管理し、必要に応じてそれらをデプロイ、スケジューリング、更新、および再起動する抽象的なKubernetesリソース
* ReplicaSet
    * 同一のPodのグループ(=レプリカ)について責任をもつ
    * マニフェスト（=YAML）で指定されたレプリカの数を制御する
    * マニフェストで指定された状態と比較して、ポッドが少なすぎる（または多すぎる）場合、ReplicasSetコントローラーはいくつかのポッドを開始（または停止）して状況を修正する。
* Service
    * Kubernetesにおけるロードバランサーまたはプロキシに相当するもの
    * 永続的に有効な単一のIPアドレスまたはDNS名を介して、トラフィックを対応するポッドにルーティングする
* 調整ループ(reconsiliation loop)
    * Kubernetesコントローラが各リソースによって指定された目的の状態をクラスタの実際の状態と比較してチェックし、それらを同期させるために必要な調整を行う仕組み
* Kubernetes Scheduler
    * どのノードでもまだ実行されていないPodを監視し、そのノードのsuitalbeノードを見つけて、そのノードのkubeletにPodを実行するように指示する。
    * 参照：
        * https://jvns.ca/blog/2017/07/27/how-does-the-kubernetes-scheduler-work/
* kubectl
    * KubernetesコントロールプレーンのAPIにアクセスできるCLIツール
* helm (=舵)
    * Kubernetesのパッケージマネージャ
* helm chart
    * helm のパッケージをこう呼ぶ

![deployments-replicasets-and-pods](https://i.imgur.com/UHgZbAA.jpg)

出典： [Kubernetesを使ったCloud Native DevOps](https://www.nginx.com/resources/library/cloud-native-devops-with-kubernetes/)
