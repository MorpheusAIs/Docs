## Installieren von Morpheus unter Windows

- Installieren Sie zunächst WSL2, indem Sie `wsl  --install` in einer Admin-Eingabeaufforderung. Öffnen Sie dann WSL2 mit `wsl` und folgen Sie dem Setup-Prozess.
    
- Dann laufen `curl https://ollama.ai/install.sh | sh` um ollama zu installieren.

- Dann installieren Sie Python, indem Sie `sudo apt-get update` und `sudo apt-get install python3`.

- Dann laufen `pip3 install gdown`.

- Laden Sie nun das Morpheus dpkg herunter, indem Sie `gdown https://drive.google.com/uc?id=1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB`.

- Überprüfen Sie die Integrität des Herunterladens von Morpheus durch `sha1sum morpheus_0.0.5_amd64.deb`. sicherstellen, dass sie mit dem Hash übereinstimmt `b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5`, sonst brechen Sie den Installationsvorgang ab.

- Dann laufen `sudo dpkg -i morpheus_0.0.5_amd64.deb`, Wenn die Installation zunächst fehlschlägt, installieren Sie die Abhängigkeiten, und versuchen Sie es erneut.

- Sobald Morpheus ohne Abhängigkeitsfehler installiert ist, öffnen Sie 2 WSL2-Fenster, indem Sie 2 Kommandozeilenfenster öffnen und in beiden wsl eingeben, dann führen Sie in einem davon `ollama serve` und im anderen `morpheus` aus.

