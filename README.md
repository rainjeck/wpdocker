# WPDOCKER

*For Linux Ubuntu*

1. `git clone https://github.com/rainjeck/wpdocker.git`

2. Create `.env` file in project folder

	`DBPREF=wp`

	`DBPREF` - prefix for Wordpress DB


3. Set file permissions

	`sudo chown -R user:www-data core`

	`suco chown -R 777 core`

	`core` - Wordpress project folder

4. Run `docker-compose up`

5. Database use Adminer and work on port 5050

	`localhost:5050`

6. Site work on port 5000

	`localhost:5000`