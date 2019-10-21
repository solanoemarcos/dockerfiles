#From base image
FROM ruby:2.5

#RUN apt-get update -qq

#Add NodeJS
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
#Install Yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo 'deb https://dl.yarnpkg.com/debian/ stable main' > /etc/apt/sources.list.d/yarn.list

#Update and install
RUN apt-get update -qq && apt-get install -y yarn build-essential libpq-dev nodejs

#Clean
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    truncate -s 0 /var/log/*lo

#Configure main directory
RUN mkdir /myapp
WORKDIR /myapp

#Copy gemfile
COPY . /myapp
COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock


#install
RUN bundle install

# Add a script to be executed every time the container starts.
#COPY entrypoint.sh /usr/bin/
#RUN chmod +x /usr/bin/entrypoint.sh
#ENTRYPOINT ["entrypoint.sh"]
#EXPOSE 3000

# Start the main process.
# if the server is running from this container
CMD ["rails", "server", "-b", "0.0.0.0"]
# if running from the comspose, comment
