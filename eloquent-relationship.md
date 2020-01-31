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

Perhatikan code diatas, dimana kita memiliki class `User` kemudian terdapat _function_ `post()` , dan sebuah relasi yaitu `hasMany().` di dalam relasi `hasMany()` diisi dengan 2 parameter, yang pertama yaitu sebuah _model class_ yang _direlasikan_, dan parameter kedua yaitu sebuah _foreign\_key._ Jadi cara memahaminya yaitu, `class User` `hasMany` `Post::class` yang perarti `User` `memiliki` `banyak` post.

1. Post

```php
<?php

namespace App\Model;

use Illuminate\Database\Eloquent\Model;

class Post extends Model
{
    protected $primaryKey = 'id';
    protected $table = 'post';
}

```

### Memanggil relasi

Buat sebuah _controller&function_ terserah

```php
public function userposts(){
        $user = User::find(1);
        $post = $user->post;

        return response()->json(['user' => $user]);
    }
```

Pada code diatas pada variabel `$user` kita akan mencari user dengan `id`= 1, nah untuk `$post` terlihat setelah `$user` terdapat variabel `post`, loh... tapi kenapa tidak ada tanda kurung  `()` itu karena `function post()`pada `User` model akan dikenali sebagai sebuah `properties` bukan sebagai _function_ lagi. Setelah itu maka akan me_return_ hasil serperti ini.

```javascript
{
  "user": {
    "id": 1,
    "name": "cakrabuana.hakim",
    "email": "paris23@waluyo.desa.id",
    "phone_id": 2,
    "email_verified_at": null,
    "password": "$2y$10$V6nu9lPTSuWFO6cxu4MwFeg7p7Lnk59TxFoGFhhD7U4shPwMmzGNS",
    "remember_token": null,
    "created_at": "2020-01-30 02:05:29",
    "updated_at": "2020-01-30 02:05:29",
    "role_id": 2,
    "post": [
      {
        "id": 1,
        "post_content": "Officiis et et fugiat esse. Libero et numquam id reprehenderit id veniam fugit. Inventore at et cumque dolor voluptas nobis necessitatibus.",
        "user_id": 1,
        "created_at": "2020-01-30 02:24:55",
        "updated_at": "2020-01-30 02:24:55",
        "post_title": "Et provident et quisquam."
      },
      {
        "id": 2,
        "post_content": "Quasi qui at esse qui nemo. At maxime quo iusto corrupti vel. Iusto est autem id quis veritatis.",
        "user_id": 1,
        "created_at": "2020-01-30 02:24:55",
        "updated_at": "2020-01-30 02:24:55",
        "post_title": "Doloremque officiis provident laborum."
      }
    ]
  }
}
```

#### Lalu bagaimana cara mengaksesnya?

lihat dibawah ini...

```php
$user->post[0]->post_content
```

karena post berisi array, maka kita perlakukan seperti array biasanya dengan engakses index nya yaitu `[0]` nah di dalam array index ke-0 kan berubah object, jadi kita perlakukan sebagaimana object biasanya yaitu `post[0]->post_content` sekian...

