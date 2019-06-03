# Kubernetes のアーキテクチャ

## コントロールプレーン

* クラスターの「脳」
* Kubernetesが仕事をするために必要なすべてのタスクを実行します。
    * スケジューリング
    * サービスの管理
    * APIリクエストの処理
    * etc.
* コントロールプレーンは以下のコンポーネントで構成されています:
    * kube-apiserver
        * API要求を処理するコントロールプレーンのフロントエンドサーバー
    * etcd
        * Kubernetesがすべての情報を保存しているデータベース
            * どのようなノードが存在するか？
            * クラスタにはどのようなリソースがあるか？
            * etc.
    * kube-sceduller
        * 新しく作成したPodをどこで実行するかを決定します。
    * kube-controller-manager
        * リソースコントローラの実行を担当します。例） Deployments
    * cloud-controller-manager
        * クラウドプロバイダとやり取りする
            * リソースを管理する
                * ロードバランサ
                * ディスクボリューム
                * etc.
* マスターノード
    * コントロールプレーンコンポーネントを実行するクラスタのメンバ

## ノードコンポーネント

* ワーカーノード
    * ユーザーワークロードを実行するクラスターメンバー
* Kubernetesクラスタの各ワーカーノードはこれらのコンポーネントを実行します。
    * kubelet
        * ノードでスケジュールされているワークロードを開始するようにコンテナランタイムを駆動し、そのステータスを監視する責任があります。
    * kube-proxy
        * 異なるノード上のPod間、およびPodとインターネット間の要求をルーティングするネットワーキングを行います。
    * コンテナランタイム
        * 実際にコンテナを起動および停止し、それらの通信を処理します。
        * 通常Dockerですが、KubernetesはrktやCRI-Oなどの他のコンテナランタイムをサポートします。

![kubernetes-components](https://i.imgur.com/LC7Uexl.jpg)
出典: *[Cloud Native DevOps With Kubernetes](https://www.nginx.com/resources/library/cloud-native-devops-with-kubernetes/)*
