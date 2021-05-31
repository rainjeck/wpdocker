# WPDOCKER

*Was made for Linux*

`# git clone https://github.com/rainjeck/wpdocker.git .`

1. Change DB prefix in `docker-compose.yml`

2. `# docker-compose up -d`

3. Set file permissions:

	`# sudo chown -R <user>:www-data public && sudo chmod -R 777 public`

	`public` - Wordpress files folder from docker-compose.yml

4. Add in `wp-config.php`

	```
	define( 'FS_METHOD', 'direct' );
	define( 'DISALLOW_FILE_EDIT', true );
	```

5. Hide WP - `wp-content` to `assets` folder. Add lines before install. Rename `wp-content` to `assets`.

	`# mv public/wp-content public/assets`

	```
	define( 'WP_CONTENT_DIR', dirname(__FILE__) . '/assets' );
	define( 'WP_CONTENT_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/assets' );
	define( 'WP_PLUGIN_DIR', dirname(__FILE__) . '/assets/plugins' );
	define( 'WP_PLUGIN_URL', 'http://' . $_SERVER['HTTP_HOST'] . '/assets/plugins' );
	define( 'UPLOADS', 'assets/uploads' );
	```

6. **Start Wordpress installation**

	Site: `localhost:5000`

	Adminer: `localhost:8080`

7. [Theme Template](https://github.com/rainjeck/wordpress)

    ```
    Create link to theme folder

    # ln -r -s public/assets/themes/<theme> <link_name>
    ```


## Add libs for optimize images

```
# docker-compose ps

<container_id> - wordpress container

# docker exec -it <container_id> bash
# apt-get update
# apt-get install jpegoptim pngquant optipng
```


## Image Sizes

```
thumbnail 100
medium 1024
medium_large 1440
large 2048

thumblarge 500x500 crop (from theme template)
```
