FROM nginx:1.15.4-alpine

# chown necessary files
RUN touch /var/run/nginx.pid \
  && chown -R nginx:nginx /var/run/nginx.pid \
  && chown -R nginx:nginx /var/cache/nginx

# default to port 8080, remove user conf, default to stdout error logs
RUN sed -i s/80\;/8080\;/g /etc/nginx/conf.d/default.conf \
  && sed -i s/user\ *nginx\;//g /etc/nginx/nginx.conf \
  && sed -i 's=/var/log/nginx/error\.log\ warn;=/dev/stdout\ info;=g' /etc/nginx/nginx.conf

# security scan
ARG AQUA_MICROSCANNER_TOKEN
RUN apk add --no-cache ca-certificates \
  && wget -O /microscanner https://get.aquasec.com/microscanner \
  && chmod +x /microscanner \
  && /microscanner ${AQUA_MICROSCANNER_TOKEN} \
  && rm -rf /microscanner \
  && apk del ca-certificates

# use non-root user
USER nginx
