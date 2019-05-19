# WPDOCKER

*For Linux Ubuntu*

1. `# git clone https://github.com/rainjeck/wpdocker.git`

2. Create `.env` file in project folder

	`DBPREF=wp`

	`DBPREF` - prefix for Wordpress DB

3. `# docker-compose up -d`

4. Set file permissions:

	`# sudo chown -R user:www-data core`

	`# suco chown -R 777 core`

	`user` - your username in system

	`core` - Wordpress project folder


5. Database uses Adminer and works on port 5050

	`localhost:5050`

6. Site works on port 5000

	`localhost:5000`
