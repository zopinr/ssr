# SSR2HeroKu

**稀缺资源，请勿滥用，日常使用中观看视频时请采用 144P 分辨率，否则一旦 Heroku 发飙大家都没得用，You know？**

**GFW 會隨機墻掉 \[your app name\].herokuapp.com 類型的網址，所以你可能得隨時以新名稱部署新應用並刪掉舊應用，或者綁定自己的域名到 heroku 才能再次用得起來。**

## 快速部署

在 https://heroku.com 网站上注册账号，登录，准备就绪后，点击这个 `Deploy to Heroku` 按钮链接。

[![](https://user-images.githubusercontent.com/30760636/96996783-0da82100-1563-11eb-9af1-3ecd0a83420b.png)](https://heroku.com/deploy?template=https://github.com/ShadowsocksR-Live/ssr2heroku/tree/main)

在随后出现的页面上按提示输入 `应用名称`,以及 `${APP_SITE}`, `${PASSWORD}`, `${SECRET_PATH}` 这三个变量的值，再点击下部的 `Deploy app` 按钮就将 SSRoT 服务端最新版本部署在 heroku 的 docker 容器上了。

部署应用的页面像下面这个样子。

![image](https://user-images.githubusercontent.com/30760636/96831486-bffebc00-146f-11eb-852e-9705b5866eb1.png)

## 客户端下载地址

https://github.com/ShadowsocksR-Live/shadowsocksr-native/wiki/%E5%AE%A2%E6%88%B7%E7%AB%AF%E7%94%A8%E6%B3%95

## 客户端配置文件 config.json

部署完毕，将以下文件中的 `${PASSWORD}` 和两个 `${APP_SITE}` 和 `${SECRET_PATH}` 替换成你的值就可以用于客户端了。

```json
{
    "password": "${PASSWORD}",
    "method": "aes-128-ctr",
    "protocol": "origin",
    "protocol_param": "",
    "obfs": "plain",
    "obfs_param": "",

    "udp": true,
    "idle_timeout": 300,
    "connect_timeout": 6,
    "udp_timeout": 6,

    "client_settings": {
        "server": "${APP_SITE}",
        "server_port": 443,
        "listen_address": "0.0.0.0",
        "listen_port": 1080
    },

    "over_tls_settings": {
        "enable": true,
        "server_domain": "${APP_SITE}",
        "path": "/${SECRET_PATH}/",
        "root_cert_file": ""
    }
}
```

另外，在具体应用页面，点击 `More` -> `Run console` 可以打开一个简易控制台窗口，通过该窗口输入命令
```bash
echo password=${PASSWORD}, path=${SECRET_PATH}, site=${APP_SITE}
```
找回关键参数时，会发现它們就是你的预设值。
