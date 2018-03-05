---
title: angularjs unit test
date: 2018-03-05 15:19:52
categories:
  - 前端
  - angular.js
tags:
  - angular.js
abbrlink: @@abbrlink
---

# 参考

* [AngularJS Testing Tips: Testing Directives](https://www.sitepoint.com/angular-testing-tips-testing-directives/)
* [Angular Test Patterns](https://github.com/daniellmb/angular-test-patterns)
* [how alert directive is tested in angular-ui/bootstrap.](https://github.com/angular-ui/bootstrap/blob/master/src/alert/test/alert.spec.js)

# 获取某个element的controller

获取某个element的controller:
```
element.controller('controllerName')
```

获取directive或者component里面的controller:
```
element.controller('directiveName');
```

参考：[angular.element](https://docs.angularjs.org/api/ng/function/angular.element)
