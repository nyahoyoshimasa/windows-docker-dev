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
- 上記のwslがインストール完了とでたら、再起動する
- 再起動後自動で以下のようなUbuntuアプリが起動する
- 今後の便利のため、ユーザを作成しておく
  ```
  $ adduser <好きなユーザ名>
  Adding user `user_name' ...
  Adding new group `user_name' (1002) ...
  Adding new user `user_name' (1002) with group `user_name' ...
  Creating home directory `/home/user_name' ...
  Copying files from `/etc/skel' ...
  Enter new UNIX password:  # パスワード入力
  Retype new UNIX password: # パスワード入力（確認）
  passwd: password updated successfully
  Changing the user information for user_name
  Enter the new value, or press ENTER for the default
        Full Name []:    # Enterでスキップする
        Room Number []: # Enter
        Work Phone []: # Enter
        Home Phone []: # Enter
        Other []: # Enter
  Is the information correct? [Y/n] Y  # Yes
  ```
- PowerShellでWSL2が有効になっていることを確認する
  ```
  $ wsl -l -v
    NAME      STATE           VERSION
  * Ubuntu    Running         2
  ```
- エクスプローラーを開き、上部のリンクを入れる部分に`\\wsl$\`と入れると`Ubuntu`のファイルシステムにアクセスできる
- PowerShellからも、以下でアクセスできる
  ```
  $ cd \\wsl$\Ubuntu
  ```
- Ubuntuのapt updateをしておく
  - Ubuntuアプリを開き、以下のコマンドを実行して、update(windowsのように自動的に行ってくれるものではない)
    - 結構時間かかるので、コマンドだけ実行して放置しとくといい(途中でインストールしていい？と聞かれるのでYを入力してEnter)
    ```
    sudo apt update && sudo apt upgrade
    ```
### Windows Terminalをインストール
正直、VSCodeで最終的にいろいろ操作するようにするので、いらないといえばいらないが、PowerShellがマルチウィンドウに適してなさそうなのが気に入らないので導入
- https://aka.ms/terminal から入手
