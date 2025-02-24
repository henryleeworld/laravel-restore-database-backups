# Laravel 11 還原資料庫備份

引入 wnx 的 laravel-backup-restore 套件來擴增還原資料庫備份，用於現有的資料毀了，或遇到需要復原的特殊狀況，讓資料可以被拯救還原回來。

## 使用方式
- 打開 php.ini 檔案，啟用 PHP 擴充模組 zip，並重啟服務器。
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __Artisan__ 指令的 __migrate__ 來執行所有未完成的遷移。
```sh
$ php artisan migrate
```
- 執行 __Artisan__ 指令的 __backup:run__ 來執行對資料庫進行備份。
```sh
$ php artisan backup:run
```
- 執行 __Artisan__ 指令的 __backup:restore__ 來執行對資料庫進行備份還原。
```sh
$ php artisan backup:restore
```

----

## 畫面截圖
![](https://i.imgur.com/yWhrGpE.png)
> 將資料庫儲存至備份檔來製作資料庫的副本

![](https://i.imgur.com/M5ZdK6m.png)
> 選擇資料庫備份檔，然後還原資料庫
