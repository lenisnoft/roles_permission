# LENINSOFT – Roles y Permisos

![lenisnoft](leninsoft.jpg "lenisnoft")

Descripción:

Este repositorio pretende mostrar la puesta en ejecución del repositorio de "savanihd" cuyo ejemplo se muestra en la siguiente ruta:

https://www.itsolutionstuff.com/post/laravel-6-user-roles-and-permissions-from-scratch-laravel-6-aclexample.html 

y se lo puede clonar desde:

git clone https://github.com/savanihd/Laravel-6-ACL.git

pero en ninguno de los dos casos te indican que debes hacer para poder mirar el funcionamiento del sitio en tu maquina local. A continuación muestro los pasos a seguir en Linux (Ubuntu 20.04 LTS, si estan en otra carpeta que no sea la del usuario deberas ejecutar los comandos con "sudo") para que puedas ejecutarlo localmente:

1.- Renombro la carpeta a "rol_permission" solo para distinguir de otros proyectos (no es necesario ejecutar este paso)

mv Laravel-6-ACL/ rol_permission/

2.- Ingreso al proyecto clonado con: cd rol_permission/ 

2.1.- Si no se cambio el nombre debes ingresar con: cd Laravel-6-ACL/

3.- Copio el archivo de variables de entorno de ejemplo a ".env" 

sudo cp .env.example .env

4.- Edito el archivo de variables y coloco las credenciales para acceder a la Base de Datos local

nano .env

5.- Ejecuto la actualizacion del composer que ya viene por defecto desde el repositorio

composer update

6.- Genero las nuevas claves para el sitio

sudo php artisan key:generate

7.- Publico el paquete Spatie (si no estuviera ya en el composer.json podríamos ejecutarlo como "composer require spatie/laravel-permission"), este paquete nos permite controlar los roles y permisos de los usuarios. Si deseas mas referencia acerca de este paquete te dejo el link: https://spatie.be/docs/laravel-permission/v3/installation-laravel

php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"

8- Migro las configuraciones que ya viene en el sitio para que se creen las distintas tablas a usar

php artisan migrate

9.- Genero los datos ejemplo para permisos

php artisan db:seed --class=PermissionTableSeeder

10.- Genero el usuario que me permite ingresar al sitio (admin@gmail.com con clave 123456)

php artisan db:seed --class=CreateAdminUserSeeder

11.- Levanto al server local por defecto (si se tiene mas sitios ejecutando debes ejecutarlo con el parámetro --port=XXX, donde XXX es el numero de puerto que quieras usar en tu maquina, por ejemplo: 8001)

php artisan serve

12.- Solo resta poner la dirección de tu servidor local en el navegador y podrás mirar como funciona el ejemplo

http://127.0.0.1:8000


The Laravel framework is open-sourced software licensed under the MIT license.
