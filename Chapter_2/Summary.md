
# Chapter II: AI problem solving

## 1.- Search and problem solving

Muchos problemas se pueden plantear como una búsqueda, en la que decidir entre varias alternativas evaluando sus requisitos y consecuencias.

Para evaluar las consecuencias de cada alternativa, podemos asignar un coste a cada avance en un camino concreto. Este coste puede ser:
  - Tiempo
  - Esfuerzo
  - Coste definido por una función propia

En vez de centrarse en los algoritmos de búsqueda en sí, este módulo se centra en la primera tarea a la hora de definir la solución a un problema: definir las opciones y sus consecuencias, así como el objetivo final (cuando consideramos que el problema está resuelto). Una vez hecho esto, podemos comenzar la búsqueda del camino que nos lleve del estado inicial al final.

En este capítulo, se diferencian dos tipos de problema:
  - Escenarios estáticos con un solo agente
  - Escenarios competitivos entre dos agentes (1vs1)

En el primer módulo, nos presentan dos variantes del clásico *[problema del barquero](https://es.wikipedia.org/wiki/Acertijo_del_lobo,_la_cabra_y_la_col)*. Para ello, el módulo toma el siguiente acercamiento al problema:
  - Simplificar cada una de las *fases* del problema en estados
  - Señalar cada estado asignando la posición (F|N) de cada actor involucrado
  - Mostrar las conexiones entre estados (a través del viaje de la barca)
  - Seleccionar un camino entre los posibles para llegar del estado inicial al estado final.

No obstante, en la explicación del proceso, se obvia señalar las limitaciones con las que cuenta el problema (reglas del juego), en la que ciertos actores no pueden quedarse solos en la misma orilla. Lo que en este problema es algo trivial de solucionar, en problemas más complejos introduce nuevas variables a tener en cuenta.

Conceptos clave de este módulo:
  - **Espacio de estados**
  - **Transiciones**
  - **Costes**

Finalmente, se extrapola este desarrollo en otro conocido problema clásico de lógica: [Las torres de Hanoi](https://es.wikipedia.org/wiki/Torres_de_Han%C3%B3i)

## 2.- Solving problems with AI

Este módulo comienza con una introducción a la figura de [Alan Turing](https://es.wikipedia.org/wiki/Alan_Turing) como uno de los padres de la computación, mediante su aportación de la [máquina de Turing](https://es.wikipedia.org/wiki/M%C3%A1quina_de_Turing) (un dispositivo abstracto que puede ser configurado|programado para resolver diversos problemas).

También se recuerda a [John McCarthy](https://es.wikipedia.org/wiki/John_McCarthy) (quién acuñó el término *Inteligencia Artificial*) en la célebre [conferencia de Dartmouth](https://es.wikipedia.org/wiki/Conferencia_de_Dartmouth). Este encuentro se llevó a cabo durante 6-8 semanas en el verano de 1956, y sentó las bases del campo de la **IA**, gracias a las aportaciones de los participantes. Los organizadores fueron:
  - El propio **John McCarthy**
  - **[Marvin Minsky](https://es.wikipedia.org/wiki/Marvin_Minsky)** (padre de la IA)
  - **[Claude E. Shannon](https://es.wikipedia.org/wiki/Claude_Elwood_Shannon)** (padre de la *[teoría de la información](https://es.wikipedia.org/wiki/Teor%C3%ADa_de_la_informaci%C3%B3n)*)

La premisa del propio McCarthy con respecto a la conferencia era:
`El objeto de estudio es profundizar en la conjetura de que cualquier aspecto del aprendizaje u otra característica de la inteligencia puede, en principio, ser descrito de forma tan precisa que una máquina puede diseñarse para su simulación.`

A continuación, se explica que los primeros problemas en ser abordados por el campo de la **IA** fueron los juegos, especialmente aquellos "fáciles de plantear" al tener:
  - Un número limitado de agentes (1 o 2)
  - Un número finito (y abarcable) de estados posibles
  - Unas funciones objetivo muy claras para determinar si se gana o se pierde (o se empata)
  - Un conocimiento pleno en todo momento del estado de la partida

## 3.- Search and games

El tercer módulo explora los juegos previamente descritos. Para la explicación, utiliza el [tres en raya](https://es.wikipedia.org/wiki/Tres_en_l%C3%ADnea), un juego tradicional para enseñar los conceptos de *teoría de juegos*, y el papel de los *árboles de juego* en *IA*.

Para ello, se plantea un estado en el que uno de los dos jugadores acaba de situar su pieza. A partir de ese estado, el otro jugador puede seleccionar cualquier espacio libre para colocar su figura, lo cual realizará teniendo en cuenta que:
  - Su objetivo es ganar el juego, por lo tanto se beneficiará de colocar la pieza en aquel hueco que le lleve más rápido a un estado de victoria
  - Al ser un [juego de suma cero](https://es.wikipedia.org/wiki/Juego_de_suma_cero), su beneficio es directamente proporcional a la pérdida del oponente, y viceversa.
  - En los nodos finales de cada rama del árbol, el jugador que ha colocado la pieza en ese nivel puede otorgar un valor absoluto al estado (1 si gana, -1 si pierde, 0 si empata).
  - Cuando dos nodos finales del mismo nivel comparten valor, el nodo *padre* puede verse representado con ese valor, ya que invariablemente de la decisión del contrincante, ese estado llevará a una misma situación final de partida.

Para resolver este tipo de problemas, se desarrolló el [algoritmo minimax](https://es.wikipedia.org/wiki/Minimax), un algoritmo recursivo para *minimizar la pérdida máxima esperada en juegos con adversario y con información perfecta*. En resumen, podría decirse que cada decisión se toma eligiendo el mejor movimiento para mí, ya que mi adversario elegirá el peor para mí.

A pesar de que existen evidencias de que [Charles Babbage](https://es.wikipedia.org/wiki/Charles_Babbage) pudo haber trabajado en una idea similar, la idea de *minimax* se le atribuye a [John von Neumann](https://es.wikipedia.org/wiki/John_von_Neumann) en su artículo de 1928 *Zur Theorie der Gessellschaftsspiele* (*Sobre la teoría de los juegos de sociedad*).

No obstante, *Minimax* solo es adecuado para ciertos tipos de problemas, mientras que en otros casos se nos queda obsoleto:
  - Juegos con árboles muy densos y profundos (*ajedrez*, *go*)
  - Juegos con información oculta (*piedra-papel-tijeras*)
  - Juegos no deterministas (*Monopoly*, *backgammon*)

Para solventar estas limitaciones, se introduce el concepto de **función de evaluación heurística**, mediante la cual trataremos de evaluar el valor de un estado sin necesidad de computar el total de todos los estados del árbol, reduciendo considerablemente los tiempos de procesamiento. De encontrar una buena aproximación a esta función dependerá el desempeño de nuestros algoritmos en el futuro.
