# laravel-9-new-features

### **Controller Route Groups**


Laravel 8.x
```php
Route::group(['prefix' => '/seeds-transactions'], function () {
    Route::post('/', [SeedsTransactionsController::class, 'store']);
    Route::put('/{seeds_transaction}', [SeedsTransactionsController::class, 'update']);
    Route::delete('/{seeds_transaction}', [SeedsTransactionsController::class, 'destroy']);
});
```
Laravel 9.x
```php
Route::controller(SeedsTransactionsController::class)->group(function() {
  Route::post('/seeds-transactions', 'store');
  Route::put('/seeds-transactions/{seeds_transaction}', 'update');
  Route::delete('/seeds-transactions/{seeds_transaction}', 'destroy');
}
```


### **Anonymous Migration Class**

Laravel 8.x
```php
class CreateUsersTable extends Migration {
[...]
}
```

Laravel 9.x
```php
return new class extends Migration {
[...]
}
```


### **Forced Scoped Bindings**

```php
User.php
public function licences() {
  return $this->hasMany(Licence::class);
}
```

Laravel 8.x
```php
Route::get('/users/{user}/licences/{licence:id}', 'show');
```

Laravel 9.x
```php
Route::get('/users/{user}/licences/{licence}', 'show')->scopeBindings();
```



### **Test Coverage**

Requires XDebug with XDebug coverage mode enabled

Laravel 8.x
```php
php artisan test
```

Laravel 9.x
```php
XDEBUG_MODE=coverage php artisan test --coverage --min=
```

