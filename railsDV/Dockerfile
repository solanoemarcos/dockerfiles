#From base image
FROM ruby:2.5

#Update and install
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

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
EXPOSE 3000

# Start the main process.
# if the server is running from this container
#CMD ["rails", "server", "-b", "0.0.0.0"]
# if running from the comspose, comment