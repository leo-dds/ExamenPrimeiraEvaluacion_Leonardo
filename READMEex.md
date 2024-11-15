# ExamenPrimeiraEvaluacion_Leonardo


Crea un repositorio para contestar todo o exame.
Este repositorio ten que conter tódo-los ficheiros necesarios para xustifica-la túas respostas.

Contesta as seguintes preguntas, xustificándoas, nun README.md

1. Explica métodos para 'abrir' unha consola/shell a un contenedor en execución.
2. No contenedor anterior (en execución), qué opciones tes que ter usado ó arrincalo para poder interactuar coas súas entradas e salidas
3. Cómo sería un ficheiro docker-compose para que dous contenedores se comuniquen entre si nunha rede só deles?
4. Qué tes que engadir ó ficheiro anterior para que un contenedor teña unha IP fixa?
5. Qué comando de consola podo usar para sabe-las ips dos contenedores anteriores?
6. Cál é a funcionalidade do apartado "ports" en docker compose?
7. Para qué serve o rexistro CNAME? Pon un exemplo
8. Cómo podo facer para que a configuración dun contenedor DNS non se borre se creo outro contenedor?
9. Engade unha zoa tendaelectronica.int no teu docker DNS que teña:
- www á IP 172.16.0.1
- owncloud sexa un CNAME de www
- un rexistro de texto có contido "1234ASDF"
Comproba que todo funciona có comando "dig"
Mostra nos logs que o servicio funciona ben usando a saída da terminal ó levantar o compose ou có comando "docker logs [nomeContenedorOuID]"
(o apartado 9 realízase na máquina virtual)
