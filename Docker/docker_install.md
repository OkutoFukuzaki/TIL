# bundle installをする際

```
$ docker compose up -d
$ docker compose exec web bash
# bin/dev
```
を実行し、コンテナに入った際には**bundle install**を使っても構わないが、
コンテナの外で**bundle install**を行いたい場合は
```
$ docker compose run web bundle install
```
を実行する必要がある。

もしコンテナに入ったであろうにも関わらず、エラーが起きてしまった場合
```
$ docker compose down
$ docker compose up -d
$ docker compose exec web bundle install
```
を実行し、webが走っているか確認し走っていなかった場合
```
$ docker compose down
$ docker compose run web bundle install
```
そ実行することで一度コンテナを落として外側から入れ直し、
```
$ docker compose up -d
$ docker compose exec web bash
#bin/dev
```
コンテナを開いた状態にして作業を進めることで解決した。
