# openshift_airgap_install

OpenShift Container Platform 4.21 を Agent-based Installer で閉域導入するための手順書と、検証用テンプレートをまとめたリポジトリーです。

## 収録ファイル

### `openshift_agentbasedinstall_airgap.md`

Agent-based Installer を用いて閉域環境へ OpenShift を導入するための手順書です。既存の DNS / NTP を利用でき、閉域内へ汎用パッケージの搬入と導入が済んでいる前提で、外部側での資材取得、閉域搬入、ミラーレジストリー準備、`install-config.yaml` と `agent-config.yaml` の作成、Agent ISO 生成、インストール確認までを扱います。

### `openshift_agentbasedinstall_airgap_sample.md`

`openshift_agentbasedinstall_airgap.md` の手順に加え、閉域内で利用する作業ホストに汎用パッケージの搬入と導入、DNS / NTP の設定を行います。CloudFormation テンプレート（`ocp-airgap-aws-test-cloudformation.yaml`）を使う場合は、利用前に EC2 キーペアを用意します。

### `ocp-airgap-aws-test-cloudformation.yaml`

`openshift_agentbasedinstall_airgap_sample.md` の手順を AWS 上で検証するための CloudFormation テンプレートです。EC2 キーペアはテンプレート内では作成しないため、事前に用意します。

## 想定用途

- OpenShift 閉域インストール手順書の版管理
- 検証環境での air-gap インストール手順の共有
- AWS 上のテスト用インフラテンプレートの保管