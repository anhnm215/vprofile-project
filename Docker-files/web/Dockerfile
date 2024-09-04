# use latest tag
FROM nginx
LABEL "Project"="Vprofile"
LABEL "Author"="anhnm"

# need to change config in the nginx base image
# nginx main config file: /etc/nginx/nginx.conf (from image doc)
# our own config can be pushed in /etc/nginx/conf.d -> can have multiple config in that dir
# we will remove the default config file and put our own config file in there
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf
