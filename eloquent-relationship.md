# Eloquent Relationship

Eloquent Relationship merupakan salah satu fitur yang cukup menarik dan mempermudah developer dalam membuat sebuah relasi seperti dalam sebuah database tetapi dilakukan di dalam sebuah _Model._ Langsung saja lihat gambar dibawah ini.

![](.gitbook/assets/image%20%281%29.png)

### Buat 2 buah Model User & Post

1. User

```php
<?php

namespace App\Model;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    protected $table = 'users';
    protected $primaryKey = 'id';

    public function post(){
        return $this->hasMany(Post::class,'user_id');
    }
}
```

Perhatikan code diatas

1. Post

