# Supported Languages

Wayscript supports and provides SDKs (see [sdk](../using-wayscript/sdk/ "mention")) in the following languages:

* Python 3.11
* Node v.6.15.0

Wayscript additionally supports the following languages:&#x20;

{% hint style="warning" %}
support for the following languages are still in beta. Please report any issues to  [support@wayscript.com](mailto:support@wayscript.com)
{% endhint %}

* Golang 1.18
* Rust 1.48
* Java 11
* PHP 7.4
* R 4.04

### Special considerations for PHP

Note that vendor directory will be installed at `/var/tmp/cache/php_vendor` . Include autoloaders with this code snippet:

```
require '/var/tmp/cache/php_vendor/autoload.php';
```
