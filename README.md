# WPDOCKER

*For Linux Ubuntu*

1. `git clone https://github.com/rainjeck/wpdocker.git`

2. Create `.env` file in project folder

	`DBPREF=wp`

	`DBPREF` - prefix for Wordpress DB

3. Run `docker-compose up`

4. Set file permissions:

	`sudo chown -R user:www-data core` - `user` - your username in system

	`suco chown -R 777 core`

	`core` - Wordpress project folder


5. Database uses Adminer and works on port 5050

	`localhost:5050`

6. Site works on port 5000

	`localhost:5000`