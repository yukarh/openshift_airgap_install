# openshift_airgap_install

OpenShift Container Platform 4.21 を Agent-based Installer で閉域導入するための手順書と、検証用 AWS テンプレートをまとめたリポジトリーです。

## 事前準備

- `ocp-airgap-aws-test-cloudformation.yaml` は EC2 キーペアを自動作成しません。
- スタック作成前に、デプロイ先リージョンで EC2 キーペアを事前に作成してください。
- `LabKeyName` の既定値は `ocp-airgap-lab` です。パラメーターを変更しない場合は、この名前でキーペアを用意します。

## 収録ファイル

### `openshift_agentbasedinstall_airgap.md`

既設の DNS / NTP の利用を前提に整理した、標準的な閉域インストール手順書です。外部側での資材取得、閉域搬入、ミラーレジストリー準備、`install-config.yaml` と `agent-config.yaml` の作成、Agent ISO 生成、インストール確認までを扱います。

### `openshift_agentbasedinstall_airgap_sample.md`

サンプル値を多く含む検証向け手順書です。閉域内作業ホストへの DNS / NTP / ミラーレジストリー同居や、必要 RPM の持ち込みなど、PoC やラボで再現しやすい補足を含みます。

### `ocp-airgap-aws-test-cloudformation.yaml`

Agent ISO 作成までの閉域ワークフローを AWS 上で検証するための CloudFormation テンプレートです。download host、work host、SNO dummy 用の EC2、VPC / サブネット、セキュリティグループ、RHEL 9 AMI と SNO MAC アドレスの自動解決用 Lambda-backed custom resource を定義します。テンプレートの対象は検証環境であり、OpenShift ノードへの ISO 接続や起動までは行いません。

## 想定用途

- OpenShift 閉域インストール手順書の版管理
- 検証環境での air-gap インストール手順の共有
- AWS 上のテスト用インフラテンプレートの保管