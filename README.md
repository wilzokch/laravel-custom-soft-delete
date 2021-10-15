# Laravel Custom Soft Delete ( Laravel 5 Package )

 ![php 5.5+](https://img.shields.io/badge/php-5.5+-brightgreen.svg?style=flat&logo=php&labelColor=777BB4&logoColor=white&color=lightgrey) ![author](https://img.shields.io/badge/author-kch-brightgreen.svg?style=flat&logo=bitbucket&color=lightgrey)

## Installation

1. add

	    "repositories": [
	        {
	            "type": "vcs",
	            "url":  "git@bitbucket.org:wilzokch/laravel-custom-soft-delete.git"
	        }
	    ],

	to your composer.json.

2. run the `composer require` command from your terminal:

    	composer require wilzokch/laravel-custom-soft-delete:dev-master


3. add the Wilzokch\LaravelCustomSoftDelete\SoftDeletes trait to the model:

       <?php

       namespace App\Models;

       use Illuminate\Database\Eloquent\Model;
       use Wilzokch\LaravelCustomSoftDelete\SoftDeletes;

       class Flight extends Model
       {
           use SoftDeletes;
       }

4. add soft delete columns to your migration

        use Illuminate\Database\Schema\Blueprint;
        use Illuminate\Support\Facades\Schema;

        Schema::table('flights', function (Blueprint $table) {
            $table->tinyInteger('is_deleted')->default(false);
            $table->timestamp('deleted_at')->nullable();
        });

        Schema::table('flights', function (Blueprint $table) {
            $table->dropColumn('is_deleted');
            $table->dropColumn('deleted_at');
        });

