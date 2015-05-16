# my-docker-images
*My Docker Images For Personal Testing*

Builds on top of the official WordPress docker image
- Increases upload limit to 32MB
- Adds WP-Mail-SMTP plugin
- Adds WP-Super Cache plugin

###Using the image via docker:

docker run --name mysql -e MYSQL_ROOT_PASSWORD=yourpasswordgoeshere -d mysql

docker run --name wordpress --link mysql:mysql -d -p 80 chucklingalong/wordpress

###Using the image with a separate container for data:

docker run -d --name wp-data chucklingalong/data tail -f /dev/null

docker run --name mysql --volumes-from wp-data 
 -e MYSQL_ROOT_PASSWORD=yourpasswordgoeshere -d mysql

docker run --name wordpress --volumes-from wp-data 
 --link mysql:mysql -d -p 1080:80 chucklingalong/wordpress



