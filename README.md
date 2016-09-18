# docker-phoenix
Dockerfile ideal for testing Phoenix applications. Given it also contains
Elixir, it can also be used to test other types of Elixir apps.

However, given a bunch of other components are also pre-installed such as
ImageMagick, PhantomJS etc, it's more specialised towards Phoenix apps.

## Example Dockerfile
```
FROM marvellousmutants/phoenix:latest

# Install phantomjs
RUN npm install -g phantomjs-prebuilt

# Create working directory
RUN mkdir /app
WORKDIR /app

# Get your app and add it to the working directory
ADD . /app

# Get and compile hex dependencies
RUN mix deps.clean --all
RUN mix deps.get
RUN mix deps.compile

# Run the test suite!
RUN mix test
```
