# Capitulo 5. Neural Network.
Una de las razones del gran interes por "Neural Networks" es la esperanza de entender nuestra propia mente, que emerge del procesamiento neuronal en nuestro cerebro.

> **Deep learning**. El aprendizaje profundo se refiere a ciertos tipos de técnicas de aprendizaje automático en las que varias "capas" de unidades de procesamiento simples están conectadas en una red para que la entrada al sistema se pase a través de cada una de ellas. Esta arquitectura se a inspirado en el procesamiento de información visual en el cerebro que entra a través de los hojos y es capturada por la retina. Esta profundidad permite a la red aprender estructuras más complejas sin necesidad de cantidades de datos inmensamente grandes.

> **Neuronas, cuerpos celulares y señales**. Una red nueronal, ya sea biológica o artificial, consiste en un gran número de unidades simples, neuronas, que reciben y transmiten señales entre si. Las neuronas son procesadores muy simples de información que consiste en un cuerpo celular y cables que conectan las neuronas entre sí. La mayoría de las veces no hacen más que quedarse "quietas" y observar las señales que ingresan a través de los cables.

> **Dendritas, axones y sinapsis**. En la jerga biológica, llamamos a los cables que proporcionan la entrada a las neuronas, **dendritas**. A veces, dependiendo de las señales entrantes, la neurona puede dispararse y enviar una señal para que las otras neuronas las reciban. El cable que transmite la señal de salida se llama **axon**. Cada axon puede estar conectado a una o más dendritas en intersecciones que se denominan **sinapsis**.

Nos hemos desviado un poco del tema del curso. De hecho, **la razón principal para construir redes neuronales artificiales tiene poco que ver con la comprensión de los sistemas biológicos**. La razón principal es utilizar los sistemas biológicos como **inspiración** para construir mejores técnicas de IA y aprendizaje automático. La idea es muy natural: el cerebro es un sistema de procesamiento de información increíblemente complejo capaz de una amplia gama de comportamientos inteligentes (además de algunos no tan inteligentes), y por lo tanto, tiene sentido buscar inspiración en él cuando tratamos de crear sistemas artificialmente inteligentes.

## 2. How Neural networks are built.
> **Pesos y Entradas**.
El modelo básico de neurona artificial implica un conjunto de parámetros adaptativos, llamados pesos, como en la regresión lineal y logística. Al igual que en la regresión, estos pesos se usan como multiplicadores en las entradas de la neurona, que se suman. La suma de los pesos por las entradas se denomina combinación lineal de las entradas. En el ejemplo de la cesta de la compra: multiplicar la cantidad de cada artículo por su precio unidad y sumar para obtener el total.

### Activaciones y salidas.
Una vez que se ha calculado la combinación lineal, la neurona hace una operación más. Toma la combinación lineal y la coloca a través de una llamada a **función de activación**. Algunos ejemplos típicos de función de activación son:
- Función de Identidad: No hacer nada y simplemente generar la combinación lineal.
- Función de paso: Si el valor de la combinación lineal es mayor que cero, envía un "pulso" (ON), de lo contrario no hacer nada (OFF).
- Función Sigmoid: Version "soft" de la función de paso (step).

La salida de la neurona, determinada por la combinación lineal y la función de activación, se puede utilizar para extraer una predicción o una decisión. Por ejemplo, si la red está diseñada para identificar señales de stop delante de un coche autónomo, la entrada pueden ser los pixeles de una imagen capturada por una cámara conectada delante del coche y la salida se puede utilizar para activar un procedimiento de parada que detiene el coche antes de la señal.

### El Perceptron: La madre de todas las ANN.
El perceptron es simplemente un nombre elegante para el modelo de neurona simple con la función de activación de pasos. Fue uno de los primeros modelos formales de cálculo neural y debido a su papel fundamental en la historia de las redes neuronales, se le puede considerar la madre de todas las ANN.

Se puede utilizar como clasificador simple en tareas de clasificación binaria. Un método para aprender los pesos del perceptrón a partir de datos, llamado algoritmo Perceptron, fue introducido por el psicólogo Frank Rosenblatt en 1957. Baste decir que es tan simple como el clasificador de vecino más cercano. El principio básico es alimentar los datos de entrenamiento de red con un ejemplo a la vez. Cada clasificación errónea conduce a una actualización en el peso.

