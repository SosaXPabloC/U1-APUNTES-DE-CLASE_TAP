# **Unidad I. Interfaz Gráfica de Usuario (GUI)**

La Interfaz Gráfica de Usuario (GUI, por sus siglas en inglés Graphical User Interface) representa el entorno visual que permite la comunicación entre el usuario y el sistema operativo o la aplicación. A diferencia de las Interfaces de Línea de Comandos (CLI), las GUIs se basan en el paradigma WIMP (Windows, Icons, Menus, Pointer), facilitando la interacción mediante representaciones visuales de los datos y las acciones.

![ejemplo](https://iyrix.com/assets/img/Ejemplos%20de%20interfaz%20gr%C3%A1fica%20de%20usuario.png)

## _**1.1 Creación de interfaz gráfica para usuarios**_

La creación de una GUI moderna en la Ingeniería de Software ha transitado de un enfoque puramente "imperativo" (donde se indicaba paso a paso cómo dibujar cada pixel) a un enfoque declarativo. Tecnologías como Flet (que sirve como puente hacia el motor de renderizado de Flutter) permiten a los desarrolladores definir "qué" debe mostrarse en pantalla, mientras el framework se encarga de calcular "cómo" dibujarlo.

_Conceptos clave en la creación de GUIs:_

Paradigma de "UI como Código" (UI as Code): En lugar de usar diseñadores visuales de arrastrar y soltar (como en tecnologías antiguas tipo Windows Forms), la interfaz se construye instanciando objetos directamente en el código base (en nuestro caso, Python). Esto facilita el control de versiones en plataformas como GitHub.

Árbol de Componentes (Widget Tree): La interfaz no es plana, sino jerárquica. Existe un contenedor raíz (generalmente llamado Page o Window) del cual se desprenden nodos hijos. Si se destruye un nodo padre, sus hijos en el árbol de renderizado también son eliminados.

Motor de Renderizado: Es el subsistema encargado de traducir los objetos en memoria a píxeles en la pantalla. En Flet, el servidor interno (Fletd) serializa los objetos de Python y los envía al cliente (navegador web o ventana nativa de escritorio) para ser dibujados a 60 cuadros por segundo.

Diseño Responsivo y Adaptativo: La creación moderna de GUIs exige que las interfaces se adapten dinámicamente al tamaño del Viewport (pantalla del dispositivo), utilizando conceptos como Flexbox para distribuir el espacio disponible de manera proporcional.

## _**1.2 Tipos de eventos**_

En el contexto de las interfaces gráficas, un evento es un mensaje asíncrono o una notificación originada por el hardware, el usuario o el propio sistema operativo, que indica que ha ocurrido una acción específica. El programa debe estar preparado para identificar estos eventos y reaccionar en consecuencia.

_Los eventos se pueden clasificar en las siguientes categorías principales:_

_Eventos de Interacción del Usuario (Hardware Events):_

Eventos de Dispositivo Apuntador (Mouse/Touch): Clic único (on_click), doble clic, mantener presionado, arrastrar y soltar (drag and drop), o el desplazamiento del cursor sobre un elemento (hover).

Eventos de Teclado: Pulsación de una tecla (on_key_down), liberación de la misma (on_key_up), o combinaciones de teclas (atajos/shortcuts).

Eventos de Cambio de Estado (State Events):

Ocurren cuando el valor interno de un componente cambia. Por ejemplo, marcar una casilla de verificación (checkbox), mover un control deslizante (slider), o modificar el texto dentro de un campo de entrada (on_change).

Eventos de Enfoque (Focus Events):

Se disparan cuando un componente gráfico gana o pierde la atención del usuario (el cursor está parpadeando en él). Se conocen como on_focus y on_blur.

Eventos de Ciclo de Vida y Sistema (Lifecycle Events):

Son gestionados por la ventana o la página. Incluyen la inicialización de la interfaz, el redimensionamiento de la ventana (on_resize), el cambio de rutas en la navegación, o la desconexión del cliente con el servidor.

## **1.3 Manejo de eventos**

El Manejo de Eventos (Event Handling) es el pilar de la Programación Orientada a Eventos (Event-Driven Programming). A diferencia de la programación secuencial clásica, donde el programa dicta el flujo de ejecución, en una GUI es el usuario quien determina el orden de ejecución mediante sus acciones.

Para que el manejo de eventos funcione, se implementa un patrón de diseño conocido como Observador (Observer Pattern).

Mecanismo de funcionamiento:

Bucle de Eventos (Event Loop): La aplicación entra en un ciclo infinito de "escucha" en segundo plano, esperando a que el sistema operativo le notifique sobre nuevas acciones.

Manejador de Eventos (Event Handler / Callback): Es una función o método específico desarrollado por el programador. Su única responsabilidad es contener la lógica de negocio que debe ejecutarse cuando ocurra un evento concreto.

Suscripción (Binding): Se debe enlazar explícitamente el componente gráfico, el tipo de evento y la función manejadora. En código, esto significa asignar la función al parámetro del componente (ej. decirle a un botón que, al detectar un clic, ejecute la función guardar_datos).

El Objeto Evento (e): Cuando la función manejadora es llamada, recibe automáticamente un argumento que encapsula toda la información de la acción (qué componente lo disparó, coordenadas del ratón, tecla presionada, etc.).

Sincronización de Estado (Update): Una vez que la función manejadora procesa la lógica, debe instruir al motor gráfico para que actualice la pantalla y refleje los nuevos datos al usuario.

## **1.4 Manejo de componentes gráficos de control**
Los componentes gráficos de control, comúnmente llamados Widgets o Controles, son los elementos de software encapsulados que conforman las piezas de construcción de cualquier GUI. El manejo adecuado de estos componentes implica comprender su taxonomía y sus propiedades físicas y de comportamiento.

_Una interfaz bien diseñada separa los componentes según su responsabilidad:_

_Controles de Contenedor y Diseño (Layout Controls):_

No suelen ser visibles por sí mismos, pero estructuran a los demás.

Ejemplos: Filas (Row), Columnas (Column), Cuadrículas (GridView), y Contenedores (Container). Manejan propiedades geométricas como la alineación, el espaciado interno (padding) y el margen exterior (margin).

Controles de Entrada de Datos (Input Controls):

Permiten la captura de información del usuario.

### Ejemplos:
 Campos de texto (TextField), menús desplegables (Dropdown), botones de opción múltiple (RadioButtons), y selectores de archivos o fechas. Su manejo requiere validar la información que el usuario introduce para evitar errores de ejecución.

_Controles de Acción (Action Controls):_

Son los detonadores de eventos primarios.

### Ejemplos: 
* botones elevados
* botones flotantes (FAB)
* botones de ícono
Su manejo se centra en el ruteo de la lógica del programa.

Controles de Visualización y Retroalimentación (Display & Feedback Controls):

Muestran información estática, dinámica o el estado del sistema.

### Ejemplos: 
Etiquetas de texto (Text), imágenes, barras de progreso (ProgressBar), y alertas emergentes (AlertDialog o SnackBar). Su manejo es vital para confirmar al usuario que sus acciones están siendo procesadas por el sistema.

***


## **Fuentes Consultadas:**


* Flet. (2024). Flet documentation: Build interactive Flutter apps in Python. Recuperado de https://flet.dev/docs/

* GeeksforGeeks. (2023, 23 de mayo). Event-driven programming in software engineering. Recuperado de [https://www.geeksforgeeks.org/event-driven-programming/](https://www.google.com/search?q=https://www.geeksforgeeks.org/event-driven-programming/&authuser=1)

* Python Software Foundation. (2024). Python 3.12 documentation. Recuperado de https://docs.python.org/3/

* Tecnológico Nacional de México. (2010). Programa de la asignatura SCD-1027: Tópicos Avanzados de Programación [Documento en línea]. Plataforma de Educación a Distancia IT Cuautla. Recuperado de los archivos del curso.

* W3C. (2023). UI Events: W3C working draft (Especificaciones técnicas de eventos de interfaz). World Wide Web Consortium. Recuperado de https://www.w3.org/TR/uievents/
