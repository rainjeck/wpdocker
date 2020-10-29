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

7. Setup theme

	`# git clone https://github.com/rainjeck/wordpress.git public/assets/themes/apptheme`

8. Create link to theme folder

	`# ln -r -s public/assets/themes/apptheme apptheme`

9. **Start installation**

Database uses Adminer and works on port **8080**: `localhost:8080`
Site works on port **5000**: `localhost:5000`

10. [Robots.txt](https://gist.github.com/rainjeck/4cadf694438e69db4122d93966b4f49e)

11. Add libs for optimize images

    `<container_id>` - wordpress container

    ```
    docker exec -it <container_id> bash
    apt-get update
    apt-get install jpegoptim pngquant optipng
    ```