A continuación hacen referencia al artículo [A Sociological Study of the Official History of the Perceptrons Controversy](http://journals.sagepub.com/doi/10.1177/030631296026003005) donde se cuenta el abandono de la investigación en IA durante más de 20 años desde 1960 a causa de todas las chorradas que se habían dicho sobre "donde ibamos a llegar con la IA". También comenta, sobre el artículo [article in the MIT Technology Review](https://www.technologyreview.com/s/608911/is-ai-riding-a-one-trick-pony/), que volvemos a las andadas de antes de los 60 montandonos películoas sobre la IA.

### Poniendo las neuronas juntas: redes
A menudo, la arquitectura de red se compone de capas. La capa de entrada consiste en neuronas que obtienen sus entradas directamente de los datos. Por ejemplo, en una tarea de reconocimiento de imágenes, la capa de entrada utilizaría los valores de los pixel de la imagen de entrada. La red, normalmente, también tiene capas ocultas que utilizan las salidas de otras neuronas como entrada, y cuya salida se utiliza como entrada de otras capas de neuronas. Por ultimo, la capa de salida produce la salida de toda la red.

### Un clasificador de red neuronal simple.
Ejercicio de caras sonrrientes y caras tristes.

## Advanced neural network techniques
Hay algunas variaciones interesantes y potententes a las ya vistas en cuanto a redes neuronales que han llevado a grandes avances en el aprendizaje profundo en muchas áreas.

### Convolutional neural networks (CNNs)
Un área donde el aprendizaje profundo ha logrado un exito espectacular es en el procesamiento de imágenes. El clasificador simple visto anteriormente está severamente limitado, ya que no se ha dado cuenta que ni siquiera era posible clasificar todas las caras sonrientes correctamente. Añadir más capas en la red y usar la retropropagación para aprender los pesos en principio resuelve el problema, pero surge otra: el número de pesos se vuelve extremadamente grande y, en consecuencia, la cantidad de datos de entrenamiento necesarios para lograr precisión satisfactoria puede llegar a ser demasiado grande para ser realista.

Existe una solución muy elegante al problema de demasiados pesos: un tipo especial de red nueronal o, más bien, un tipo especial de capa que se puede incluir en una red neuronal profunda. Este tipo especial de capa es llamada **[capa convolucional](https://es.wikipedia.org/wiki/Redes_neuronales_convolucionales)**. Las redes que incluyen capas convolucionales se denominan redes neuronales convolucionales (CNN).
Su propiedad clave es que pueden detectar entidades de imagen como manchas brillantes u oscuras (o de color específico), bordes en varias orientaciones, patrones, etc.

> **Por que son necesarias las CNN**
Las CNN utilizan un truco inteligente para reducir la cantidad de datos de entrenamiento necesarios para detectar objetos en diferentes condiciones. El truco básicamente equivale a usar los mismos pesos de entrada para muchas neuronas – por lo que todas estas neuronas se activan por el mismo patrón – pero con diferentes píxeles de entrada. Podemos, por ejemplo, tener un conjunto de neuronas que son activadas por la oreja puntiaguda de un gato. Cuando la entrada es una foto de un gato, se activan dos neuronas, una para la oreja izquierda y otra para la derecha. También podemos permitir que los píxeles de entrada de la neurona sean tomados de un área más pequeña o más grande, de modo que diferentes neuronas sean activadas por la oreja que aparece en diferentes escalas (tamaños), para que podamos detectar las orejas de un gato pequeño incluso si los datos de entrenamiento sólo incluían imágenes de grandes gatos.

### ¿Sueñan las redes neuronales con ovejas eléctricas? Redes adversarias generativas (GANs)
Un resultado fascinante se obtiene tomando las capas inferiores pre-entrenadas y estudiando cómo se ven las características que han aprendido. Esto se puede lograr mediante la generación de imágenes que activan un cierto conjunto de neuronas en las capas inferiores. Mirando las imágenes generadas, podemos ver cómo "piensa" la red nueronal una característica en particular, o cómo se vería una imagen con un conjunto selecto de características en ella. A algunos incluso les gusta hablar de las redes "soñando" o "alucinando" imágenes (ver [Google’s DeepDream system](https://en.wikipedia.org/wiki/DeepDream)).

Para generar gatos de aspecto real, rostros humanos u otros objetos (obtendrás lo que hayas usado como datos de entrenamiento), Ian Goodfellow que actualmente trabaja en Google Brain, propuso una combinación inteligente de dos redes neuronales. La idea es dejar que las dos redes compitan entre sí. Una de las redes está entrenada para generar imágenes como las de los datos de entrenamiento. La tarea de la otra red es separar las imágenes generadas por la primera red de imágenes reales de los datos de entrenamiento – se llama la red adversaria, y todo el sistema se llama red adversaria generativa o un GAN.

El sistema entrena los dos modelos uno al lado del otro. Al principio del entrenamiento, el modelo adversario tiene una tarea fácil de distinguir las imágenes reales de los datos de entrenamiento y los intentos torpes del modelo generativo. Sin embargo, a medida que la red generativa poco a poco mejora y mejora, el modelo contradictorio también tiene que mejorar, y el ciclo continúa hasta que finalmente las imágenes generadas son casi indistinguibles de las reales. El GAN trata de no sólo reproducir las imágenes en los datos de entrenamiento: esa sería una estrategia demasiado simple para vencer a la red adversarial. Más bien, el sistema está entrenado para que tenga que ser capaz de generar nuevas imágenes de aspecto real también.