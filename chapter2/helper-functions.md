## 辅助函数

## 存放位置

Laravel 提供了很多 辅助函数，有时候我们也需要创建自己的辅助函数。

**必须** 把所有的『自定义辅助函数』存放于 `bootstrap` 文件夹中。

并在 `bootstrap/app.php` 文件的最顶部进行加载：

```
<?php

require __DIR__ . '/helpers.php';

...

```

