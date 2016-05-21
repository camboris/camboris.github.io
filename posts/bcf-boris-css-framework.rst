.. title: BCF - Boris CSS Framework
.. slug: bcf-boris-css-framework
.. date: 2016-05-21 10:00:27 UTC-03:00
.. tags: css, html
.. category: programación
.. link: 
.. description: 
.. type: text

Hace poco estaba armando un pequeño sitio de prueba y me encontré con que iba a necesitar un sistema de grillas. Viendo un poco la oferta de frameworks y sistemas de grillas para CSS, llegué a la conclusión que al mundo le faltaba un framework más. Y le puse mi nombre, no podía ser de otra manera...

Así nació, el `Boris CSS Framework`_, aunque debo admitir que acepto sugerencias para el nombre, siempre que incluyan el Boris :)

En realidad, de original tiene poco, y de framework menos, ya que es un rejunte de distintas cosas que fui encontrando y adaptando a mis necesidades. Lo que hice fue juntarlos, para encontrarlos fácilmente y no renegar buscando. No es un framework en el sentido que la idea es bajarlo y modificarlo a gusto.

Lo primero que necesitamos al encarar un sitio, pequeño o grande, es un reset. Cada navegador le da propiedades diferentes a los componentes básicos, así que la idea es poner una serie de reglas básicas que nos permita asegurarnos que las cosas se van a ver más o menos parecidas en todos los navegadores.

Una aclaración, no tengo interés alguno en soportar la versión que sea de IE, si anda, genial, sino, lo siento, siempre pueden agregar la funcionalidad que necesiten.

El que puse es un mix de distintos resets que fui encontrando en la web y que necesité en el proyecto que dio origen al `BCF`_.

Como característica final, -dije que era un framework sencillo-, tenemos una grilla, robada y modificada. La grilla original es `Dead Simple Grid`_.

El principal cambio que le hice a la grilla, fue hacerla depender de una clase ``container`` al estilo bootstrap, para que la estructura quede  ``.container > .row > .col``

Al encararlo de esta manera nos permite definir libremente el tamaño del ``container`` y las ``col``, dándonos flexibilidad absoluta para resolver los problemas que nos proponen algunos diseñadores cuando se les ocurre poner 5 columnas en el diseño.

.. code::

    //css
    .container {
        width: 100%
    }

    .col.-demo {
        width: 20%;
    }


    //html
    <div class="container">
        <div class="row">
            <div class="col -demo"></div>
            <div class="col -demo"></div>
            <div class="col -demo"></div>
            <div class="col -demo"></div>
            <div class="col -demo"></div>
        </div>
    </div>

Si a alguien le suena raro que la clase sea ``-demo`` se debe a que estoy tratando de seguir los consejos de este sistema `Reasonable System for CSS Stylesheet Structure`_. Estoy probando y adaptándolo a mi gusto.

Una de las ventajas de encarar la grilla de esta manera, es que podemos redefinir arbitrariamente el ancho de las columnas dentro de los media queries, ajustándolo a las necesidades particulares del sitio.

Para ir cerrando esta breve presentación del aún más breve `BCF`_, ¿por qué no usé flex? Porque todavía no está tan difundido y sigue teniendo un aura de magia negra. La idea es implementarlo a futuro porque nos trae beneficios adicionales, como columnas del mismo alto, algo que a los diseñadores les encanta y a que los desarrolladores nos complica la vida.

Si alguno lo prueba, lo usa o lo rompe, me avisa.

.. _`Boris CSS Framework`: https://github.com/camboris/bcf
.. _`BCF`: https://github.com/camboris/bcf
.. _`Dead Simple Grid`: https://github.com/mourner/dead-simple-grid
.. _`Reasonable System for CSS Stylesheet Structure`: https://github.com/rstacruz/rscss
