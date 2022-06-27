# HSApi

In Hifi Station Kft we decided to create a new automation system for our B2B partners.
You can connect your webshop, ecommerce, or any other system to our API.

We won't be able to write your backend code but we will help you to create the connection.

The api does not support OpenCart/Magento/PrestaShop/WooCommerce/Unas/Shoprenter/etc.
You need to write your own code to connect to your system.

## Requirements

* PHP 7.4
* Composer
* ext-openssl: * 
* ext-simlexml: *
* ext-json: *

## Features

* List products with informations
* Secure authentication (HTTP Basic Auth + API Key)
* JSON/XML REST output

## Installation
    "hsapi/hsapi": "^1.0.0"

or run

    composer require hscore/hsapi

Note that the vendor folder and the vendor/autoload.php script are generated by Composer; they are not part of the api.

Alternatively, if you're not using Composer, you can download HSApi as a zip file, then copy the contents of the HSApi folder into one of the include_path directories specified in your PHP configuration and load class file manually:
```php
use hscore\RequestGenerator;
require 'path/to/src/RequestGenerator.php'; /* or wherever the file is located */
```

## Authentication

In order to use the API you need to authenticate. You can do this by using the `authenticate` method.

```php
$request->authenticate('api_username', 'api_password', 'api_key');
```

## Output format

We provide two output formats: JSON and XML.
To change the output format, use the `setOutputFormat` method.
You can disable the output format by using the `setOutputFormat` method with an empty string.

```php
$request->setOutputFormat('json'); // or 'xml', default is 'json'
```
Use this method before the `send()` method.

## Usage
```php
$request = new RequestGenerator('products', 'json');
$request->authenticate('api_username', 'api_password', 'api_key');

$response = $request->send();

echo $response;
```

### Functions

`send()` return the response in the format you specified.

`authenticate(string $username, string $password, string $api_key)` authenticate the request.

`setOutputFormat(string $type)` set the output format.

`public $disablePrettyHeader = false;` disable the php `header()` function.

## Security
Please submit bug reports, or you found a mistake in the docs, or want to add something suggestions create a pull request or go ahead and create an issue at [Github issue tracker](https://github.com/csedo/hsapi/issues "Github issue tracker")