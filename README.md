# docker-compose.yml内の環境変数`${IP}`について
* docker-composeの.envでIPを指定する
  * 120.0.0.1〜127.255.255.254の範囲のローカルループバックアドレスが使用可能
```.env
IP=120.0.0.1
```

# ローカルループバックアドレスについて
* ただし、macOSではデフォルトで120.0.0.1以外のローカルループバックアドレスが使用できなくなっている
  * ifconfigに指定する必要がある

## 127.0.0.2を個別で指定
```sh
#!/bin/bash
sudo ifconfig lo0 alias 127.0.0.$i up
```

## # 127.0.0.2〜127.0.0.255を一括で指定
```sh
#!/bin/bash
for ((i=2;i<256;i++))
do
    sudo ifconfig lo0 alias 127.0.0.$i up
done
```
