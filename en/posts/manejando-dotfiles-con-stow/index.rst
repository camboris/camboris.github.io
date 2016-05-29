.. title: Manejando dotfiles con Stow
.. slug: manejando-dotfiles-con-stow
.. date: 2016-05-28 21:58:25 UTC-03:00
.. tags: 
.. category: linux
.. link: 
.. description: 
.. type: text

Después de pasar buena parte del día instalando dependencias para probar React Native y que no ande, decidí poner un poco de orden a mis dotfiles.

Como cualquier linuxero que haya modificado en algo la configuración por defecto de cualquier programa sabe, los archivos dotfiles - llamados así porque empiezan con `.` para ocultarlos - se empiezan a acumular. Cuanto más se personalizan, con más razón uno quiere guardarlos.

.. TEASER_END

La primer reacción es ir guardando una copia, en un servicio como ``Dropbox`` o ``Drive``, pero se vuelve algo tedioso.

El segundo paso, es guardarlos en una carpeta, linkearlos a su destino original y versionar esa carpeta. Esto funciona bastante bien, pero termina siendo algo incomodo.

Esta es la solución que venía usando, con un repo git privado en bitbucket, pero era un lío, distintas versiones de los archivos, con distintos nombres y distintas estrategias de guardado lo convirtieron en algo complicado de mantener y de a poco se estaba poniendo obsoleto, porque no hacía el mantenimiento adecuado.

Investigando un poco, me encontré con `Stow`_, una herramienta que se encarga de gestionar los symlinks, ahorrándonos trabajo.


La idea es guardar los archivos en carpetas, simulando dentro de estas carpetas, la estructura que deberían tener, y Stow_ se ocupa de crear los links necesrios.

Supongamos que en nuestra carpeta ``home``, creamos una llamada ``dotfiles``, dentro de esta 
podemos agrupar nuestros archivos de la manera que consideremos necesaria, entonces podemos tener una carpeta para ``nvim`` otra para ``i3`` otra para ``git``, etc. 
Dentro de la carpeta de ``git`` tendríamos nuestro archivo de configuración en ``.config\git\config``.

.. code::
    
    dotfiles
     ├- git
     |    └─ .config
     |          └─ git
     |                └─ config
     ├- nvim
     |     └─ .config
     |          └─ nvim
     |                └─ init.vim

Una vez creada esta estructura, dentro de ``dotfiles`` ejecutamos ``stow git`` y ``stow`` nos creará los ``symlinks`` en la carpeta padre. Una cosa a tener en cuenta es que ``stow`` solo creará el ``symlink`` si el archivo no existe o es un link, de esta manera no nos borrará nada importante.

Una manera sencilla de visualizar esto es viendo mi repo público de dotfiles_ en github, en caso de agregar archivos o querer replicar mi setup en otro equipo, solo tengo que clonar el repo y correr ``stow X``, ``stow git``, etc, para recuperar mi config.

Otra cosa que hice fue mudar todos los archivos que pude de mi carpeta de usuario a su correspondiente carpeta ``XDG``, o sea, dentro de ``~/.config``.

| ♪ *Ofelia, en el medio de su entierro*
| ♪ *ha causado gran revuelo al salir de su ataúd*

Solletico - Ofelia_


.. _`Stow`: https://www.gnu.org/software/stow/stow.html
.. _dotfiles: https://github.com/camboris/dotfiles
.. _Ofelia: https://www.youtube.com/watch?v=NGwuoJNjYwQ
