
# 常见问题

## chrome 浏览器 net::ERR_BLOCKED_BY_CLIENT

一次调试中，有三个js文件一直下载不下来，分别是：
```
GET http://localhost:9130/scripts/modules/mobile-app/mobile-app.ads.controller.js net::ERR_BLOCKED_BY_CLIENT
GET http://localhost:9130/scripts/modules/dialog/life-advertisement.dlg.controller.js net::ERR_BLOCKED_BY_CLIENT
GET http://localhost:9130/scripts/modules/dialog/community-advertisement.dlg.controller.js net::ERR_BLOCKED_BY_CLIENT
```

错误提示都是：`net::ERR_BLOCKED_BY_CLIENT`

原因：chrome 浏览器的广告拦截插件把这三个文件拦截了，因为文件名带`ads` `advertisement` 字样。

解决办法：把域名添加到白名单

