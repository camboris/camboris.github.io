.. title: Haxe JS | Externs + LowDb
.. slug: haxe-js-externs-+-lowdb
.. date: 2017-03-08 22:27:24 UTC-03:00
.. tags: 
.. category: programación
.. link: 
.. description: 
.. type: text

Estoy probando cosas en Js últimamente y no me gustan mucho babel y parientes. Permiten usar características avanzadas del lenguaje, pero al final del día, sigue siendo Js. :)

Haxe_ nos permite tener un compilador real validando nuestro código, además de sus características específicas como: Macros, enums, tipos de datos abstractos, etc.

Para poder usar Haxe_ con Js y acceder a librerías externas tenemos que usar Externs. Son definiciones de los métodos que proveen estas librerías de terceros en un formato que le permite a Haxe_ validar tipos de datos, estructuras y demases. Para estas pruebas voy a usar Node_, ya que me permite probar de manera rápida y sencilla el código sin tener que armar una página web para ejecutar en el browser.

.. TEASER_END

Me voy a basar en el ejemplo de esta http://matthijskamstra.github.io/haxenode/03lowdb/about.html, pero con algunas adaptaciones.

Para instalar algunas libs necesarias uso Haxelib_, la herramienta de manejo de paquetes de Haxe_.

.. code:: bash

    haxelib install hxnodejs
    haxelib git js-kit https://github.com/clemos/haxe-js-kit.git haxelib

El primer comando instala una librería directamente del repositorio de Haxelib_. El segundo usa el código del repo git, especificando la rama haxelib.

La librería ``hxnodejs`` nos da externs, es decir una interfaz para usar Node_ con Haxe_ mientras que js-kit_ nos brinda muchos otros externs de librerías populares, tanto de Node_ como de Js.

Para estas pruebas elegí LowDb_ porque me pareció interesante y útil el concepto de una bbdd json. En este momento estoy trabajando en un sistema que abusa del xml y me la paso deseando tener algo más flexible y sencillo de usar. Esta lib nos permite guardar tanto en un archivo físico como uno en memoria, en LocalStorage o implementar los métodos de guardado y recuperación, pudiendo implementar otras formas de guardado asíncronas.

Tengo que instalar LowDb_ usando npm, así que inicializo el archivo ``package.json`` y creo la estructura de carpetas necesarias para la demo.

.. code:: bash

    npm init
    npm install lowdb --save
    mkdir src
    mkdir bin

El siguiente paso es crear el archivo ``build.hxml`` que tiene las instrucciones para que Haxe_ compile el proyecto.

.. code:: bash

    -cp src
    -lib js-kit
    -lib hxnodejs
    -main Main
    -js bin/main.js
    -cmd node bin/main.js

Básicamente le digo a Haxe_ que el código está en la carpeta ``src``, que use las libs ``js-kit`` y ``hxnodejs``, que la clase principal es ``Main``, que el archivo de salida es ``bin/main.js`` y por ultimo que ejecute ``node bin/main.js``, o sea, el programa.

En ``src/Main.hx`` pongo:

.. code:: javascript

    package;

    import js.Node;
    import js.npm.LowDb;

    class Main {
        public function new() {
            //initialize variables
            trace('demo lowdb');

            var _lowdb = LowDb.construct("db.json", {async: false});
            _lowdb.defaults({'posts': [], 'user': {}}).write();
            _lowdb.get("posts").push({id: 1, title: "Mario" }).write();

            _lowdb.set('user.name', 'boris').write();

            trace("user name " + _lowdb.get('user.name'));
            trace("has posts " + _lowdb.has("posts").value());
            trace("number of posts " + _lowdb.get('posts').size().value());
            trace("filter posts" + _lowdb.get("posts").filter({id: 1}).take(2).value());
        }

        static function main() {
            var main = new Main();
        }

    }

El código es bastante claro. Empiezo importando las librerías que voy a usar y en el constructor de la clase, inicializo la bbdd. Por cuestiones de como se arman los externs, hay cosas que no se pueden mapear uno a uno con la lib origina, es por eso que la línea ``LowDb.construct(....`` no mapea uno a uno con el constructor en Js.

Con ``defaults`` defino una estructura básica del archivo, y después pusheo un objeto con la estructura del post en el array de posts, y seteo un valor especifico en una estructura de objeto, que sería el user.

Lo más interesante de esta lib, es que esta basada en Lodash_, una lib que brinda todo tipo de funciones helper. El resultado de las consultas a LowDb_ es un ``chain`` de Lodash_, lo que permite manipularlo de manera sencilla. En los trace del ejemplo, hago filtrados, ordenamientos, búsqueda de valores específicos, etc.

Investigando un poco para este post, encontré que hay un port de la lib en Haxe_ puro, lo que simplificaría la integración. Me queda probarlo, así como otros externs de js-kit_


| ♪ *In a steel cage match with a maze of cables*
| ♪ *Brazen, game-face based on Azazel*
| Kirby_ - Aesop Rock

.. _Haxe: http://haxe.org/
.. _Node: https://nodejs.org/en/
.. _Haxelib: http://lib.haxe.org/
.. _js-kit: https://github.com/clemos/haxe-js-kit
.. _LowDb: https://github.com/typicode/lowdb
.. _Lodash: https://lodash.com/
.. _Kirby: https://www.youtube.com/watch?v=7T_KKiQiolk
