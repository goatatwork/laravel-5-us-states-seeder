#Laravel 5 State Seeder

**Usage**

To create the model and migration for a `states` table in your database:

```bash
$ php artisan make:model -m State
```

In your migration you need to include `string` fields for `code` and `name`. Your migration should look like this:

```
<?php

use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;

class CreateStatesTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('states', function (Blueprint $table) {
            $table->increments('id');
            $table->string('name');
            $table->string('code');
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
        Schema::dropIfExists('states');
    }
}

```

Then simply drop the `StatesSeeder.php` into your `seeds` folder.  Back at the command line run:

```
$ php artisan migrate
$ php artisan db:seed --class StateSeeder
```

You'll now have a functional States database suitable for populating drop downs or whatever else you crazy kids do with your states tables.
