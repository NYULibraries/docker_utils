FROM nginx:1.15.4-alpine

# default to port 8080
RUN sed -i s/80\;/8080\;/g /etc/nginx/conf.d/default.conf

# chown necessary files
RUN touch /var/run/nginx.pid && \
  chown -R nginx:nginx /var/run/nginx.pid && \
  chown -R nginx:nginx /var/cache/nginx

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
