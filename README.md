
    1.Explica métodos para 'abrir' una consola/shell a un contenedor que se está ejecutando

    ***
   
    Mediante el comando 'docker exec -it 'nuestro contenedor' bash ' accedemos a nuestro contenedor en marcha y ejecutamos una shell.
   
    ***

    2.En el contenedor anterior con que opciones tiene que haber sido arrancado para poder interactuar con las entradas y salidas del contenedor
    
    ***
   
    Debe haber sido arrancado con las opciones que permiten la interectavidad con la terminal, es decir, -i:mantiene la entrada abierta y -t que asigna al contenedor una terminal.
    
    ***

    3.¿Cómo sería un fichero docker-compose para que dos contenedores se comuniquen entre si en una red solo de ellos?
   
    ***
    
    Primero debemos definir una red. Despues en cada contenedor indicar la red definida y darle una IP a cada contenedor.
    
    ***
    
    *Explicado en imagen 'examenEJ3.png'*
    
    
    4.¿Qué hay que añadir al fichero anterior para que un contenedor tenga la IP fija?

    ***
   
    En la imagen anterior lo hemos hecho ya con IP fija pero simplemente en la network que indicamos en cada contenedor añadimos *ipv4_addres:* y asignamos la IP.
   
    *** 


    5.¿Que comando de consola puedo usar para saber las ips de los contenedores anteriores? Filtra todo lo que puedas la salida.

    ***
    Con *docker inspect 'nombre contenedor'* obtenemos una informacion detallada del contenedor. Si queremos saber solo la ip basta con añadir -f para filtrar y {.IPAddress} para que nos muestre su IP.
    
    ***


    6.¿Cual es la funcionalidad del apartado "ports" en docker compose?

    ***

    Nos permite mapear los puertos entre el host y el contenedor. Por ejemplo:
    
    services:
        ports:
        - "90:80"
    
    El puerto 80 del contenedor se mapea al puerto 90 del host

    ***

    7.¿Para que sirve el registro CNAME? Pon un ejemplo

    ***

    Permite crear un alias de un nombre de dominio. Es decir asocia los dominios y permite que se resuelvan con la misma IP.
    Ej: Tengo dos dominios rubi1.com y subdominio.rubi1.com quiero que el subdominio apunte a otro servidor. 
            subdominio.rubi1.com in CNAME servidor_nuevo
    Cuando se resuelve la IP del subdominio nos dirije al servidor_nuevo.

    ***


    8.¿Como puedo hacer para que la configuración de un contenedor DNS no se borre si creo otro contenedor?

    ***

    Utilizamos volumenes, mapeamos los directorios del contenedor con directorios del host.
    
    ***

    *Explicado en la imagen : examenEJ8.png*

    9.Añade una zona tiendadeelectronica.int en tu docker DNS que tenga
        www a la IP 172.16.0.1
        owncloud sea un CNAME de www
        un registro de texto con el contenido "1234ASDF"
        Comprueba que todo funciona con el comando "dig"
        Muestra en los logs que el servicio arranca correctamente
   
    *Explicado en : examenEJ9.1,examenEJ9.2,examenEJ9.3,examenEJ9.4*

    No fui capaz de que funcione siguiendo los pasos poco a poco no soy capaz de encontrar el error en el caso de que exista.
    La zona esta bien definida, el contenedor bien mapeado pero aun asi no funciona.

   
    10.Realiza el apartado 9 en la máquina virtual con DNS

    *Explicado en : examenEJ10.1,examenEJ10.2,examenEJ10.3,examenEJ10.4*

    ***
    Nos ocurre lo mismo que en el apartado anterior, aun siguiendo los pasos el dig no devuelve una respuesta.

    ***

    *Las busquedas con dig para ambos apartados serian*
        -dig www.tiendadeelectronica.int : tendria que devolver 172.16.0.1
        -dig owncloud.tiendadeelectronica.int: tendria que devolver www.tiendadeelectronica.int
        -dig txt tiendadeelectronica.int: que devolveria 1234ASDF