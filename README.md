# BaseUTF8

BaseXX encoder/decoder those support any valid UTF-8 sequences.

## Installation

```
composer require mpyw/base-utf8
```

## Example

```php
require 'vendor/autoload.php';
use mpyw\BaseUTF8\Coder;

$coder = new Coder; // Default is base64
echo $coder->encode('foobar') . PHP_EOL; // Zm9vYmFy
echo $coder->decode('Zm9vYmFy') . PHP_EOL; // foobar

$coder = new Coder('ABCDabcd'); // Base8
echo $coder->encode('foobar') . PHP_EOL; // DBacdbbdDAacAbcC
echo $coder->decode('DBacdbbdDAacAbcC') . PHP_EOL; // foobar

$coder = new Coder('ンアッーイキソ！'); // UTF-8 base8
echo $coder->encode('田所浩二') . PHP_EOL;
echo $coder->decode('！ア！アッッソン！アキンイソンン！アキーッソキア！アアーキッアイ') . PHP_EOL;
```
