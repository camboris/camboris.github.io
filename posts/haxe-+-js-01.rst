.. title: Haxe + JS 01
.. slug: haxe-+-js-01
.. date: 2016-04-02 16:49:50 UTC-03:00
.. tags: haxe, js
.. category: programación
.. link: 
.. description: 
.. type: text

Haxe_ es un lenguaje muy atractivo, por un lado su facilidad para aprenderlo, ya que su sintaxis es muy similar a EcmaScript, y por el otro su capacidad de escribir otros lenguajes. Es tanto un lenguaje como un compilador.

Además de soportar características avanzadas como el soporte para macros, lo que más me gusta es lo simple que hace escribir un gran rango de aplicaciones, desde juegos para la plataforma que queramos, a frontends en js o backends en js o php. 

.. TEASER_END

Suelo usarlo para juegos, con frameworks como Openfl_ o Flixel_ o Luxe_, pero estoy empezando a probarlo con js, ya que tiene un excelente soporte, y es un lenguaje mas completo que Coffescript o Typescript.

Las últimas versiones de Haxe_ ya tiene por defecto habilitado DCE (Dead Code Elimination), lo que hace que el código generado sea en muchos casos mejor que el de otras herramientas.

Ejemplo mínimo de un hola mundo:

.. code:: javascript
    :number-lines:
    :name: HolaMundo.hx

    //HolaMundo.hx
    package;

    class HolaMundo {

        function new() {
            trace("Hola Mundo");
        }

        static public function main() {
            var main = new HolaMundo();
        }
    }

Este es el ejemplo mas sencillo que podemos hacer en Haxe_. La función `main()` es el punto de entrada de la aplicación, la cual crea una nueva instancia de la clase `HolaMundo`, que ejecuta `new` como su constructor.

Para compilar, ejecutamos por linea de comando:

.. code:: bash

    haxe -main HolaMundo -js holamundo.js

Donde ``haxe`` es el ejecutable del compilador, con ``-main HolaMundo`` le decimos cual es la clase que contiene el punto de entrada de la aplicación y ``-js holamundo,js`` cuál es el archivo de salida. Con las dependencias adecuadas instaladas, podríamos decirle que genere ``cpp`` lo que nos daría un ejecutable en la plataforma que estamos, escribiendo por nosotros código C++, o ``php`` o ``python`` o ``java`` o algún otro de los targets del lenguaje.

Si vemos el código js generado, es bastante legible y compacto.

.. code:: javascript

    (function (console) { "use strict";
    var HolaMundo = function() {
        console.log("Hola Mundo");
    };
    HolaMundo.main = function() {
        var main = new HolaMundo();
    };
    HolaMundo.main();
    })(typeof console != "undefined" ? console : {log:function(){}});


Para próximos posts, voy a explicar como usar librerías externas, organizar mejor el código y muchas cosas más que podemos hacer con Haxe_

| ♪ *Soy la estrella del baile*
| ♪ *Me piden que baile y todos miran hacia mi*
| La estrella del baile - Riki Musso

.. _Haxe: http://haxe.org/
.. _Openfl: http://openfl.org/
.. _Flixel: http://haxeflixel.com/
.. _Luxe: http://luxeengine.com/
