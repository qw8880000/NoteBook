

```
    app.module.js
        |
        |-- blocks/
        |   |
        |   |-- exception/
        |   |-- logger/
        |   \-- ..
        |
        |-- widgets/
        |
        |-- core/
        |
        \-- features/
            |
            |-- app.feature1
            |-- app.feature2
            |-- app.feature3
            \-- ...

```

angualr.js框架总体上分为三个部分：app功能模块，app通用模块，跨app通用模块。

* `app.module.js`: 存放app启动逻辑和模块依赖。
* `blocks/`：跨app的通用模块。如 blocks.exception, blocks.logger。
* `core/` `widgets`：此app的通用的模块。
* `features/`：app的功能模块。
