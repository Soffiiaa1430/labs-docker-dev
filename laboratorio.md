docker pull nginx:
Using default tag: latest
latest: Pulling from library/nginx
efc2b5ad9eec: Pull complete 
8fe9a55eb80f: Pull complete 
045037a63be8: Pull complete 
7111b42b4bfa: Pull complete 
3dfc528a4df9: Pull complete 
9e891cdb453b: Pull complete 
0f11e17345c5: Pull complete 
Digest: sha256:6af79ae5de407283dcea8b00d5c37ace95441fd58a8b1d2aa1ed93f5511bb18c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest


## Ejercicios 1.1.: Descarga la imagen oficial de Ubuntu:
```sh
docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

docker pull python:3.9
3.9: Pulling from library/python
ca4e5d672725: Pull complete 
30b93c12a9c9: Pull complete 
10d643a5fa82: Pull complete 
d6dc1019d793: Pull complete 
c7d45ab0573c: Pull complete 
564d1c451ea7: Pull complete 
ddfb50ba1977: Pull complete 
91b87d81d4c8: Pull complete 
Digest: sha256:65438c2e26dbf9f5db4b5553e332747fa20722c1b7c7ccc6f8480396ff4186db
Status: Downloaded newer image for python:3.9
docker.io/library/python:3.9


## Ejercicios 2.1.: Ejecuta un contenedor de Ubuntu en modo interactivo
root@39877f4543dc:/#

##2.2. Ejecuta un servidor web Apache en segundo plano, mapeando el puerto 8000 del host al puerto 80 del contenedor:
Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
efc2b5ad9eec: Already exists 
fce1785eb819: Pull complete 
4f4fb700ef54: Pull complete 
f214daa0692f: Pull complete 
05383fd8b2b3: Pull complete 
88ad12232aa1: Pull complete 
Digest: sha256:932ac36fabe1d2103ed3edbe66224ed2afe0041b317bcdb6f5d9be63594f0030
Status: Downloaded newer image for httpd:latest
e0fb141f88f955d654807c5c00e8878e2e47385b344907e71451d6a56d4992a1


## Ejercicios 3.1.: Elimina el contenedor de Ubuntu que creaste en el ejercicio 2.1:
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                        PORTS                                   NAMES
e0fb141f88f9   httpd     "httpd-foreground"       13 minutes ago   Up 13 minutes                 0.0.0.0:8000->80/tcp, :::8000->80/tcp   romantic_bose
f7525b4a4c8f   nginx     "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes                 0.0.0.0:8080->80/tcp, :::8080->80/tcp   trusting_tesla
39877f4543dc   ubuntu    "bash"                   16 minutes ago   Exited (0) 14 minutes ago                                             confident_yalow
96d9b293cf18   ubuntu    "bash"                   19 minutes ago   Exited (130) 18 minutes ago                                           musing_hugle

##3.2. Elimina todos los contenedores detenidos:
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
96d9b293cf18a41cb4ae94c48f5569fcc5e0890a68b51b237cd54e10fcae3bae

Total reclaimed space: 5B


#Ejercicio 1: Crear un Dockerfile simple con Ubuntu y actualizar paquetes

docker build -t ubuntu-updated:latest .
[+] Building 9.8s (6/6) FINISHED                        docker:default
 => [internal] load build definition from Dockerfile              0.1s
 => => transferring dockerfile: 97B                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest  0.0s
 => [internal] load .dockerignore                                 0.1s
 => => transferring context: 2B                                   0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                    0.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y                8.5s
 => exporting to image                                            0.6s 
 => => exporting layers                                           0.4s 
 => => writing image sha256:01e18ee1b0381bae90ec39b6c49fbd556b20  0.0s 
 => => naming to docker.io/library/ubuntu-updated:latest


##Ejercicio 3: Crear un Dockerfile para instalar Nginx en Ubuntu
[+] Building 0.5s (6/6) FINISHED                        docker:default
 => [internal] load build definition from Dockerfile              0.1s
 => => transferring dockerfile: 137B                              0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest  0.0s
 => [internal] load .dockerignore                                 0.1s
 => => transferring context: 2B                                   0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                    0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx   0.0s
 => exporting to image                                            0.1s
 => => exporting layers                                           0.0s
 => => writing image sha256:328062377be60acb607ed55bd77ba85222e0  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest


 ##Ejercicio 4: Construir y ejecutar la imagen de Nginx

##Construir:
[+] Building 0.4s (6/6) FINISHED                        docker:default
 => [internal] load build definition from Dockerfile              0.0s
 => => transferring dockerfile: 137B                              0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest  0.0s
 => [internal] load .dockerignore                                 0.0s
 => => transferring context: 2B                                   0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                    0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx   0.0s
 => exporting to image                                            0.1s
 => => exporting layers                                           0.0s
 => => writing image sha256:328062377be60acb607ed55bd77ba85222e0  0.0s
 => => naming to docker.io/library/my-nginx:latest 


##Ejecutar:
11294e088fb1562756c5039f791020bb596977bb671b92980fbe3ee1523a4307

