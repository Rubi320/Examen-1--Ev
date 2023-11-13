
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
    
    ¿Para que sirve el registro CNAME? Pon un ejemplo
    ¿Como puedo hacer para que la configuración de un contenedor DNS no se borre si creo otro contenedor?
    Añade una zona tiendadeelectronica.int en tu docker DNS que tenga
        www a la IP 172.16.0.1
        owncloud sea un CNAME de www
        un registro de texto con el contenido "1234ASDF"
        Comprueba que todo funciona con el comando "dig"
        Muestra en los logs que el servicio arranca correctamente
    Realiza el apartado 9 en la máquina virtual con DNS
