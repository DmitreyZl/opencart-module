[![Build Status](https://github.com/retailcrm/opencart-module/workflows/ci/badge.svg)](https://github.com/retailcrm/opencart-module/actions)
[![Coverage](https://img.shields.io/codecov/c/gh/retailcrm/opencart-module/master.svg?logo=codecov&logoColor=white)](https://codecov.io/gh/retailcrm/opencart-module)
[![GitHub release](https://img.shields.io/github/release/retailcrm/opencart-module.svg?logo=github&logoColor=white)](https://github.com/retailcrm/opencart-module/releases)
[![PHP version](https://img.shields.io/badge/PHP->=5.4-blue.svg?logo=php&logoColor=white)](https://php.net/)

Opencart module
===============

Module allows integrate CMS Opencart >= 2.3 with [RetailCRM](https://retailcrm.pro)

### Previous versions:

[v1.x](https://github.com/retailcrm/opencart-module/tree/v1.x)

[v2.x (2.0, 2.1, 2.2)](https://github.com/retailcrm/opencart-module/tree/v2.2)

#### Features:

* Export orders to RetailCRM & fetch changes back
* Export product catalog into [ICML](https://help.retailcrm.pro/Developers/ICML) format

#### Install

Copy files to the site root

```
unzip master.zip
cp -r opencart-module/src/* /path/to/site/root
```

#### Setup

* Go to Admin -> Extensions -> Modules -> RetailCRM
* Fill you api url & api key
* Specify directories matching

#### Migrating to 4.* from early modules versions

Before you copy the files of module you will to remove the directory `path/to/opencart/system/library/retailcrm`

#### Getting changes in orders

Add to cron:

```
*/5 * * * * /usr/bin/php /path/to/opencart/system/library/retailcrm/cron/history.php >> /path/to/opencart/system/storage/logs/cronjob_history.log 2>&1
```

#### Setting product catalog export

Add to cron:

```
* */4 * * * /usr/bin/php /path/to/opencart/system/library/retailcrm/cron/icml.php >> /path/to/opencart/system/storage/logs/cronjob_icml.log 2>&1
```

Your export file will be available by following url

```
http://youropencartsite.com/retailcrm.xml
```

#### Export existing orders and customers

You want to run this command onecly:
/usr/bin/php /path/to/opencart/system/library/retailcrm/cron/export.php
