FROM mcr.microsoft.com/windows/servercore:ltsc2019


# Chocolateyのインストール
#SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

RUN powershell -Command "Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))"

# Pythonのインストール
RUN powershell -Command "choco install -y python --version 3.8.10"


# ホストマシンのコードをコンテナにコピー
COPY ./src C:/app/src
WORKDIR C:/app/src

# 依存関係のインストール
RUN pip install --no-cache-dir pyinstaller

RUN powershell -Command "pyinstaller main.py --onedir --onefile --clean --distpath C:/windows/dist --workpath C:/windows/build --specpath C:/windows"