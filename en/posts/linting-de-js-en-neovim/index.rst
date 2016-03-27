.. title: Linting de js en Neovim
.. slug: linting-de-js-en-neovim
.. date: 2016-03-24 12:04:51 UTC-03:00
.. tags: neovim, js
.. category: programación
.. link: 
.. description: 
.. type: text

Reescribiendo mi configuración de Neovim_, porque eso hago los fines de semana largos, reemplacé YouCompleteMe_ con Deoplete_ y Syntastic_ por Neomake_, me encuentro haciendo algunas cosas en js y no tengo linting habilitado.

Ternjs es una posiblidad, pero siempre encuentro que configurarlo es tedioso para cosas chicas, así que busqué otras opciones.

Neomake soporta varios compiladores o linters de js para informar los errores, lo que llaman "Makers".

.. TEASER_END

Configuré jscs_, porque sí. La verdad es que no hice una búsqueda demasiado exhaustiva, sino que me quedé con el primero que funcionó. Lo instalé global con npm, porque hoy quién se puede escapar de node y npm...

.. code:: sh

    npm install -g jscs


Una vez instalado jscs, podemos generar un archivo de configuración automáticamente que nos pregunta el estilo de programación que usamos, corriendo este comando en la carpeta del proyecto.

.. code:: sh

    jscs --auto-configure ./ 

Yo elegí "idiomatic" porque sí. Tengo que buscar un estilo que me guste y ese me pareció interesante para empezar a probar.

Tenemos que asegurarnos que Neomake corra cuando guardamos el archivo, así que tenemos que tener esto en nuestro ``init.vim``

.. code:: sh
    
    autocmd! BufWritePost * Neomake

Con esto ya es suficiente para que nos marque los errores al grabar el archivo, pero siempre se puede configurar un poco más :)

Como estoy probando React y cada framework está obligado a reinventar la rueda, tienen algo llamado JSX, que es js con la posibilidad de escribir html o xml directamente, además de usar ES6 y compilar con Babel y todas esas transformaciones que tanto gustan...

Necesitamos pasarle a ``jscs`` parámetros para indicarle que usamos estas cosas y no proteste. Para eso, redefinimos el *maker* de ``neomake`` de la siguiente manera en nuestro init.vim

.. code::

    let g:neomake_javascript_jscs_maker = {
        \ 'exe': 'jscs',
        \ 'args': ['--no-color', '--preset', 'airbnb', '--reporter', 'inline', '--esnext'],
        \ 'errorformat': '%f: line %l\, col %c\, %m',
        \ }
    let g:neomake_javascript_enabled_makers = ['jscs']


Y si todo sale bien, ahora tenemos linting de js en Neovim de manera asíncrona.



| ♪ *the sheriff after me*
| ♪ *for what I did to his daughter*


.. _Neovim: http://neovim.org/
.. _YouCompleteMe: https://github.com/Valloric/YouCompleteMe
.. _Deoplete: https://github.com/Shougo/deoplete.nvim
.. _Syntastic: https://github.com/scrooloose/syntastic
.. _Neomake: https://github.com/benekastah/neomake
.. _jscs: http://jscs.info/
