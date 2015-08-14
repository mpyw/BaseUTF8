# BaseUTF8

BaseXX encoder/decoder those support any valid UTF-8 sequences.

## Installation

```
composer require mpyw/base-utf8
```

## Example

```php
require 'vendor/autoload.php';
use mpyw\BaseUTF8\BaseUTF8;

$base = new BaseUTF8; // Default is base 64
echo $base->encode('foobar') . PHP_EOL; // Zm9vYmFy
echo $base->decode('Zm9vYmFy') . PHP_EOL; // foobar

$base = new BaseUTF8('ABCDabcd'); // Base8
echo $base->encode('foobar') . PHP_EOL; // DBacdbbdDAacAbcC
echo $base->decode('DBacdbbdDAacAbcC') . PHP_EOL; // foobar

$base = new BaseUTF8('ンアッーイキソ！'); // UTF-8 base8
echo $base->encode('田所浩二') . PHP_EOL;
echo $base->decode('！ア！アッッソン！アキンイソンン！アキーッソキア！アアーキッアイ') . PHP_EOL;
```
