# we need a mysql image and we will copy our sql file into it
FROM mysql:8.0.33
LABEL "Project"="Vprofile"
LABEL "Author"="anhnm"

# set the password, can give a fake password here and override this when run the container
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
# set this var so when creating the container it will create a db with the name 'accounts'
ENV MYSQL_DATABASE="accounts"

# add our sql file into the image (into the folder mentioned in the doc)
ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql

# EXPOSE 3306 is already in the mysql base image -> don't need to give it