FROM ruby:2.6

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y nodejs yarn postgresql-client

WORKDIR /usr/src/app
COPY Gemfile* ./
RUN bundle install
RUN rails new ./
RUN ls -la ./
# COPY . .

EXPOSE 3000
CMD ["rails", "server", "-b", "0.0.0.0"]