## 表单验证

### 表单请求验证类

**必须** 使用 [表单请求 - FormRequest 类](http://d.laravel-china.org/docs/5.5/validation#form-request-validation) 来处理控制器里的表单验证。

### 基类

所有 `FormRequest` 表验证类 **必须** 继承 `app/Http/Requests/Request.php` 基类。基类文件如下：

``` php
<?php

namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class Request extends FormRequest
{
    public function authorize()
    {
        // Using policy for Authorization
        return true;
    }
}
```

### 验证类命名

FormRequest 表验证类 **必须** 遵循 **资源路由** 方式进行命名，`photos` 对应 `app/Http/Requests/PhotoRequest.php` 。

### 类文件参考

FormRequest 表验证类文件请参考以下：

``` php
<?php

namespace App\Http\Requests;

class PhotoRequest extends Request
{
    public function rules()
    {
        switch($this->method())
        {
            // CREATE
            case 'POST':
            {
                return [
                    // CREATE ROLES
                ];
            }
            // UPDATE
            case 'PUT':
            case 'PATCH':
            {
                return [
                    // UPDATE ROLES
                ];
            }
            case 'GET':
            case 'DELETE':
            default:
            {
                return [];
            };
        }
    }

    public function messages()
    {
        return [
            // Validation messages
        ];
    }
}
```