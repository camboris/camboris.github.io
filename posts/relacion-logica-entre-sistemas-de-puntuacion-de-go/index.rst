.. title: Relación Lógica entre sistemas de puntuación de Go
.. slug: relacion-logica-entre-sistemas-de-puntuacion-de-go
.. date: 2016-04-17 17:34:11 UTC-03:00
.. tags: juegos, juegos de mesa, go
.. category: 
.. link: 
.. description: 
.. type: text


Hace años que me interesa el juego de mesa Go. Tengo un tablero comprado en la Asociación Argentina de Go hace varios años, el cual tiene más uso como fondo para las fotos de origami que como tablero de juego.

A pesar de que las reglas son sencillas, el tema de la puntuación es más complejo y siempre tuve dudas. Gracias a la publicidad que le dio al juego las partidas entre Deep Mind y Lee Sedol, han salido muchos artículos interesantes al respecto.

Uno que me llamó la atención se encuentra en esta `url <https://gist.github.com/fohristiwhirl/4eac86766f3bb868bec1>`_, y decidí traducirlo para tener una referencia a mano.

.. TEASER_END

La relación lógica entre los sistemas de puntuación de Go.
==========================================================

¿Cuál es el sistema más sencillo de puntuación de Go? Es este:

* **Puntaje por piedras:** tan solo cuenta las piedras en el tablero.

Al final del juego, ambos jugadores querrán llenar su propio territorio los más que puedan, dejando dos ojos por grupo (para no ser capturados). Entonces el ganador es el jugador con más piedras en el tablero. Nota: los prisioneros no se cuentan.

Pero nadie quiere jugar todas esas piedras al final. Entonces podemos usar:

* **Puntuación por área sencilla:** cuenta las piedras en el tablero, más el territorio completamente rodeado.

Ahora, al final del juego, los jugadores necesitan capturar piedras enemigas dentro de su territorio (porque el territorio no está rodeadoá-en un sentido matemático- hasta que haya solo un color presente), pero después de eso, el juego esta listo para ser puntuado. Nota: los prisioneros siguen sin contarse.

En la práctica, los jugadores con un poco de experiencia pueden saber si un grupo está vivo o muerto. Jugar las movidas para capturar piedras muertas es una pérdida de tiempo. Entonces preferimos:

* **Puntuación por área rápida:** los jugadores se ponen de acuerdo en qué grupos están vivos o muertos, los quitan y cuentan como arriba.

Así es como funcionan las reglas modernas Chinas, al menos online (en la vida real, hay un método físico). Nota: los prisioneros todavía no se cuentan. Diría que es el mejor método para los principiantes. Cuando hay dudas si un grupo está vivo o muerto, se puede jugar sin perder nada. Jugar dentro del propio territorio no nos hace perder puntos, **excepto por perder una movida**, pero al final del juego, no existen esas preocupaciones.

De todas maneras, contar piedras es tedioso en la vida real. Lo que nos lleva a:

* **Puntuación por territorio:** igual que arriba, pero contando prisioneros en lugar de piedras.

En un juego normal, ambos jugadores juegan el mismo número de piedras [1]_. Cualquier diferencia en el número de piedras en el tablero es causado por las capturas. Por lo tanto, podemos evitar contar las piedras del tablero y solo contar prisioneros. Así funcionan las reglas modernas japonesas.

El problema con las reglas japonesas es cuando un principiante, inseguro acerca de la vida y la muerte, juega dentro de su territorio (perdiendo un punto) mientras que su oponente pasa (sin perder nada). Por esta razón prefiero las reglas chinas para los principiantes.

Dejando de lado eso, todas las reglas descriptas son más o menos equivalentes matemáticamente [2]_ cuando los jugadores saben lo que hacen.

Notas
-----

.. [1] Negro puede tener una movida más si blanco pasa primero.

.. [2] La puntuación por piedras no cuenta territorio. Cuando llenás tu territorio con piedras, debes dejar dos ojos por grupo. Si tenes más grupos que tu oponente, estas reglas son malas, porque los ojos, que serían contados con otras reglas, no son contados. Incidentalmente, Japón tuvo un sistema por territorio que explícitamente penalizaba cada grupo vivo con un impuesto de 2 puntos ojo, para mantener paridad matemática con la puntuación por piedras.
