# WPDOCKER

*For Linux Ubuntu*

1. `# git clone https://github.com/rainjeck/wpdocker.git`

2. Change DB prefix

3. `# docker-compose up -d`

4. Set file permissions:

	`# sudo chown -R :www-data core && sudo chmod -R 777 core`

	`core` - Wordpress files folder from docker-compose.yml

5. Add these lines in `wp-config.php`

	```
	define('WPLANG', 'ru_RU');
	define('FS_METHOD', 'direct');
	```

6. Hide WP - 'wp-content' to 'data' folder. Add lines before install. Rename 'wp-content' to 'data'.

	```
	define( 'WP_CONTENT_DIR', dirname(__FILE__) . '/data' );
	define( 'WP_CONTENT_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/data' );
	define( 'WP_PLUGIN_DIR', dirname(__FILE__) . '/data/plugins' );
	define( 'WP_PLUGIN_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/data/plugins' );
	define( 'UPLOADS', 'data/uploads' );
	```

7. Database uses Adminer and works on port 8080

	`localhost:8080`

8. Site works on port 5000

	`localhost:5000`

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
