# wordpress-template

## このテンプレートを使ってテーマを開発する場合の注意点

### docker-compose.ymlを修正する

wordpressのvolumesを以下のように修正する。

```
wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       
     // ↓ローカルのSampleThemeを、Docker上のSampleThemeにマウントしている
     // テーマのファイル名を変える場合は、ここの名前も変える必要がある。
     volumes:
      - ./SampleTheme:/var/www/html/wp-content/themes/SampleTheme
      
      ~~省略~~
```

## カスタムフィールドの設定

タイトルと本文以外に入力項目を用意したい場合に設定する。
商品詳細ページを作りたい場合、商品名、金額、画像などを設定できる。

参考：
https://ferret-plus.com/8047

参考サイト  

Docker ComposeでWordPressのテーマ開発環境を一瞬で作成する  
https://qiita.com/akiyama01/items/4dcaf889aad8883b4364

wordpressのSampleThemeを生成してくれるサイト  
https://underscores.me/

WordPressオリジナルテーマを作る方法  
https://webst8.com/blog/wordpress-theme-howto-make/
