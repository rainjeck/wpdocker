# WPDOCKER

*For Linux Ubuntu*

1. Create `.env` file in project folder
	`DBPREF=wp`
	`DBPREF` - prefix for Wordpress DB

2. `git clone https://github.com/rainjeck/wpdocker.git`

3. Set file permissions
	`sudo chown -R user:www-data core`
	`suco chown -R 777 core`
	`core` - Wordpress project folder

4. Run `docker-compose up`