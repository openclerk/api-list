openclerk/api-list [![Build Status](https://travis-ci.org/openclerk/api-list.svg?branch=master)](https://travis-ci.org/openclerk/api-list)
==================

A library for listing and discovering runtime properties of APIs

## Installing

Include `openclerk/api-list` as a requirement in your project `composer.json`,
and run `composer update` to install it into your project:

```json
{
  "require": {
    "openclerk/api-list": "dev-master"
  }
}
```

## Using

If you are using something like [component-discovery](https://github.com/soundasleep/component-discovery),
you can define a new API for listing all runtime discovered APIs using the _ApiListApi_ abstract superclass:

```php
class MyApiListApi extends \Apis\ApiList\ApiListApi {

  function getAPIs() {
    return \DiscoveredComponents\Apis::getAllInstances();
  }

}
```

You can also get all runtime API information like so:

```php
$lister = new \Apis\ApiList\ApiLister();
$apis = $lister->processAPIs(\DiscoveredComponents\Apis::getAllInstances());

foreach ($apis as $api) {
  print_r(array(
    $api['endpoint'],
    $api['title'],
    $api['description'],
    $api['params'],   // array
    // ...
  ));
}
```

