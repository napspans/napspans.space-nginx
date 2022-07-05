# napspans.space-nginx
napspans.space配下のルーティングを行うdocker

# 初期設定
## git clone
```
git clone https://githubusername:password@github.com/napspans/napspans.space-nginx.git
```
## .env
git clone後ルートディレクトリ/直下に`.env`ファイル下記の通り作成
- 本番環境
```
NGINX_DEFAULT_CONF=prod.default.conf
```
- テスト環境
```
NGINX_DEFAULT_CONF=dev.default.conf
```
環境によってコピーするnginx設定ファイル`default.conf`を分けている。

## compose
ビルド&起動
```
docker-compose up -d
```
停止
```
docker-compose down
```
ビルドで認証関係の失敗する場合はdocerのjsonファイルを書き換え
```
nano  ~/.docker/config.json
```
```
{
  "credStore": "desktop.exe"
}

▼▼▼

{
  "_credStore": "desktop.exe"
}
```