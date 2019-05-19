# WPDOCKER

*For Linux Ubuntu*

1. `# git clone https://github.com/rainjeck/wpdocker.git`

2. Create `.env` file in project folder

	`DBPREF=wp`

	`DBPREF` - prefix for Wordpress DB

3. `# docker-compose up -d`

4. Set file permissions:

	`# sudo chown -R user:www-data core && sudo chmod -R 777 core`

	`user` - your username in system

	`core` - Wordpress files folder (config)
	
5. Add these lines in `wp-config.php`
	
	`define('WPLANG', 'ru_RU');` - russian language
	
	`define('FS_METHOD', 'direct');` - for correctly work market of plugins


5. Database uses Adminer and works on port 5050

	`localhost:5050`

6. Site works on port 5000

	`localhost:5000`
