## 概要
windows10でなるべくきれいにかつ、リサイクル可能なCPythonの実行環境を考える
## 試行スペック
- Windows 10
- 64bit(x64)
- cpu: intel core i7-8550U@1.80GHz(max: 1.99)
- RAM: 16.0GB
## 作業ログ
### WSL2のインストール
#### WSL2とはなにか
WSL2(Windows Subsystem for Linux 2)はwindows上でlinuxライクなシステムコマンドを実行できる.
(もう少しいうとWindowsが持つ専用のVM上に建てられた専用パッチをあてたLinuxカーネル上で実行される)
#### install 手順
- PowerShellを開き以下を実行
  ```
  $ wsl --install
  ```
  上記実行時に以下が出てくる場合はWindowsのバージョンが足りていないのでアップデートする
  ```
  wsl : 用語 'wsl' は、コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されません。(以下略)
  ```
