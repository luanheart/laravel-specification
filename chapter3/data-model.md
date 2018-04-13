## 数据模型

### 文件位置

数据模型文件 **必须** 放在：`app/Models`文件夹中

命名空间:

``` php
namespace App\Models;
```

### 基类

所有的数据模型都 **应该** 继承统一的基类`App/Models/Model`，此类文件为`/app/Models/Model.php`，内容参考如下

``` php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model as EloquentModel;

class Model extends EloquentModel
{
    public function scopeRecent($query)
    {
        return $query->orderBy('created_at', 'desc');
    }
}
```

### 命名规范

数据模型相关的命名规范：


