---
description: membuat dummy data dengan cepat
---

# Laravel Faker

### Inisialisasi awal

> deklarasi dahulu _traits-_nya

```php
use Faker\Factory as Faker;
```

### Konfigurasi Locale untuk Indonesia

Disini kita akan men-konfigurasi settingan untuk dummy berbahasa indonesia. Kita akan menambahkan beberapa code kedalam _function run\(\)._

```php
$faker = Faker::create('id_ID');
```





