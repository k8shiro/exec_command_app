FROM centos/python-38-centos7

USER root

# ホストマシンのコードをコンテナにコピー
COPY ./src /src
WORKDIR /src

# 依存関係のインストール
RUN pip install --no-cache-dir pyinstaller