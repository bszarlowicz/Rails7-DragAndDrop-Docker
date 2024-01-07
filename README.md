# Rails7/Bootstrap/Docker

Rails 7 app with bootstrap and docker configuration (Windows):

Step by step instruction:

- Bootstrap connection:  https://jasonfleetwoodboldt.com/courses/rails-7-crash-course/
- In Dockerfile:
    1. remove:
         ``` RUN SECRET_KEY_BASE_DUMMY=1 ./bin/rails assets:precompile ```
    3. add:
         ``` RUN apt-get update && \ apt-get install -y nodejs ```
- In Dockerignore:
    1. remove:
         ``` /public/assets ```
- In config/environment/production.rb:
    1. change:
         ```config.force_ssl = true``` to ```config.force_ssl = false```
    3. change:
         ``` config.assets.compile = false ``` to  ```config.assets.compile = true ```
- In console:
    1. Image build:
         ``` docker build . -t <containerName> ```
    3. Start server frome image:
         ``` docker run -p <portNumber>:<portNumber> -e SECRET_KEY_BASE=<key> <containerName> ```
