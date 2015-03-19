# Wordpress-composer

> Composer setup to separate Wordpress core files from themes and plugins.
> Moves Wordpress core to a separate folder (`/wp/` by default).

## Install

Install Wordpress core files:

- `~$ composer install`
- Rename `sample.htaccess` to `.htaccess`; and edit `PATH_TO_BLOG_DIR`.
- Rename `sample.wp-config.php` to `wp-config.php`; and edit `PATH_TO_BLOG_DIR` + database connection settings.


## Modify install path

By default, Wordpress core will be installed inside /wp/.

To modify the install path, you'll need to edit:

- `composer.json`:
```
  "webroot-dir": "wp",
```
- `sample.wp-config.php`: 
```
define( 'ABSPATH', dirname( __FILE__ ) . '/wp/' );
```
- `index.php`:
```
require( dirname( __FILE__ ) . '/wp/wp-blog-header.php' );
```
- `sample.htaccess`:
```
RewriteRule ^([_0-9a-zA-Z-]+/)?(wp-(content|admin|includes).*) wp/$2 [L]
RewriteRule ^([_0-9a-zA-Z-]+/)?(.*\.php)$ wp/$2 [L]
```


### Notes

- Theme and plugins inside `/wp-content/`.
- Whitelist plugins and themes in `.gitignore`.
