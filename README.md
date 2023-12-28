## git
https://github.com/chiba0/ewel8_backend/tree/master

## 参考
https://qiita.com/ucan-lab/items/56c9dc3cf2e6762672f4

# docker-laravel-handson
 docker compose up -d

## into php
 docker compose exec app bash

## コンテナ破棄
 docker compose down

## composer (vendorフォルダを作る)
 composer install

## キーの発行
php artisan key:generate

## mysql
docker compose exec db mysql -V

## migrateの実行
docker compose exec app bash
php artisan migrate

## mysql接続
docker compose exec db bash

mysql -u $MYSQL_USER -p$MYSQL_PASSWORD $MYSQL_DATABASE

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| laravel            |
| performance_schema |



## 試しにデータを作る
chiba@chiba:~/ewel8_backend/src$ docker compose exec app bash
root@3f344b3a554e:/data# php artisan tinker
```
>>> $user = new App\Models\User();
user->name = 'phper';
$user->email = 'phper@example.com';
$user->password = Hash::make('secret');
$user->save();=> App\Models\User {#3501}
>>> $user->name = 'phper';
=> "phper"
>>> $user->email = 'phper@example.com';
=> "phper@example.com"
>>> $user->password = Hash::make('secret');
=> "$2y$10$QrUhmenFrCW0B6KNSOMBpe37aJm6QfWiS.qKiMsQMRHwxoBisjLiO"
>>> $user->save();
=> true
>>>
```
### データの確認

mysql> SELECT * FROM users\G
*************************** 1. row ***************************
               id: 1
             name: phper
            email: phper@example.com
email_verified_at: NULL
         password: $2y$10$QrUhmenFrCW0B6KNSOMBpe37aJm6QfWiS.qKiMsQMRHwxoBisjLiO
   remember_token: NULL
       created_at: 2023-12-28 16:23:30
       updated_at: 2023-12-28 16:23:30
1 row in set (0.00 sec)
