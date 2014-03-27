PHP Gearman Handler
===================

[![Build Status](https://travis-ci.org/gabrielbull/php-gearman-handler.svg)](https://travis-ci.org/gabrielbull/php-gearman-handler)

Better doc will be coming.

## Config

File ``/path/to/config.php``

```php
return [
    'gearman_host' => '127.0.0.1',
    'gearman_port' => 4730,
    'worker_dir' => '/path/to/workers',
    'user' => 'apache'
];
```

## Create worker

```php
class WorkerExample implements \GearmanHandler\JobInterface
{
    public function getName()
    {
        return 'WorkerExample';
    }

    public function execute(\GearmanJob $job)
    {
        // To something
    }
}
```

## Start workers daemon

```shell
php vendor/bin/gearman start -c /path/to/config.php
```

## Worker usage

```php
$config = new GearmanHandler\Config([
    'gearman_host' => '127.0.0.1',
    'gearman_port' => 4730,
    'jobs_dir' => __DIR__ . '/Jobs'
]);
$worker = new GearmanHandler\Worker($config);
$worker->execute('JobName', ['data' => 'value']);
```