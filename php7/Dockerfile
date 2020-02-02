FROM fadlee/php7-fpm

ENV TIMEZONE Asia/Jakarta

RUN apk add --no-cache tzdata git \
  && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
  && echo "${TIMEZONE}" > /etc/timezone \
  && apk del tzdata

# make www-data user id:33
RUN sed -i '/xfs/d' /etc/group && sed -i '/xfs/d' /etc/passwd \
  && sed -i 's/82:82/33:33/' /etc/passwd \
  && sed -i 's/x:82/x:33/' /etc/group \

  && addgroup -g 1000 -S motekar \
  && adduser -u 1000 -D -S -G motekar motekar

CMD ["php-fpm"]
