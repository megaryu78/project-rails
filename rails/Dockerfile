FROM ruby:2.6

RUN wget https://dl.yarnpkg.com/debian/pubkey.gpg && \
    apt-key add ./pubkey.gpg && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y nodejs yarn postgresql-client

WORKDIR /usr/src/app
COPY Gemfile* ./
COPY ./src ./
RUN bundle install
RUN yarn install

EXPOSE 3000
CMD ["rails", "server", "-b", "0.0.0.0", "-e", "development"]