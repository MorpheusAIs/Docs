## 在Windows上安装Morpheus

- 首先，必须先安装 WSL2，你可以通过在管理员命令提示符下运行 `wsl --install` 来做到这一点。然后打开 WSL2，输入 `wsl` 并跟随设置过程。

- 然后运行 `curl https://ollama.ai/install.sh | sh` 来安装ollama。

- 接着通过运行 `sudo apt-get update` 和 `sudo apt-get install python3` 来安装 python。

- 然后运行 `pip3 install gdown`。

- 现在你可以下载 morpheus dpkg。 请运行 `gdown https://drive.google.com/uc?id=1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB`。

- 通过使用 `sha1sum morpheus_0.0.5_amd64.deb` 验证 Morpheus 下载文件的完整性。确保它与哈希值 `b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5` 匹配，否则中止安装过程。

- 接下来，运行 `sudo dpkg -i morpheus_0.0.5_amd64.deb`，如果安装初次失败，安装依赖项然后再试一次。

- 现在一旦你安装了 morpheus 而没有任何依赖错误，通过打开2个命令行窗口并在两者中输入 wsl 来打开2个 WSL2 窗口，然后在其中一个上运行 `ollama serve`，在另一个上运行 `morpheus`。
