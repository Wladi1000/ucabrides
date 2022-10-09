
# UCAB RIDES - API🚗
  _aplicacion web, basada en un sistema de "colas" para la poblacion ucabista, ubicada en Venezuela, Proyecto de Formulas Innovadoras_
## Construido con 🛠️
  **Backend**
* [PHP 8.0](https://www.php.net/downloads.php)
* [Laravel 9.5.1](https://laravel.com/docs/9.x)


## Comenzando 🚀

  
_Estas instrucciones te permitirán obtener una copia del proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas._

  

### Pre-requisitos 📋

  

_Que cosas necesitas para instalar el software y como instalarlas (backend)_ 

* [PHP 8.x.x](https://www.php.net/downloads.php) - lenguaje de programacion

* [Apache2](https://httpd.apache.org/download.cgi) - HTTP servidor web
* [Mongodb](https://www.mongodb.com/) - Base de Datos

_Es posible/recomendado instalar un paquete como "[XAMPP](https://www.apachefriends.org/es/index.html)" que ya incluye ambos elementos, Necesario PHP 8.^ y Apache 2.^_

  

* [Composer](https://getcomposer.org/) - Manejador de dependencias

* [Laravel 9.x](https://laravel.com/docs/9.x) - Framework web utilizado

  
### Preparacion del a Base de Datos (back) 🔧
1. Ir a la carpeta del [Drive](https://drive.google.com/drive/folders/1J8FqD1h-fkRdf3w8orDQRqO6pWsz0vmx?usp=sharing) y copiar los archivos de "**php_mongodb.dll**" y "**php_mongodb.pdb**", 
2. Pegarlos los archivos en la ruta de xampp: C:\xampp\php\ext
3. Ir al **php_ini** de xampp que se encuentra en la ruta C:\xampp\php y agregar la extension **extension=php_mongodb.dll**
4. Reiniciar xampp.
### Instalación de la API (back) 🔧

  _Una serie de ejemplos paso a paso que te dice lo que debes ejecutar para tener un entorno de desarrollo ejecutándose_

Una vez teniendo instalado XAMPP.

  1. Clonamos el repositorio en la carpeta "C:\xampp\htdocs"
2. Preparamos el archivo .env con nuestras credenciales, codigos smtp, etc
3. Creamos la base de datos en nuestro gestor de BDD de preferencia
4. El archivo .**env.example** lo modificamos a **.env** y  configuramos la variables de entorno de conexión a la base de datos
```
DB_URI= # AÑADE LA URI DE TU CONEXION 
```
6. Ejecutamos los siguientes comandos

```bash
composer install
php artisan storage:link
php artisan key:generate
php artisan migrate:fresh --seed
php artisan jwt:generate
```
Y levantamos el servidor de **laravel**
```bash
php artisan serve
```
_Recomendamos crear un dominio local para el proyecto [Tutorial:Como crear un dominio local](https://www.youtube.com/watch?v=HzygRlPmYQc)_

  ### Otras Bases de Datos (back) 🔧
_En caso de que quieras usar otro entorno de base de datos, en el archivo **.env** des comenta las siguientes variables de entorno_
```
#DB_CONNECTION=mysql
#DB_HOST=127.0.0.1
#DB_PORT=3306
#DB_DATABASE=
#DB_USERNAME=root
#DB_PASSWORD=
```
Luego ve al archivo **config/database.php** y cambia la conexion a mysql o el gestor de tu preferencia en la linea 19
```
'default' => env('DB_CONNECTION', 'mysql'),
```
Por ultimo, ve al **app/Models/User** y descomenta el Illiminate Autenticable
```
use Illuminate\Foundation\Auth\User  as Authenticatable;
```
luego cambia el extends por **Authenticatable** y remueve el implements **AuthenticatableContract**
```
class  User  extends  Authenticatable  implements  JWTSubject
{
}
```
Como ultimo paso comenta los protected de mongodb
```
protected  $connection = 'mongodb';
protected  $collection = 'users';
```
Ahora solo debes de volver a ejecutar las migraciones
```
php artisan migrate:fresh
```
## Autores ✒️

 Por definir
  

## Objetivo del proyecto 📄

Este es un proyecto realizado sin fines de lucro para la comunidad Ucabista