
# ビルドステージ
FROM node:22 AS builder

# アプリケーションのディレクトリを作成
WORKDIR /usr/src/app

# package.jsonとpackage-lock.jsonをコピー
COPY package*.json ./

# 依存関係をインストール
RUN npm install --production

# アプリケーションのソースコードをコピー
COPY . .

# 実行ステージ
FROM gcr.io/distroless/nodejs22-debian12

# ビルドステージからアプリケーションのディレクトリをコピー
COPY --chown=nonroot:nonroot --from=builder /usr/src/app /usr/src/app
USER nonroot

# 作業ディレクトリを設定
WORKDIR /usr/src/app
#ENTRYPOINT [ "/opt/draios/bin/instrument","/nodejs/bin/node" ]
CMD [ "index.js" ]
