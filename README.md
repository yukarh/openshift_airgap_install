# openshift_airgap_install

OpenShift Container Platform 4.21 を Agent-based Installer で閉域導入するための手順書と、検証用 AWS テンプレートをまとめたリポジトリーです。

## 収録ファイル

### `openshift_agentbasedinstall_airgap.md`

既設の DNS / NTP の利用を前提に整理した、標準的な閉域インストール手順書です。外部側での資材取得、閉域搬入、ミラーレジストリー準備、`install-config.yaml` と `agent-config.yaml` の作成、Agent ISO 生成、インストール確認までを扱います。

### `openshift_agentbasedinstall_airgap_sample.md`

サンプル値を多く含む検証向け手順書です。AWS CloudFormation で検証環境を作る流れや、閉域内作業ホストへの標準パッケージ導入など、PoC やラボで再現しやすい補足をまとめています。利用前に EC2 キーペアを用意します。

### `ocp-airgap-aws-test-cloudformation.yaml`

Agent ISO 作成までの閉域ワークフローを AWS 上で検証するための CloudFormation テンプレートです。download host、work host、SNO dummy 用の EC2、VPC / サブネット、セキュリティグループ、RHEL 9 AMI と SNO MAC アドレスの自動解決用 Lambda-backed custom resource を定義します。EC2 キーペアはテンプレート内では作成しないため、事前に用意して `LabKeyName` へ渡します。

## 想定用途

- OpenShift 閉域インストール手順書の版管理
- 検証環境での air-gap インストール手順の共有
- AWS 上のテスト用インフラテンプレートの保管