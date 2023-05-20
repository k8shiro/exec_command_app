FROM mcr.microsoft.com/windows/servercore:ltsc2019

# Pythonのインストール
RUN powershell -Command "Invoke-WebRequest -Uri https://www.python.org/ftp/python/3.8.12/python-3.8.12-amd64.exe -OutFile python-installer.exe" ; \
    Start-Process python-installer.exe -ArgumentList '/quiet', 'InstallAllUsers=1', 'PrependPath=1' -Wait ; \
    Remove-Item -Force python-installer.exe

# ホストマシンのコードをコンテナにコピー
COPY ./src /src
WORKDIR /src

# 依存関係のインストール
RUN pip install --no-cache-dir pyinstaller