# laravel-docker
Just Note for Laravel Development with Docker

Step 1 — Downloading Laravel and Installing Dependencies

$ cd ~
$ git clone https://github.com/laravel/laravel.git laravel

$ cd laravel 

Next, use Docker's composer image to mount the directories that you will need for your Laravel project and avoid the overhead of installing Composer globally:

$ docker run --rm -v $(pwd):/app composer install

Set permission for non-root user

$ sudo chown -R $USER:$USER ~/laravel

Step 2 — Creating the Docker Compose File

Copy from docker-compose.yml and paste it 

Step 4 — Creating the Dockerfile

Copy from dockerfile 

Step 5 — Configuring PHP,Nginx,Mysql 

Create needed folder in root(project) direcroy.such as nginx,php,mysql etc...
And copy from all of my config to your local

Step 6 — Running the Containers and Modifying Environment Settings

$ cp .env.example to .env in your local project

$ docker-compose up -d (-d is the flag daemonizes the process, running your containers in the background.)

After all, you can see the running container with $ docker ps.

You can now modify the .env file on the app container to include specific details about your setup.

use docker-compose  exec 

You can edit now your laravel env with the following command.(Note-if you want to use nano editor,firstly you already installed this while building your conatiner)
In my case,I used vim editor,so 
docker-compose exec app vim .env

Next things to do is to generate key for your laravel application
docker-compose exec app php artisan key:generate

Next is to config cache 
docker-compose exec app php artisan config:cache

Ohh now,You can browse your laravel app with http://localhost:80 
Bango!!!