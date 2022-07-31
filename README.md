# napspans.space-nginx
napspans.space配下のルーティングを行うdocker

# 初期設定
## git clone
```
git clone https://githubusername:password@github.com/napspans/napspans.space-nginx.git
```
`githubusername:password`部分は書き換える
githubusernameはメアドじゃない
passwordはリモートアクセス用に生成したものでも可
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

## network
コンテナ間通信のためネットワークを生成
```
docker network create napspans_network
```
ymlに記載されているネットワークをクリエイト

cecretbase側のdocker-compose.ymlも同様のネットワークに入るよう設定されている。

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

## commit message roles
書き方例``「add:△△を追加」``  
変更を加えて機能を母国語で表記
```
add:「～追加」 新しい機能追加
fix:「～修正」 バグの修正
refactor: 「～改善」仕様に影響がないコード改善(リファクタ)
perf:「～向上」 パフォーマンス向上関連
style: コメント等スタイルの修正編集
chore: ビルド、補助ツール、ライブラリ関連
docs: read.me、json、アカウントデータ等ドキュメント修正※
test:「～テスト」 テスト関連
```
※read.me、アカウントデータ等の仕様に影響がないドキュメントはdocumentのブランチにてコミット、マージ