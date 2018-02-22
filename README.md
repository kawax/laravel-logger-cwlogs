# CloudWatchLogs channel for Laravel Log

Demo project  
https://github.com/kawax/laravel-logger-project

## Requirements
- Laravel >= 5.6
- PHP >= 7.1.3

## Installation

### Composer
```
composer require revolution/laravel-logger-cwlogs
```

### config/logging.php

```php
    'channels' => [
        'stack' => [
            'driver'   => 'stack',
            'channels' => ['single', 'cwlogs'],
        ],
        
        'cwlogs' => [
            'driver'    => 'custom',
            'via'       => Revolution\Laravel\Logger\CloudWatchLogs\CloudWatchLogger::class,
            'region'    => env('CWLOGS_REGION'),
            'key'       => env('CWLOGS_KEY'),
            'secret'    => env('CWLOGS_SECRET'),
            'group'     => env('CWLOGS_GROUP'),
            'stream'    => env('CWLOGS_STREAM'),
            'retention' => env('CWLOGS_RETENTION', 14),
            'level'     => 'debug',
        ],
    ]
```

### .env
```
CWLOGS_REGION=us-east-1
CWLOGS_KEY=your AWS key
CWLOGS_SECRET=your AWS secret
CWLOGS_GROUP=
CWLOGS_STREAM=
CWLOGS_RETENTION=14
```

## LICENSE
MIT
