## Answer 1
There is no key for indexing from EXPLAIN.
So that is slow because the optimizer could not find any usable index to access rows if the table is large.


## Answer 2
```php
<?php
function searchInt($list, $find){
    in_array($find, $list, true);
}

$exIntArray = [
    1,
    2,
    3,
    4,
    12,
    45,
    34234,
    3452345,
    1234,
];

var_dump(serachInt(3, $exIntArray));
var_dump(serachInt(100, $exIntArray));
```

## Answer 3
```php
<?php
$pdo->setAttribute(PDO::MYSQL_ATTR_USE_BUFFERED_QUERY, false); // solution
$stmt = $pdo->prepare('SELECT * FROM largeTable');
$stmt->execute();
$results = $stmt->fetchAll(PDO::FETCH_ASSOC);
foreach ($results as $result) {
    // manipulate the data here
}
```
## Answer 4
1. Submited one zip folder (show_data(Drupal Answar4).zip).
2. Please Setup basic Drupal 8 site in your local and create Article content.
3. unzip folder and placed in module folder in Drupal 8.
4. Installed show_data module in Drupal . 
5. Open URL(<BasePath>/data-list).
6. Displayed list of all Article content in the page. 


## Answer 5

```php
<?php

interface iCaching {
    public function setCache($data);
    public function getCache();
}

/**
 * Class exMemCache
 */
class exMemCache implements iCaching {

    private $exCache;

    public function __construct() {
        // create instance for Memcached
        $this->exCache = new Memcached();
    }

    public function setCache($data) {
        // do something to store into exMemCache

    }

    public function getCache() {
        // do something to retrieve from exMemCache

    }
}

/**
 * Class exAPCCache
 */
class exAPCCache implements iCaching {
    public function __construct() {

    }

    public function setCache($data) {
        // do something to store into APCCache

    }

    public function getCache() {
        // do something to retrieve from APCCache

    }
}

/**
 * Class exNoneCache
 */
class exNoneCache implements iCaching {

    private $exCache;

    public function __construct() {

    }

    public function setCache($data) {
        return true;
    }

    public function getCache() {
        return true;
    }
}

/**
 * Class exCache
 */
class exCache {

    private $cache;

    public function __construct($env) {
        if ($env == 'PRODUCT') {
            $this->cache = new exMemCache();
        } else if ($env == 'STAGING') {
            $this->cache = new exAPCCache();
        } else {
            $this->cache = new exNoneCache();
        }

    }

    public function setCache($data) {
        $this->cache->setCache($data);
    }

    public function getCache() {
        return $this->cache->getCache();
    }
}

/**
 * Example
 */
$cache = new exCache('PRODUCT');
$cache->setCache($data);
$data = $cache->getCache();
```

## Answer 6
```php
<?php
require './fizzBuzz.php';
class FizzBuzzTest extends \PHPUnit_Framework_TestCase
{
    public function testFizzBuzz()
    {
        $this->assertEquals('Fizz', fizzBuzz(3, 3), 'Multiples of 3 should return Fizz');
        $this->assertEquals('Buzz', fizzBuzz(5, 5), 'Multiples of 5 should return Buzz');
        $this->assertEquals('FizzBuzz', fizzBuzz(15, 15), 'Multiples of 3 and 5 should return FizzBuzz');
        $this->assertEquals('2', fizzBuzz(2, 2), 'Non-multiples of 3 or 5 should return input');
    }
}
```

## Answer 7

This is not how you get the result from a query. You are setting it to a PDOStatement object. You need to fetch() the result in order to use it.
```php
<?php
$results = $stmt->fetchAll(PDO::FETCH_ASSOC);
```
## Answer 8

Yes, I worked on Drupal headless project.
1- I was used https://www.drupal.org/project/jsonapi module for creating API and pass to React guys and he display data in UI.
