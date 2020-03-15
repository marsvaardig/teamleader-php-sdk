# Teamleader API v2 PHP SDK

This is a PHP wrapper for the Teamleader API v2. Documentation of the API can be found here: [https://developer.teamleader.eu/]().
Please note that the Teamleader API v2 is not complete and some Entities and Actions are missing.

Currently we only support a few entities and per entity only a few actions:

1.  Company (create and update, getById)
2.  Contact (create, update, linkToCompany, getById)
3.  Deal (create, update, move, get, getById)
4.  Deal phases (get)
5.  Deal sources (get)
6.  Activity types (get)
7.  Event (create, update, delete, get, getById)
8.  Business types (get)
9.  Tags (get)
10. Invoice (get, book, registerPayment)
11. Credit notes (get)
12. Payment terms (get)
13. Tax rates (get)
14. Withholding tax rates (get)
15. Departments (get)
16. User (me, get, getById)
17. Webhook (get, register)
18. Projects (get, getById)
19. Tasks (get, getById)
20. Milestones (get, getById)
21. TimeTracking (get, getById)
22. Worktypes (get)
23. Productcategories (get)
24. Products (create, get, getById)
25. Custom fields (get)

Teamleader API v2 works with OAuth2. This means your application needs to be registered on the [Teamleader Marketplace](https://marketplace.teamleader.eu/nl/nl/ontwikkel/integraties) (you can keep them private though).

Please contact me at jan@jannesmannes.nl if you have any feedback or questions.

# Examples

See all examples in the examples directory.

## Request an access token

You need to do this once, after you get an access token you can use the refresh token to obtain a new access token after it expires.

```
<?php
require __DIR__ . '/../vendor/autoload.php';

require __DIR__ . '/credentials.php';

$redirectUrl = 'https://teamleader-php-sdk.dev/examples/acquire-access-token.php';

$connection = new \Teamleader\Connection();
$connection->setClientId( $clientId );
$connection->setClientSecret( $clientSecret );
$connection->setRedirectUrl( $redirectUrl );

$connection->acquireAccessToken();
```

## Create a company

```
$company = $client->company( [
    'name' => 'Test API v2',
] )->save();
```

## Get deal phases

```
$dealPhases = $client->dealPhase()->get();
```

# TODO

- [ ] Support custom actions on Deals
- [ ] Add all other Entities

# Change log

## 2.2.0 (2020-03-04)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/2.1.0...d38974d8a6eb42442e08ba55296903693be72971)

Credits for this release go to [@kjellknapen](https://github.com/kjellknapen) and [@PazkaL](https://github.com/PazkaL)

**Features:**

- Book invoices and register payments
- Get product categories
- Get products

## 2.1.0 (2020-03-03)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/2.0.0...dad6de27b32d24d5ec81cd3cf0fc74b029db21f2)

Credits for this release go to @cschalenborgh

**Features:**

- Get deals improvements
- Get projects
- Get tasks
- Get milestones
- Get time tracking
- Get work types

## 2.0.0 (2019-09-24)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/1.1.1...0c7c5f4080adbd1640542ca79f68a01191c61e20)

Many thanks to @Senjutsuu and @carakas from @sumocoders for most of the below changes!

**Features:**

- Move deals
- List and register webhooks
- Added repo license
- Added old id to new id migration endpoint
- Moved to PHP 7.1
- Activity type entity added
- Event entity added
- Added a remove endpoint to all storable entities
- Added businesstype entity
- Added tag entity
- Added invoice entity
- Added credit note entity
- Added tax rate entity
- Added payment term entity
- Added withholding tax rate entity
- Added department entity
- Added unit tests
- A lot of code refactoring
- Added filter, paging en sorting attributes to entities
- Added JSON serialisation
- Added fetchAll method to entities
- Added user entity

**Fixes:**

- Updated outdated attributes for the company entity
- Fix getting data from the cache when there is no cached data
- Storable::update fixed

## 1.2.0 (2018-08-23)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/1.1.1...1.2.0)

**Features:**

- Added Contact->linkToCompany Action

## 1.1.1 (2018-08-23)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/1.1.0...1.1.1)

**Features:**

- Added readme

**Fixes:**

- Switched back to GuzzleHttp 6


## 1.1.0 (2018-08-22)
[Full change log](https://github.com/janhenkes/teamleader-php-sdk/compare/1.0.2...1.1.0)

**Features:**

- Added more examples
- Implemented FindAll action
- Added DealPhase entity
- Added DealSource entity
