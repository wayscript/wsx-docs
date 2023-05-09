# Supported Languages

WayScript supports and provides SDKs (see [sdk](../using-wayscript/sdk/ "mention")) in the following languages:

* Python 3.11
* Node v.16.20.0

WayScript additionally supports the following languages:&#x20;

{% hint style="warning" %}
support for the following languages are still in beta. Please report any issues to  [support@wayscript.com](mailto:support@wayscript.com)
{% endhint %}

* Golang 1.20
* Rust 1.48
* Java 11
* PHP 7.4
* R 4.0.3
* C# (.NET 7.0)
* F# (.NET 7.0)
* Visual Basic (.NET 7.0)

### Special considerations for PHP

Note that vendor directory will be installed at `/var/tmp/cache/php_vendor` . Include autoloaders with this code snippet:

```
require '/var/tmp/cache/php_vendor/autoload.php';
```
