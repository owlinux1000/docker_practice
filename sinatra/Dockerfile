FROM ruby:2.5.0
MAINTAINER mail@alicemacs.com
COPY ./app /app
WORKDIR /app
RUN gem install sinatra
CMD ["ruby", "main.rb", "-o", "0.0.0.0"]
