FROM ruby

RUN apt-get -y update 
RUN	apt-get -y install sqlite3 nodejs
RUN	gem update 
RUN	gem install bundler rails

EXPOSE 3000
ONBUILD COPY . /opt/app
ONBUILD RUN rm -fR /opt/app/test.sh
ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install && rails db:migrate && rails db:seed
