Este repositorio contiene todo el material necesario para
realizar la práctica: "Builds de DevOps usando Jenkins"
para la materia de Auditoria de Sistemas 2017, Ues FMOcc.


*** Prerequisitos ***

- Docker y docker-compose instalado en su pc

- Una copia de este repositorio en su pc. Puede clonarlo 
ejecutando desde una consola:

	git clone https://github.com/proundmega/auditoria2017-devops.git

- Una con buen CPU o bien, paciencia

- Deseos de aprender y de seguir las indicaciones



*** Uso ***

Para iniciar todos los servicios que necesitará en el transcurso
de este tutorial, ejecute el archivo init.sh que está en el
directorio raiz de este repo desde una consola, asi:

	bash deploy.sh

Y siga las instrucciones contenidas en este archivo...


*** Detalles ***

En esta práctica se proporciona una app sencilla hecha en Java con fines 
explicativos nada más. Lo que se busca es compilar automáticamente el app
una vez un programador haga commit al código de la app.

Se desea aplicar un pipeline con varios pasos:

- Pruebas unitarias
- Pruebas de integración
- Todas las pruebas
- Análisis estático con SonarQube
- Compilar el app

Se usan 3 contenedores para emular las condiciones de la empresa:

- 1 servidor de control de versiones (gitlab, puerto 80)
- 1 servidor de compilacion (jenkins, puerto 8000)
- 1 servidor de analisis estatico (sonarqube, puerto 9000)


*** Pasos ***

1) Ejecute el siguiente comando:

	bash deploy.sh

Espere un buen momento a que cargue todo, alrededor de 5 a 7 minutos (dependiendo
del hardware).

2) Cuando halla cargado, acceda desde el navegador a las siguientes 3 urls, creando
una pestaña para cada url:

- localhost		(gitlab)
- localhost:8000	(jenkins)
- localhost:9000	(sonarqube)

Espere a que todo cargue de nuevo....



3) Muevase desde una consola a la carpeta app/Finanzas que es donde esta el app
de Java. Primero inicialice un repositorio de git (instalelo si no lo tiene) asi:

	git init

4) Añada todos los archivos encontrados alli usando:

	git add --all

5) Haga commit (guarde) todo el codigo usando:

	git commit -m "Mi primer commit"

6) Agregue el servidor de gitlab como servidor remoto (donde se guarda el codigo
a nivel global) usando:

	git remote add origin http://localhost/auditoria2017/finanzas.git/

7) Envie todo el codigo al servidor remoto al branch (path de codigo, por asi decirlo) master
usando: 

	git push origin master

8) Muevase a la pestaña de jenkins (localhost:8000) y mantenga su pc alli. Al pasar un
tiempo debe ver como aparece en la barra lateral izquierda que llego una orden para compilar.
Haga click sobre ella y mire como se ejecuta paso a paso el build.



