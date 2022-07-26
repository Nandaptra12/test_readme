###### Nama      : Nanda Dian .S
###### Kelas     : XII RPL-2 
###### No. Absen : 13 

# Modul 1
## Soal  
1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing. 
2. Buatlah projek pertama laravel dengan nama projek “penjualan” dan tampilkan dalam browser. 

```
composer create-project laravel/laravel penjualan
```


# Modul 2 
## Soal  
1. Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam
modul ini.

Langkah pertama
```
php artisan make:migration create_produk_table
```
langkah kedua 
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('produk', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->integer('id_kategori');
            $table->integer('qty');
            $table->integer('harga_beli');
            $table->integer('harga_jual');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('produk');
    }
};
```
Langkah ketiga jalankan program 
```
php artisan migrate
```
Langkah selanjutnya membuat model kategori
```
php artisan make:model kategori
```
Kemudian buatlah seeder, jalankan kode dibawah pada terminal 
```
php artisan make:seeder kategoriTableSeeder 
```
Selanjutnya, isi **Public function run()** seperti dibawah
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'nama' => 'perlengkapan sekolah',
            ], 
            [
                'nama' => 'Komputer',
            ],
            [
                'nama' => 'Sabun',
            ],
            [
                'nama' => 'Accessories',
            ],
            [
                'nama' => 'ATK',
            ],
        ));
    }
}
```
Langkah selanjutnya, buka file **DatabaseSeeder** isi **Public function run()** seperti dibawah 
```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(kategoriTableSeeder::class);
    }
}
```
Lalu jalankan code pada terminal 
```
php artisan db:seed
```
