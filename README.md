
:warning: Deprecated. Use https://github.com/careerbuilder/php-oauth instead.

---

php-oauth
=========

This is a PHP Guzzle3 plugin for dealing with CB OAuth2.

## Example Usage

```php
use CareerBuilder\OAuth2\OAuth2Plugin;
use CareerBuilder\OAuth2\TokenFactory;
use CareerBuilder\OAuth2\NullTokenStorage;
use CareerBuilder\OAuth2\Flows\ClientCredentials;

// create Guzzle client as you normally do

$client = new Client('https://api.careerbuilder.com');

// register the OAuth2Plugin

$configs = array(
    'client_id' => 'yourclientid',
    'client_secret' => 'shhh',
    'shared_secret' => 'supersecret',
    'base_url' => 'https://www.careerbuilder.com'
);

$client->addSubscriber(new OAuth2Plugin(new ClientCredentials($configs), new NullTokenStorage()));

// do whatever you normally do with Guzzle

$request = $client->get('/corporate/geography/validate');
$request->getQuery()->set('query', 'Atlanta');
$response = $request->send();
```

See more in [usage.php](usage.php).
