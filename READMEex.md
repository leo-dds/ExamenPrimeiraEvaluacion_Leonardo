# ExamenPrimeiraEvaluacion_Leonardo


Crea un repositorio para contestar todo o exame.
Este repositorio ten que conter tódo-los ficheiros necesarios para xustifica-la túas respostas.

Contesta as seguintes preguntas, xustificándoas, nun README.md

1. Explica métodos para 'abrir' unha consola/shell a un contenedor en execución.
Una de las formas con las que podemos abrir una consola a un contenedor en ejecucion es son **exec** este podria ser un ejemplo  docker exec -it ejemplo_contenedor bash.

Otra forma es con **sudo docker run -it  --name ejemplo ubuntu** que crea y abre directamnete el contenedor al tener -it delande.



2. No contenedor anterior (en execución), qué opciones tes que ter usado ó arrincalo para poder interactuar coas súas entradas e salidas


3. Cómo sería un ficheiro docker-compose para que dous contenedores se comuniquen entre si nunha rede só deles?
~~~
 cat docker-compose.yml 
version: '3.8'

services:
  dns_server:
    image: ubuntu/bind9
    container_name: dns_server
    networks:
      dns_network:
        ipv4_address: 172.21.0.2
    volumes:
      - ./bind_config:/etc/bind
    environment:
      - BIND9_USER=root
    command: ["-g", "-c", "/etc/bind/named.conf"]

  dns_client:
    image: alpine
    container_name: dns_cliente
    networks:
      dns_network:
    depends_on:
      - dns_server
    entrypoint: ["/bin/sh", "-c", "apk add --no-cache bind-tools && sleep infinity"]

networks:
  dns_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.21.0.0/16
~~~

4. Qué tes que engadir ó ficheiro anterior para que un contenedor teña unha IP fixa?
Añadiendole en el apartado de network una ip fija de la misma red


5. Qué comando de consola podo usar para sabe-las ips dos contenedores anteriores?

Con **docker ps -a** te dara una lista de todos los contenedores que estan creados, con  **sudo ip a** puedes ver todas las ip de todos esos contenedores.


6. Cál é a funcionalidade do apartado "ports" en docker compose?

Es un documento con el cual podemos crear una serie de contenedores que se puedan comunicar entre ellos en una misma red que configuraremos en el.


7. Para qué serve o rexistro CNAME? Pon un exemplo

En el se guardan otros alias de otros dominios al que te redirigen los subdominios al no encontrar ellos una respuesta completa


8. Cómo podo facer para que a configuración dun contenedor DNS non se borre se creo outro contenedor?


9. Engade unha zoa tendaelectronica.int no teu docker DNS que teña:
- www á IP 172.16.0.1
- owncloud sexa un CNAME de www
- un rexistro de texto có contido "1234ASDF"
Comproba que todo funciona có comando "dig"
Mostra nos logs que o servicio funciona ben usando a saída da terminal ó levantar o compose ou có comando "docker logs [nomeContenedorOuID]"
(o apartado 9 realízase na máquina virtual)
