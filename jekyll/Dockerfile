FROM ruby:2.3-alpine


ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN apk add --update build-base git libffi-dev libxml2-dev libxslt-dev && rm -rf /var/cache/apk/*
RUN bundle config build.nokogiri --use-system-libraries
RUN gem install bundler
RUN mkdir -p /usr/share/nginx/html

# Replace this with ADD . /data/jekyll-source when running from source dir
RUN git clone https://github.com/johnotander/pixyll.git /data/jekyll-source
WORKDIR /data/jekyll-source
RUN bundle install

CMD ["bundle", "exec", "jekyll", "build", "--destination=/usr/share/nginx/html"]
