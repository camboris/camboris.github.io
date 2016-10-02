.. title: Desembalando la Raspi
.. slug: desembalando-la-raspi
.. date: 2016-09-28 16:40:00 UTC-03:00
.. tags: hardware
.. category: hardware
.. link: 
.. description: 
.. type: text

Por fin llegó. Tampoco la esperamos tanto, pero la ansiedad puede con nosotros. Y digo nosotros, porque fue una cuestión familiar, ya que el destino inicial es servir como centro multimedia para el tele.

Ya habíamos estado experimentando con Kodi_ usando mi notebook, pero no era lo más cómodo, así que pedimos una Raspberry 3 con un kit, que traía todo lo necesario.

Justo llegó el sábado del Pyday_, por lo que tuvimos que esperar un par de días más para probarla.

Antes de abrir el paquete cual cavernícolas desenfrenados, le pedí a Dori que hiciera unas fotos con el celular.


.. figure:: /galleries/UnboxRaspi/raspi-0.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-0.jpg
    :align: center
    
    Caja cerrada.

.. figure:: /galleries/UnboxRaspi/raspi-1.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-1.jpg
    :align: center
    
    Todo acomodado y muy prolijo.


.. figure:: /galleries/UnboxRaspi/raspi-2.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-2.jpg
    :align: center
    
    Desembalando...


.. figure:: /galleries/UnboxRaspi/raspi-3.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-3.jpg
    :align: center
    
    Empezamos a sacar las cosas...


.. figure:: /galleries/UnboxRaspi/raspi-4.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-4.jpg
    :align: center
    
    Raspi, caja, fuente, cable hdmi, memoria.

.. figure:: /galleries/UnboxRaspi/raspi-5.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-5.jpg
    :align: center
    
    Detalle Raspberry.

.. figure:: /galleries/UnboxRaspi/raspi-6.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-6.jpg
    :align: center
    
    Disipadores.

.. figure:: /galleries/UnboxRaspi/raspi-7.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-7.jpg
    :align: center
    
    Caja.

.. figure:: /galleries/UnboxRaspi/raspi-8.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-8.jpg
    :align: center
    
    Otro beauty shot de la caja y la raspi

.. figure:: /galleries/UnboxRaspi/raspi-9.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-9.jpg
    :align: center
    
    Instalando los disipadores.

Los disipadores ya venían con la cinta térmica. Los instalamos en segundos.
    
.. figure:: /galleries/UnboxRaspi/raspi-10.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-10.jpg
    :align: center
    
    Detalle de la instalación.

.. figure:: /galleries/UnboxRaspi/raspi-11.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-11.jpg
    :align: center
    
    Instalando la caja.

Un detalle interesante es que la caja es alta y tiene lugar para poner accesorios, ya que deja libre los conectores. 


.. figure:: /galleries/UnboxRaspi/raspi-12.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-12.jpg
    :align: center
    
    Instalando el software.

La tarjeta de memoria viene preinstalada con Noobs_, un software que nos permite elegir el sistema operativo a instalar de manera sencilla.

Como su destino inicial (hasta que empiece a comprar accesorios) es ser un centro multimedia, elegí LibreELEC_, por lo que en minutos tuve Kodi_ andando.


.. figure:: /galleries/UnboxRaspi/raspi-13.jpg
    :width: 500
    :target: /galleries/UnboxRaspi/raspi-13.jpg
    :align: center
    
    Kodi funcionando.

Hasta ahora la experiencia viene siendo extremadamente buena. El software anda muy bien y rápidamente pude configurar el televisor para usar el control remoto para manejar Kodi_. Esto es posible gracias a que el cable provisto en el kit, soporta la tecnología CEC_, Consumer Electronics Control y el televisor llama SimpLink. Distintas marcas tienen distintos nombres para esto. Con tan solo esperar unos segundos para que se conecte, tengo control casi absoluto usando el remoto del tele, muchas veces sin necesidad de tocar el mouse o teclado inalámbrico que le puse. Por supuesto que escribir en el teclado virtual es horrible, pero me hace acordar a los viejos fichines, así que Nostalgia 1, Comodidad 0.

Un detalle curioso -al menos para mí que el hardware no es mi fuerte- es la falta de un botón para prender el dispositivo. La raspberry arranca al enchufarla, y si la apagamos por software, la forma de prenderla es desenchufando y volviendo a enchufar. Me niego a creer que no hay una solución mejor, así que estoy investigando. Cuando encuentre una forma más elegante de hacerlo, voy a actualizar el post.

LibreELEC_ viene con Samba preconfigurado, así que es sencillo copiar archivos por la red a la SD del equipo, o que Kodi_ lea cosas compartidas en los equipos de la casa. Tengo que cambiar el router por uno más potente, pero eso no es culpa del equipo.


.. _`Kodi`: https://kodi.tv/
.. _`Pyday`: http://rafaela2016.pyday.com.ar/
.. _`Noobs`: https://www.raspberrypi.org/downloads/
.. _`LibreELEC`: https://libreelec.tv/
.. _`CEC`: https://en.wikipedia.org/wiki/Consumer_Electronics_Control
