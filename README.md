# Instagram PHP Scrapper

This is the fork of [`postaddictme/instagram-php-scraper`](https://github.com/postaddictme/instagram-php-scraper) repo.
Description from original:

> This library based on Instagram web version. We develop it because nowadays it is hard to get approved Instagram application. 
> The purpose support every feature that web desktop and mobile version support. 

## Code Example
```php
$instagram = Instagram::withCredentials('username', 'password');
$instagram->login();
$account = $instagram->getAccountById(3);
echo $account->getUsername();
```

Some methods do not require authentication: 
```php
$instagram = new Instagram();
$nonPrivateAccountMedias = $instagram->getMedias('kevin');
echo $nonPrivateAccountMedias[0]->getLink();
```

If you use authentication it is recommended to cache the user session. In this case you don't need to run the `$instagram->login()` method every time your program runs:

```php
$instagram = Instagram::withCredentials('username', 'password', '/path/to/cache/folder/');
$instagram->login(); // will use cached session if you can force login $instagram->login(true)
$account = $instagram->getAccountById(3);
echo $account->getUsername();
```

Using proxy for requests:

```php
$instagram = new Instagram();
Instagram::setProxy([
    'address' => '0.0.0.0',
    'port'    => '8080',
    'tunnel'  => true,
    'timeout' => 30,
]);
// Request with proxy
$account = $instagram->getAccount('kevin');
Instagram::disableProxy();
// Request without proxy
$account = $instagram->getAccount('kevin');
```

## Installation

### Using composer

```sh
composer.phar require nassajis/instagram-php-scraper
```
or 
```sh
composer require nassajis/instagram-php-scraper
```

### If you don't have composer
You can download it [here](https://getcomposer.org/download/).

## Examples
See examples [here](https://github.com/nassajis/instagram-php-scraper/tree/master/examples).
