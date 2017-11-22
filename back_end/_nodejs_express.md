
# express 的目录结构

node.js express的软件结构一般有两种：
```
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.jade
    ├── index.jade
    └── layout.jade
```
另一种：
```
|
|-- src
|   |
|   |-- client
|   |   |
|   |   |-- images
|   |   |-- javascripts
|   |   |-- stylesheets
|   |   \-- views
|   |       |-- error.html
|   |       |-- index.html
|   |       \-- layout.html
|   |
|   \-- server
|       |
|       |-- app.js
|       \-- routes
|           |-- index.js   
|           \-- users.js 
|   
\-- package.json
```

这两种结构的区别：
* 第一种结构**重后端，轻前端**，后端使用模板引擎(如：jade)
* 第二种结构**轻后端，重前端**，不需要模板引擎，使用前端框架(如：angular,vue)

