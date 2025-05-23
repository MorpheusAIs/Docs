This is a platform-specific how-to guide. For general protocol guides, see morpheus-how-to-guides.md.

## For Developers

This README will guide you on building a Docker container for agent execution as well as a desktop UI app.
You may instead simply download the [pre-built app](README.md)

#### macOS
1. Ensure you have Python, Pip, [Docker Desktop](https://www.docker.com/products/docker-desktop/), and Git installed. Note: please install python version 3.10.0+, older versions will produce outdated versions of tkinter when running the requirements install.


2. Clone Repo
```shell
 $ git clone https://github.com/LachsBagel/moragents.git
 $ cd  moragents
```

3. Build Docker Image for Local Agent Execution

```shell
For ARM (M1, M2, M3) 
    $ docker build -t morpheus/price_fetcher_agent -f agents/morpheus_price_agent/agent/Dockerfile-apple agents/morpheus_price_agent/agent

For Intel (x86_64)
    $ docker build -t morpheus/price_fetcher_agent -f agents/morpheus_price_agent/agent/Dockerfile agents/morpheus_price_agent/agent
```


4. Install Deps for UI, Recommended to use virtualenv
```shell
 $ python3 -m venv .venv
 $ . .venv/bin/activate
 $ pip install -r requirements.txt
```

5. Build App for Local Installation
```shell
 $  pyinstaller --windowed --runtime-hook runtime_hook.py --name="MORagents" --icon="moragents.icns" main.py
```
    # If you have issues, try
    python -m PyInstaller --windowed --runtime-hook runtime_hook.py --name="MORagents" --icon="moragents.icns" main.py

6. Install Application 
```shell
  $ cp dist/MORagents.app /Applications
```

7. Open the ```MORagents``` app on your Mac, Docker needs to be running before opening MORagents

--
### Signing, Notarization, and Stapling for Distribution
Instructions are [here](Packaging_Instructions_macOS.md).

--


Windows build instructions can be found [here](README_WINDOWS_DEV_BUILD.md)
