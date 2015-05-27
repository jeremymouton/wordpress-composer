# Wordpress-composer

> Composer setup to separate Wordpress core files from themes and plugins.<br>
> Moves Wordpress core to a separate folder (`/wp/` by default).

## Installation

#### 1. Install Wordpress
Run `~$ composer install` to install Wordpress to the `/wp` folder.

#### 2. Configure custom paths

###### wp-config.php
- Rename `sample.wp-config.php` to `wp-config.php`
- Edit `WP_SITE_PATH` with site path (i.e `http://localhost/PATH_TO_SITE`, no trailing slash)
- Configure database settings
- Replace salt ([secret-key service](https://api.wordpress.org/secret-key/1.1/salt/))

###### .htaccess
- Rename `sample.htaccess` to `.htaccess`
- **If accessing site via http://localhost/:** <br> Uncomment `RewriteBase` and edit `PATH_TO_SITE` (same as `PATH_TO_SITE` in `wp-config.php`, but without `http://localhost/` and with trailing slash).

#### 3. Add wp-content files

Copy theme and plugin folders to `/wp-content/themes` and `/wp-content/plugins`.

#### 4. Activate theme

If not already activated, login to the Wordpress admin (`http://localhost/PATH_TO_SITE/wp-admin/`). From the sidebar go to `Appearance > Themes`, and activate the theme.

---

## Modifying installation path

By default, Wordpress core will be installed inside /wp/.

To modify the install path, you'll need to edit:

###### composer.json:
`"webroot-dir": "wp",`
###### sample.wp-config.php:
`define( 'ABSPATH', dirname( __FILE__ ) . '/wp/' );`
###### index.php:
`require( dirname( __FILE__ ) . '/wp/wp-blog-header.php' );`
###### sample.htaccess:
`RewriteRule ^([_0-9a-zA-Z-]+/)?(wp-(content|admin|includes).*) wp/$2 [L]`<br>
`RewriteRule ^([_0-9a-zA-Z-]+/)?(.*\.php)$ wp/$2 [L]`

---

### Development notes

- Theme and plugins inside `/wp-content/`.
- Whitelist plugins and themes in `.gitignore`.
