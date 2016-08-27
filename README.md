# BaseUTF8

BaseXX encoder/decoder those support any valid UTF-8 sequences.

## Installation

```
composer require mpyw/base-utf8
```

## Features

Pass your character set as the first argument for the constructor.  
Default value is `ABCD...WXYZabcd...wxyz0123456789+/` (Base64).

- It must be either array or string.
- The number of elements must be a power of two. (2, 4, 8, 16, 32, 64, ...)
- Any paddings such as `=` are not appended.
- Control characters `\x00-\x20` are ignored.

## Example

```php
require __DIR__ . '/vendor/autoload.php';
use mpyw\BaseUTF8\Coder;

$coder = new Coder; // Base64
echo $coder->encode('foobar') . PHP_EOL; // Zm9vYmFy
echo $coder->decode('Zm9vYmFy') . PHP_EOL; // foobar
echo $coder->decode("Z  m  \n9v  Y\tmFy") . PHP_EOL; // foobar

$coder = new Coder('ABCDabcd'); // Base8
echo $coder->encode('foobar') . PHP_EOL; // DBacdbbdDAacAbcC
echo $coder->decode('DBacdbbdDAacAbcC') . PHP_EOL; // foobar

$coder = new Coder('ンアッーイキソ！'); // UTF-8 Base8
echo $coder->encode('田所浩二') . PHP_EOL;
echo $coder->decode('！ア！アッッソン！アキンイソンン！アキーッソキア！アアーキッアイ') . PHP_EOL;
```
