
<p align="center">
    <img style="width: 250px" src="./imgs/logo.png"/>
</p>

# Socket Conveyor

<p align="left">
    <a target="_blank" href="https://github.com/kanata-php/socket-conveyor/actions/workflows/php.yml"><img src="https://github.com/kanata-php/socket-conveyor/actions/workflows/php.yml/badge.svg"/></a>
    <a target="_blank" href="https://scrutinizer-ci.com/code-intelligence"><img src="https://scrutinizer-ci.com/g/kanata-php/socket-conveyor/badges/code-intelligence.svg?b=master"/></a>
    <a target="_blank" href="https://scrutinizer-ci.com/g/kanata-php/socket-conveyor/?branch=master"><img src="https://scrutinizer-ci.com/g/kanata-php/socket-conveyor/badges/quality-score.png?b=master"/></a>
</p>

> A WebSocket/Socket message Router for PHP

## Prerequisites

- PHP >= 8.0
- OpenSwoole PHP Extension

## Installation

```shell
composer require kanata-php/socket-conveyor
```

## Description

This package enables you to work with socket messages using routing strategy. It comes with some solutions such as channel or action listeners, but you can implement your own by extending the `AbstractAction`.

This package is built with [OpenSwoole](https://openswoole.com/) in mind, but it works with any websocket implementation. Please open a Github Issue if you find any! You can find out more how to use WebSockets with OpenSwoole [here](https://www.youtube.com/watch?v=Vgw5Ibqc15k).

> This package has 2 clients:
>   - **JS Client** : npm package from frontend integration: https://www.npmjs.com/package/socket-conveyor-client.
>   - **PHP Client**: composer package for backend integration:  https://packagist.org/packages/kanata-php/conveyor-server-client


## Topics:


- [How it works](/howitworks.md)
- [Quick Start](/quickstart.md)
- [Persistence](/persistence.md)
- [Usage](/usage.md)
- [Actions](/actions.md)


## Tests

Run Command:

```shell
./vendor/bin/phpunit
```

## Author

👤 **Savio Resende**

* Website: https://savioresende.com
* GitHub: [@lotharthesavior](https://github.com/lotharthesavior)

## 📝 License

Copyright © 2022 [Savio Resende](https://github.com/lotharthesavior).

This project is [MIT](https://github.com/kefranabg/readme-md-generator/blob/master/LICENSE) licensed.
