FROM nginx
ENV DEBIAN_FRONTEND=noninteractive
RUN apt -qy update && apt -qy upgrade
RUN apt -qy install git fcgiwrap
RUN sed -i 's/^\(user .*\)$/user root;/' /etc/nginx/nginx.conf

COPY nginx-git-http.conf /etc/nginx/conf.d/default.conf
VOLUME /git
CMD spawn-fcgi -s /var/run/fcgiwrap.socket -n /usr/sbin/fcgiwrap & exec nginx -g "daemon off;"
EXPOSE 80
