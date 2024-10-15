## WindowsでMorpheusをインストールする方法

- 最初に、WSL2をインストールする必要があります。次のコマンドを管理者のコマンドプロンプトで実行することで、WSL2をインストールできます: `wsl --install`。その後、WSL2を開き、`wsl`を入力して設定を行ってください。

- 次に、`curl https://ollama.ai/install.sh | sh`を実行して、ollamaをインストールします。

- その後、`sudo apt-get update`と`sudo apt-get install python3`を実行して、Pythonをインストールします。

- そして、`pip3 install gdown`を実行します。

- これで、morpheusのdpkgをダウンロードできます。次のコマンドを実行してください: `gdown https://drive.google.com/uc?id=1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB`。

- Morpheusのダウンロードファイルの正当性を確認するために、`sha1sum morpheus_0.0.5_amd64.deb`を使用してください。ハッシュ値`b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5`と一致することを確認してください。一致しない場合は、インストールプロセスを中止してください。

- 次に、`sudo dpkg -i morpheus_0.0.5_amd64.deb`を実行してください。インストールが最初に失敗した場合は、依存関係をインストールしてから再試行してください。

- これで、依存関係エラーがなくmorpheusがインストールされている場合は、2つのコマンドラインウィンドウを開き、両方で`wsl`を入力して、2つのWSL2ウィンドウを開いてください。その後、一つのウィンドウで`ollama serve`を実行し、もう一つのウィンドウで`morpheus`を実行してください。

