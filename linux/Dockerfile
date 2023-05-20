FROM python:3.8-buster

# ホストマシンのコードをコンテナにコピー
COPY src C:\src
WORKDIR C:\src

# 依存関係のインストール
RUN pip install --no-cache-dir pyinstaller
