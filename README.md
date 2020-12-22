# Secure your PHP Rest API with Magic!

This is a simple [PHP REST API](https://github.com/shahbaz17/php-rest-api) protected with [Magic](https://magic.link).

We will be using [Magic Admin PHP SDK](https://github.com/magiclabs/magic-admin-php) in this sample code to protect the PHP REST API.

The Magic Admin PHP SDK provides convenient ways for developers to interact with Magic API endpoints and an array of utilities to handle [DID Token](https://docs.magic.link/tutorials/decentralized-id).

Please read [dev.to](https://dev.to/shahbaz17/rest-api-with-magic-4d6c-temp-slug-4815677?preview=ea32cb7504bcb003c77c93ea8858e18228297015e50501c204b82a16c7c5e739d92a2eaaa67f68b9de7ef1796c64e712886c1a5d0432df19cfb112e6) to learn more about securing the PHP REST API with Magic.

### Prerequisites

- [PHP 5.6 and above](https://www.php.net/downloads.php)
- [MySQL](https://www.mysql.com/downloads/)
- [Composer](http://getcomposer.org/)
- [Postman](https://www.postman.com/downloads/)

## Getting Started

Clone this project with the following commands:

```bash
git clone https://github.com/shahbaz17/magic-php-rest-api.git
cd magic-php-rest-api
```

### Configure the application

Create the database and user for the project.

```php
mysql -u root -p
CREATE DATABASE blog CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'rest_api_user'@'localhost' identified by 'rest_api_password';
GRANT ALL on blog.* to 'rest_api_user'@'localhost';
quit
```

Create the `post` table.

```php
mysql -u rest_api_user -p;
// Enter your password
use blog;

CREATE TABLE `post` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `body` text NOT NULL,
  `author` varchar(255),
  `author_picture` varchar(255),
  `created_at` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
);
```

Copy `.env.example` to `.env` file and enter your database deatils.

```bash
cp .env.example .env
```

`.env`

```php
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=rest_api_user
DB_PASSWORD=rest_api_password
```

### Get your Magic Secret Key

Sign Up with [Magic](https://dashboard.magic.link/signup) and get your **`MAGIC_SECRET_KEY`**.

Feel free to use the Test Application automatically configured for you, or create a new one from your [Dashboard](https://dashboard.magic.link/app/all_apps).

![Dashboard Image goes here](https://dev-to-uploads.s3.amazonaws.com/i/fnjqvscslu11ih87p94t.png)

`.env` complete

```php
MAGIC_SECRET_KEY=sk_test_01234567890 // Paste SECRET KEY
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=rest_api_user
DB_PASSWORD=rest_api_password
```

## Development

Install the project dependencies and start the PHP server:

```bash
composer install
```

```bash
php -S localhost:8008 -t api
```

## Your APIs

| API               |                                Description |
| :---------------- | -----------------------------------------: |
| GET /posts        |            Get the Posts from `post` table |
| GET /post/{id}    |        Get a single Post from `post` table |
| POST /post        | Create a Post and insert into `post` table |
| PUT /post/{id}    |            Update the Post in `post` table |
| DELETE /post/{id} |            Delete a Post from `post` table |

Test the API endpoints using [Postman](https://www.postman.com/) or though the [Frontend Application](./public/index.html).

### Start your Frontend Application:

```bash
php -S localhost:8002 -t public
```

## License

See [License.](./LICENSE)
