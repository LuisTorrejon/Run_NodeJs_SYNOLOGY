# Run_NodeJs_SYNOLOGY
How NodeJS works on SYNOLOGY, first stepts

How to run NodeJS server instructions
0. Crear un archivo llamado run_NodeJS.js
    
    var http = require('http');

    http.createServer(function (req, res) {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello World!');
    }).listen(8080);
    
1. Se copia el archivo run_NodeJS.js en la carpeta donde quieras arrancar el servidor

2. Te conectas a traves de terminal SSH al servidor 

3. node /....donde tengas guardado el archivo run_NodeJS

4. desde el navegador comprobamos que se accede al puerto 8080 y vemos 'hello world'

*Si hubiera otro servidor hablando desde otro puerto no se veria el servidor

5. Hacer que se inicie el archivo al arrancar el dispositivo

5.a Logearse desde la terminal SSH
5.b cd /etc/init
5.c sudo vi ****.conf
5.d press i to insert
5.f Insertar:

    Description "test application for Node.js"
    author "****"

    start on syno.share.ready
    stop on runlevel [06]

    # run the script as the 'http' user. The default  is runnning as root which is not recommended
    setuid http

    # execute the application
    exec node /volume1/web/test.js

5.g How to start the process manually
    sudo start test
    sudo stop test


Comandos vi
    i para Insertar
    esc, depues :wq -- guardar y salir

