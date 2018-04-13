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

- 数据模型类名 **必须** 为「单数」, 如：`App\Models\Photo`
- 类文件名 **必须** 为「单数」，如：`app/Models/Photo.php`
- 数据库表名字 **必须** 为「复数」，多个单词情况下使用「Snake Case」 如：`photos`, `my_photos`
- 数据库表迁移名字 **必须** 为「复数」，如：`2014_08_08_234417_create_photos_table.php`
- 数据填充文件名 **必须** 为「复数」，如：`PhotosTableSeeder.php`
- 数据库字段名 **必须** 为「Snake Case」，如：`view_count`, `is_vip`
- 数据库表主键 **必须** 为「id」
- 数据库表外键 **必须** 为「resource_id」，如：`user_id`, `post_id`
- 数据模型变量 **必须** 为「resource_id」，如：`$user_id`, `$post_id`

### 利用 Trait 来扩展数据模型

有时候数据模型里的代码会变得很臃肿，应该 利用 Trait 来精简逻辑代码量，提高可读性

存放于文件夹：`app/Models/Traits` 文件夹中。
