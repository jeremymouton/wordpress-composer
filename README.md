# Wordpress-composer

> Composer setup to separate Wordpress core files from themes and plugins.
> Moves Wordpress core to `/wp/`.

## Install

Install Wordpress core files:

- `~$ composer install`
- Rename `/sample.htaccess` to `/.htaccess`; and edit `PATH_TO_BLOG_DIR`.
- Rename `/sample.wp-config.php` to `/wp-config.php`; and edit `PATH_TO_BLOG_DIR` + database connection settings.


### Notes

- Theme and plugins inside `/wp-content/`.
- Whitelist plugins and themes in `/.gitignore`.