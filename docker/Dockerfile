FROM ubuntu:22.04

# pip外のパッケージのインストール
RUN apt-get update && \ 
    apt-get install  -y \
    build-essential cmake curl git pkg-config \
    libopenblas-dev liblapack-dev gfortran \
    libgeos-dev \
    python3

WORKDIR /workspace

# ryeのインストール
ENV RYE_HOME="/opt/rye"
ENV PATH="$RYE_HOME/shims:$PATH"
RUN curl -sSf https://rye-up.com/get | RYE_NO_AUTO_INSTALL=1 RYE_INSTALL_OPTION="--yes" bash

# 依存ファイルのコピー
COPY pyproject.toml .
COPY .python-version .
COPY requirements.lock .
COPY requirements-dev.lock .
RUN touch README.md

# pipパッケージのインストール
RUN rye sync --no-lock

# 仮想環境の有効化
RUN . .venv/bin/activate