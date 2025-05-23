This is a platform-specific how-to guide. For general protocol guides, see morpheus-how-to-guides.md.

## For Developers

This README will guide you on building a Docker container for agent execution as well as a desktop UI app.
You may instead simply download the [pre-built app](README.md)

#### Windows
1. Ensure you have Python, Pip, [Docker Desktop](https://www.docker.com/products/docker-desktop/), and Git installed on your Windows machine. Note: please install python version 3.10.0+, older versions will produce outdated versions of tkinter when running the requirements install.

2. Clone the repository using Command Prompt or PowerShell:
```shell
> git clone https://github.com/LachsBagel/moragents.git
> cd moragents
```

3. Build the Docker Image for Local Agent Execution:
```shell
> docker build -t morpheus/price_fetcher_agent -f agents/morpheus_price_agent/agent/Dockerfile agents/morpheus_price_agent/agent
```

If we have run this command before, run this to clear the old docker image.
```shell
docker rmi morpheus/price_fetcher_agent
```

4. Install Deps for UI, Recommended to use virtualenv
```shell
> python -m venv .venv
> Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
> .\.venv\Scripts\Activate.ps1
> pip install -r requirements.txt
```

6. Build App for Local Installation
```shell
pyinstaller --runtime-hook runtime_hook_windows.py --name="MORagentsWindows" --icon="moragents.ico" main.py
```
There is a known and common issue where pyinstaller will trigger Windows Defender (see [here](https://stackoverflow.com/questions/54733909/windows-defender-alert-users-from-my-pyinstaller-exe) for more details). If there is a security warning, perform the following:

- Open Windows Security: Go to Start > Settings > Update & Security > Windows Security > Virus & threat protection.
- Manage Settings: Under Virus & threat protection settings, select "Manage settings."
- Add or remove exclusions: Scroll down to "Exclusions" and select "Add or remove exclusions."
- Add an exclusion: Select "Add an exclusion" and choose the folder where your project is located.

More details located [here](https://support.microsoft.com/en-us/windows/add-an-exclusion-to-windows-security-811816c0-4dfd-af4a-47e4-c301afe13b26)

7. The compiled executable will be located in the dist folder. You can create a shortcut to the MORagents.exe file for easy access.
8. Double-click the MORagents.exe file to open the MORagents app on your Windows machine. Make sure Docker is running before opening MORagents.

---

MacOS build instructions can be found [here](README_MACOS_DEV_BUILD.md)
