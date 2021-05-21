#### Tested on Linux Mint 20.1 Cinamon
1. Rename this folder for project
2. Edit app name in Dockerfile and docker-compose.yml (webgram_dc in example)
3. Run:
    docker-compose run web rails new . -T --force --database=postgresql
    sudo chown -R $USER:$USER .
    docker-compose build
4. Edit config/database.yml. Add host, user and password to default. Example:

   default: &default
      adapter: postgresql
      encoding: unicode
      pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
      host: db
      username: postgres
      password: password

5. Run:
    docker-compose up
6. Run in ANOTHER terminal:
    docker-compose run web rake db:create
7. Go to http://localhost:3000 or smth

##### additional
###### stop all containers
 - docker stop $(docker ps -q) 
###### delete all containers
 - docker rm $(docker ps -a -f status=exited -q)
###### delete all images
 - docker rmi $(docker images -a -q) 

    

# easyrails
