# Securing PHP Rest API with Magic!

This is a simple [PHP REST API](https://github.com/shahbaz17/php-rest-api) protected with [Magic](https://magic.link).

We will be using [Magic Admin PHP SDK](https://github.com/magiclabs/magic-admin-php).

The Magic Admin PHP SDK provides convenient ways for developers to interact with Magic API endpoints and an array of utilities to handle [DID Token](https://docs.magic.link/tutorials/decentralized-id).

## Documentation
See the [Magic doc](https://docs.magic.link/admin-sdk/php)!

## Installation

### Prerequisites

 * PHP 5.6.0 and later.
 * MySQL

### Composer

You can install the bindings via [Composer](http://getcomposer.org/). Run the following command:

```bash
composer require magiclabs/magic-admin-php

```

To use the bindings, use Composer's [autoload](https://getcomposer.org/doc/01-basic-usage.md#autoloading):

```php
require_once('vendor/autoload.php');
```

### Manual Installation

If you do not wish to use Composer, you can download the [latest release](https://github.com/magiclabs/magic-admin-php). Then, to use the bindings, include the `init.php` file.

```php
require_once('/path/to/magic-admin-php/init.php');
```

### Dependencies

The bindings require the following extensions in order to work properly:

-   [`curl`](https://secure.php.net/manual/en/book.curl.php)
-   [`gmp`](https://www.php.net/manual/en/book.gmp.php)

If you use Composer, these dependencies should be handled automatically. If you install manually, you'll want to make sure that these extensions are available.


### DATABASE
Import the php-rest-api.sql file, copy `.env.example` into `.env` and update the configuration as per your configuration.

Get **`MAGIC_SECRET_KEY`** by signing up for [Magic's Free Developer Account](https://www.magic.link).

## Development

Get [Composer](http://getcomposer.org/). For example, on Mac OS:

```bash
brew install composer
```

Install dependencies:

```bash
composer install
```

Run Server:
```bash
php -S localhost:8000 -t api
```

## API
| API               | CRUD          | Description  |
| :-------------     |:-------------:| ------------:|
| GET /post         | **READ**      | Get the Posts from `posts` table |
| GET /post/{id}     | **READ**      | Get a single Post from `posts` table |
| POST /post        | **CREATE**    | Create a Post and insert into `posts` table |
| PUT  /post/{id}   | **UPDATE**    | Update the Post in `posts` table |
| DELETE /post/{id} | **DELETE**    | Delete a Post from `posts` table |

### Test
Test the API endpoints using [Postman](https://www.postman.com/) or though the [Frontend Application](./public/index.html).
Remember to change line no. **365** of `public/index.html` file as per your localhost connection.
```
.get("http://localhost:8000/post/")
```

## License
See [License.](./LICENSE)
