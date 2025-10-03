# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
# COMPLETAR
C:\Users\P3E010-D>docker create --name srv-web nginx:alpine
64dd916327266715ead25bfda273df8c3657286036b76e064fb15d57c3c5b370

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
C:\Users\P3E010-D>docker create --name holamundo hello-world
864405d1f2e3e782bfab187878595db079d693a7b104f5a91ca77b1febec31fa

sin nombre
C:\Users\P3E010-D>docker create  hello-world
e8f1224745ee3514eddee72c72009e8e6fadff106be9d355f02d213a7e4c0f82
revisamos 
docker ips -a
# COMPLETAR

### Listar los contenedores ejecutándose o no

```
docker ps -a
```
Run 'docker inspect --help' for more information

C:\Users\P3E010-D>docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                      PORTS     NAMES
e8f1224745ee   hello-world    "/hello"                 About a minute ago   Created                               hardcore_kepler
864405d1f2e3   hello-world    "/hello"                 About a minute ago   Created                               holamundo
64dd91632726   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago        Created                               srv-web
8b57e5b9732d   hello-world    "/hello"                 12 minutes ago       Exited (0) 12 minutes ago             elegant_hugle

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>

```
Iniciar el contenedor srv-web 
C:\Users\P3E010-D>docker start srv-web
srv-web

# COMPLETAR

### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```
C:\Users\P3E010-D>docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS          PORTS     NAMES
64dd91632726   nginx:alpine   "/docker-entrypoint.…"   6 minutes ago   Up 27 seconds   80/tcp    srv-web


### Para detener un contenedor

```
docker stop <nombre contenedor>
```
C:\Users\P3E010-D>docker stop srv-web
srv-web

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR

**¿Qué sucede luego de la ejecución del comando?**
se detuvo, por que el contenedor se ejecuto en primer plano, atrapando el comando, hasta detener el contenedor 
# COMPLETAR  

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

```
C:\Users\P3E010-D>docker run srv-web2 nginx:alpine
Unable to find image 'srv-web2:latest' locally
docker: Error response from daemon: pull access denied for srv-web2, repository does not exist or may require 'docker login'

Run 'docker run --help' for more information

C:\Users\P3E010-D>docker run --name srv-web2 nginx:alpine
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2025/10/03 20:16:34 [notice] 1#1: using the "epoll" event method
2025/10/03 20:16:34 [notice] 1#1: nginx/1.29.1
2025/10/03 20:16:34 [notice] 1#1: built by gcc 14.2.0 (Alpine 14.2.0)
2025/10/03 20:16:34 [notice] 1#1: OS: Linux 6.6.87.2-microsoft-standard-WSL2
2025/10/03 20:16:34 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2025/10/03 20:16:34 [notice] 1#1: start worker processes
2025/10/03 20:16:34 [notice] 1#1: start worker process 30
2025/10/03 20:16:34 [notice] 1#1: start worker process 31
2025/10/03 20:16:34 [notice] 1#1: start worker process 32
2025/10/03 20:16:34 [notice] 1#1: start worker process 33
2025/10/03 20:19:09 [notice] 1#1: signal 2 (SIGINT) received, exiting
2025/10/03 20:19:09 [notice] 30#30: exiting
2025/10/03 20:19:09 [notice] 31#31: exiting
2025/10/03 20:19:09 [notice] 32#32: exiting
2025/10/03 20:19:09 [notice] 30#30: exit
2025/10/03 20:19:09 [notice] 31#31: exit
2025/10/03 20:19:09 [notice] 32#32: exit
2025/10/03 20:19:09 [notice] 33#33: exiting
2025/10/03 20:19:09 [notice] 33#33: exit
2025/10/03 20:19:09 [notice] 1#1: signal 17 (SIGCHLD) received from 33
2025/10/03 20:19:09 [notice] 1#1: worker process 33 exited with code 0
2025/10/03 20:19:09 [notice] 1#1: signal 29 (SIGIO) received
2025/10/03 20:19:09 [notice] 1#1: signal 17 (SIGCHLD) received from 32
2025/10/03 20:19:09 [notice] 1#1: worker process 30 exited with code 0
2025/10/03 20:19:09 [notice] 1#1: worker process 31 exited with code 0
2025/10/03 20:19:09 [notice] 1#1: worker process 32 exited with code 0
2025/10/03 20:19:09 [notice] 1#1: exit

C:\Users\P3E010-D>c
```
para evitar eso, lo creamos en segundo plano y usando -d
### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine

C:\Users\P3E010-D>docker dicker ps
docker: unknown command: docker dicker

Run 'docker --help' for more information
```
C:\Users\P3E010-D>docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS     NAMES
06be77693461   nginx:alpine   "/docker-entrypoint.…"   57 seconds ago   Up 54 seconds   80/tcp    srv-web3
```
# COMPLETAR
```
C:\Users\P3E010-D>docker run  -d --name srv-web3 nginx:alpine
06be77693461978ed2e060b1f0956f113eb83c4bc0193f967879a6a9a4a5b39e
```
### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
C:\Users\P3E010-D>docker rm srv-web3
Error response from daemon: cannot remove container "srv-web3": container is running: stop the container before removing or force remove

Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR
C:\Users\P3E010-D>docker rm holamundo
holamundo

C:\Users\P3E010-D>docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES
06be77693461   nginx:alpine   "/docker-entrypoint.…"   4 minutes ago    Up 3 minutes                80/tcp    srv-web3
07519a3af23a   nginx:alpine   "/docker-entrypoint.…"   8 minutes ago    Exited (0) 5 minutes ago              srv-web2
e8f1224745ee   hello-world    "/hello"                 15 minutes ago   Created                               hardcore_kepler
64dd91632726   nginx:alpine   "/docker-entrypoint.…"   17 minutes ago   Exited (0) 9 minutes ago              srv-web
8b57e5b9732d   hello-world    "/hello"                 26 minutes ago   Exited (0) 26 minutes ago             elegant_hugle

C:\Users\P3E010-D>

Verificar que el contenedor que se eliminó

# COMPLETAR


### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR

Verificar que el contenedor que se eliminó
# COMPLETAR
C:\Users\P3E010-D>docker rm -f srv-web3
srv-web3

C:\Users\P3E010-D>docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                      PORTS     NAMES
07519a3af23a   nginx:alpine   "/docker-entrypoint.…"   9 minutes ago    Exited (0) 6 minutes ago              srv-web2
e8f1224745ee   hello-world    "/hello"                 15 minutes ago   Created                               hardcore_kepler
64dd91632726   nginx:alpine   "/docker-entrypoint.…"   18 minutes ago   Exited (0) 10 minutes ago             srv-web
8b57e5b9732d   hello-world    "/hello"                 26 minutes ago   Exited (0) 26 minutes ago             elegant_hugle
### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR

C:\Users\P3E010-D>docker inspect srv-web3
[]
Error: No such object: srv-web3

<img width="2165" height="1150" alt="image" src="https://github.com/user-attachments/assets/5452463c-e229-4afc-8175-22c559f4b591" />
