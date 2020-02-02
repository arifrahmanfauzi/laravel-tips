---
description: membuat dummy data dengan cepat
---

# Laravel Faker

### Inisialisasi awal

>

> deklarasi dahulu _traits-_nya dan jika menggunakan eloquent insert maka panggil _Model_ nya juga

```php
use Faker\Factory as Faker;
use App\User;
```

### Konfigurasi Locale untuk Indonesia

Disini kita akan men-konfigurasi settingan untuk dummy berbahasa indonesia. Kita akan menambahkan beberapa code kedalam _function run\(\)._

```php
$faker = Faker::create('id_ID');
```

### Looping Banyaknya Data

```php
for ($i=0; $i < 10; $i++) { 
            $user = new User;
            $user->name = $faker->unique()->userName;
            $user->email = $faker->unique()->email;
            $user->password = bcrypt('kebersamaan@');
            $user->role_id = $faker->numberBetween(1,2);
            $user->phone_id = $faker->unique()->numberBetween(1,10);
            $user->save();
        }
```



