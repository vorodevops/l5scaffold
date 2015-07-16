# Laravel 5 Scaffold Generator


Hi, this is a scaffold generator for Laravel 5.



## Usage

### Step 1: Install Through Composer


Setup your composer.json


```
  "require": {
    "php": ">=5.5.9",
    "laravel/framework": "5.1.*",
    "laralib/l5scaffold": "dev-master"
  },
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/alnutile/l5scaffold.git"
    }
  ],
```

then

~~~
composer update
~~~

### Step 2: Add the Service Provider

Since we only want this on dev go to `app/Providers/AppServiceProvider.php`

```
    public function register()
    {
        $this->app->singleton('App\Services\ResponseInterface', function ($app) {
            return new \App\Services\ResponseService;
        });

        if ($this->app->environment() == 'local') {
            $this->app->register('Laralib\L5scaffold\GeneratorsServiceProvider');
        }
    }
}
```

### Step 3: Run Artisan!

You're all set. Run `php artisan` from the console, and you'll see the new commands `make:scaffold`.

## Examples


```
php artisan make:scaffold Tweet --schema="title:string:default('Tweet #1'), body:text"
```
This command will generate:

```
app/Tweet.php
app/Http/Controllers/TweetController.php
database/migrations/2015_04_23_234422_create_tweets_table.php
database/seeds/TweetTableSeeder.php
resources/views/layout.blade.php
resources/views/tweets/index.blade.php
resources/views/tweets/show.blade.php
resources/views/tweets/edit.blade.php
resources/views/tweets/create.blade.php
```
And don't forget to run:

```
php artisan migrate
```


## Scaffold
![image](http://i62.tinypic.com/11maveb.png)
![image](http://i58.tinypic.com/eqchat.png)
![image](http://i62.tinypic.com/20h7k8n.png)
