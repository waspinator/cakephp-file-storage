Installation
============

Make sure you've checked the [requirements](Requirements.md) first!

Using Composer
--------------

Installing the plugin via [Composer](https://getcomposer.org/) is very simple, just run in your project folder:

```
composer require burzum/file-storage:"^2"
```

Database Setup
--------------

You need to setup the plugin database using [the official migrations plugin for CakePHP](https://book.cakephp.org/migrations/2.x/en/).

```
bin/cake migrations migrate --plugin Burzum/FileStorage
```

If you're coming from the CakePHP 2.0 version of the plugin, the support for the CakeDC Migrations plugin has been dropped in favor of [the official migrations plugin](https://github.com/cakephp/migrations).

CakePHP Bootstrap
-----------------

Add the following part to your applications ```config/bootstrap.php```.

```php
use Cake\Event\EventManager;
use Burzum\FileStorage\Storage\StorageManager;
use Burzum\FileStorage\Storage\Listener\ImageProcessingListener;

// For automated image processing you'll have to attach this listener as well
$listener = new ImageProcessingListener();
EventManager::instance()->on($listener);
```

Adapter Specific Configuration
------------------------------

Depending on the storage backend of your choice, for example Amazon S3 or Dropbox, you'll very likely need additional vendor libs and extended adapter configuration.

Please see the [Specific Adapter Configuration](Specific-Adapter-Configurations.md) page of the documentation for more information about then. It is also worth checking the Gaufrette documentation for additonal adapters.

Running Tests
-------------

The plugin tests are set up in a way that you can run them without putting the plugin into a CakePHP3 application. All you need to do is to go into the FileStorage folder and run these commands:

```
cd <file-storage-plugin-folder>
composer update
phpunit
```
