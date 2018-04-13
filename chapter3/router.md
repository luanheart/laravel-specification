## 路由

### 路由闭包

**绝不** 在路由配置文件里书写『闭包路由』或者其他业务逻辑代码，因为一旦使用将无法使用 [路由缓存](http://d.laravel-china.org/docs/5.5/controllers#route-caching) 。

### 使用 Restful 路由

[Restful 介绍](http://www.ruanyifeng.com/blog/2014/05/restful_api)

**必须** 优先使用 Restful 路由，配合资源控制器使用，见 [文档](http://d.laravel-china.org/docs/5.5/controllers#RESTful-%E8%B5%84%E6%BA%90%E6%8E%A7%E5%88%B6%E5%99%A8)。

![](/assets/09GHC72ygP.png)
超出 Restful 路由的，**应该** 模仿上图的方式来定义路由。

### resource 方法正确使用

一般资源路由定义：
``` php
Route::resource('photos', 'PhotosController');
```

等于以下路由定义：
``` php
Route::get('/photos', 'PhotosController@index')->name('photos.index');
Route::get('/photos/create', 'PhotosController@create')->name('photos.create');
Route::post('/photos', 'PhotosController@store')->name('photos.store');
Route::get('/photos/{photo}', 'PhotosController@show')->name('photos.show');
Route::get('/photos/{photo}/edit', 'PhotosController@edit')->name('photos.edit');
Route::put('/photos/{photo}', 'PhotosController@update')->name('photos.update');
Route::delete('/photos/{photo}', 'PhotosController@destroy')->name('photos.destroy');
```

使用 `resource` 方法时，如果仅使用到部分路由，**必须** 使用 `only` 列出所有可用路由：
``` php
Route::resource('photos', 'PhotosController', ['only' => ['index', 'show']]);
```

**绝不** 使用 `except`，因为 `only` 相当于白名单，相对于 `except` 更加直观。路由使用白名单有利于养成『安全习惯』。

### 单数 or 复数？

资源路由路由 URI 必须 使用复数形式，如：

- `/photos/create`
/photos/{photo}
错误的例子如：

/photo/create
/photo/{photo}

