# Flask+GKE勉強のためのwebAPI
## このwebAPIでできること
ターミナルからcurlコマンドでjsonデータを送ると,
文字列が成型されて, 同じくjson形式でデータが返ってくる.

## webアプリを立ち上げる
``` docker
$ git clone
$ docker build --no-cache -t miniapp-flask:1.0.0 . 
$ docker run -p 5555:5555 -it -v $(pwd):/app/  --name miniapp-flask miniapp-flask:1.0.0
```

## 動作確認
```docker
$ curl http://localhost:5555/reply -X POST -H "Content-Type: application/json" -d '{"keyword": "sample"}'
<出力>
{
  "Answer": {
    "Text": "Yes, it is sample!\n"
  }, 
  "Content-Type": "application/json"
}

$ curl http://localhost:5555/
<出力>
Hello World!
```

## 削除するとき
``` docker
$ docker stop miniapp-flask
$ docker rm  miniapp-flask
$ docker rmi miniapp-flask:1.0.0
``` 

## ログ
同じフォルダにtest.logとして出力される