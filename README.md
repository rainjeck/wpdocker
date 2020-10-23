# WPDOCKER

*For Linux Ubuntu*

1. `# git clone https://github.com/rainjeck/wpdocker.git .`

2. Change DB prefix in `docker-compose.yml`

3. `# docker-compose up -d`

4. Set file permissions:

	`# sudo chown -R :www-data public && sudo chmod -R 777 public`

	`public` - Wordpress files folder from docker-compose.yml

5. Add in `wp-config.php`

	```
	define( 'FS_METHOD', 'direct' );
	define( 'DISALLOW_FILE_EDIT', true );
	```

6. Hide WP - `wp-content` to `assets` folder. Add lines before install. Rename `wp-content` to `assets`.

	`# mv public/wp-content public/assets`

	```
	define( 'WP_CONTENT_DIR', dirname(__FILE__) . '/assets' );
	define( 'WP_CONTENT_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/assets' );
	define( 'WP_PLUGIN_DIR', dirname(__FILE__) . '/assets/plugins' );
	define( 'WP_PLUGIN_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/assets/plugins' );
	define( 'UPLOADS', 'assets/uploads' );
	```

8. Setup theme

	`# git clone https://github.com/rainjeck/wordpress.git public/assets/themes/apptheme`

9. Create link to theme folder

	`# ln -r -s public/assets/themes/apptheme apptheme`

10. **Start installation**

11. Database uses Adminer and works on port **8080**: `localhost:8080`

11. Site works on port **5000**: `localhost:5000`

9. htaccess

	```
	AddDefaultCharset UTF-8

	# BEGIN WordPress
	<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteBase /
	RewriteRule ^index\.php$ - [L]
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule . /index.php [L]
	</IfModule>
	# END WordPress
	```

10. WWW & HTTP to without WWW & HTTPS
	```
	RewriteEngine On
	RewriteBase /

	RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
	RewriteRule ^(.*)$ https://%1/$1 [R=301,L]

	RewriteCond %{HTTPS} !=on
	RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R,L]
	```

11. [Robots.txt](https://gist.github.com/rainjeck/4cadf694438e69db4122d93966b4f49e)
