<img src="media/icon.png" alt="" width="96" align="right">

# Tools4i

[English](README.md) · **Español**

Herramientas de desarrollo para IBM i en Visual Studio Code, construidas sobre
[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi).

Tools4i añade herramientas para las tareas que van surgiendo durante el día:
encontrar objetos y fuentes, buscar dentro del código, mirar los datos, modelar y
documentar la base de datos, administrar trabajos y archivos en spool, editar
objetos de IBM i, y analizar a qué puede afectar un cambio. Todo desde el editor,
y contra el servidor.

**Instalación:**
[VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i)
·
[Open VSX](https://open-vsx.org/extension/tools4i/tools4i)
(que es además la vía por la que llega a IBM Bob, la compilación de VS Code de IBM)

> **Sobre este repositorio.** Esta es la casa pública de la documentación de
> Tools4i: qué hace la extensión, cómo se instala, qué cambió en cada versión y
> dónde reportar un problema. El código fuente de la extensión no se publica aquí.
> Los reportes de fallos y las ideas son bienvenidos en
> [Issues](https://github.com/Juan-Concepcion/tools4i-docs/issues).
>
> La interfaz de las herramientas está en inglés, por lo que los nombres de
> herramientas, pestañas y botones aparecen en inglés también en este documento.

## Requisitos

- **Visual Studio Code 1.118 o posterior**, o un IBM Bob construido sobre esa
  versión o una más reciente. La línea Bob 2.1 lo está.
- **[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)**,
  que se instala automáticamente como dependencia obligatoria.
- **Una conexión activa** a su IBM i. Tools4i trabaja a través de la conexión que
  ya tiene Code for IBM i; nunca abre una propia.

Las instrucciones completas, incluido el caso sin conexión a internet y cómo
actualizar o desinstalar, están en [INSTALLATION.md](INSTALLATION.md).

## Primeros pasos

1. Instale **Code for IBM i** (llega solo como dependencia) y conéctese a su
   sistema.
2. Abra la vista **Tools4i** desde la barra de actividad, o ejecute cualquier
   comando desde la paleta (**F1** y escriba el nombre de la herramienta).

## Funciones

Todas las herramientas se abren desde la vista **Tools4i** de la barra de
actividad, o desde la paleta de comandos escribiendo su nombre. Los títulos
coinciden con los grupos de esa vista. Pulsando la estrella de una herramienta se
fija en una sección **Favorites** al principio de la vista, sin dejar de aparecer
también en su grupo.

La mayoría de los paneles de resultados comparten las mismas costumbres: filtros
rápidos por columna, columnas ordenables, exportación a CSV y, en las herramientas
de análisis e inspección, guardar lo que hay en pantalla como una instantánea que
se puede volver a abrir después, en otra máquina o sin conexión alguna.

### Navegación

- **Navigate Server**: recorrer bibliotecas, objetos y miembros fuente. Filtros por
  nombre, tipo, atributo, descripción y fecha de creación o modificación, con
  columnas ordenables y redimensionables, filtros rápidos y exportación a CSV.
  Cambiar una descripción o un tipo de fuente, renombrar, copiar o eliminar, bajar
  de una biblioteca a sus objetos o a sus fuentes, y **crear un fuente nuevo** desde
  la barra o desde el menú de una fila, con la biblioteca y el archivo fuente ya
  puestos según dónde se esté. Desde aquí también se pueden **descargar fuentes a un
  proyecto local**, ya sea un miembro, un archivo fuente o una biblioteca entera,
  eligiendo cómo se organizan las carpetas, junto con los metadatos que permiten
  devolverlos después. Con los fuentes en una carpeta quedan al alcance de lo que su
  equipo use fuera del servidor: control de versiones, análisis de código asistido
  por inteligencia artificial, o cualquier otro producto que espere archivos y no
  miembros de una biblioteca.
- **Navigate Local**: el mismo navegador, con sus filtros, columnas ordenables y
  redimensionables, filtros rápidos, selección de filas con Ctrl y Mayúsculas, y las
  acciones de cada fila, aplicado a una carpeta de proyecto local en lugar del
  servidor. Seleccione varias filas para subirlas o borrarlas de una vez, edite el
  nombre, el tipo de fuente o la descripción directamente en la tabla, y cree ahí
  mismo un fuente nuevo. Y los fuentes no tienen que volver a mano para compilarse:
  **Run Action on Server** deja el fuente local en la biblioteca que nombra el
  proyecto y ejecuta contra él su propia Action de Code for IBM i, ya sea en el
  archivo fuente real o en uno temporal que se limpia después, según lo que se
  configure. Los errores de compilación aparecen en el panel **Problems** sobre el
  archivo local, de modo que el ciclo de editar, compilar y corregir se queda donde
  se está editando.
- **Project Properties**: las bibliotecas a las que pertenece un trabajo, guardadas
  con el trabajo mismo. La biblioteca que sus fuentes reflejan, la biblioteca donde
  escribe una compilación y la lista de bibliotecas que esa compilación necesita. Un
  proyecto local las guarda en la carpeta, y una biblioteca del servidor las guarda
  en la propia biblioteca, de modo que las recoge todo el equipo. **Apply** las pone
  en la conexión y **Load** trae lo que la conexión está usando, así una lista armada
  a mano se conserva en vez de volver a escribirse. Una biblioteca puede nombrarse
  por desarrollador, con lo que un mismo proyecto compartido le sirve a cada uno.
  **Project Commands** guarda la lista que prepara un proyecto: ejecutarlos todos,
  retomar donde se detuvo la última ejecución y ver qué respondió cada uno.

### Búsqueda

- **Scan Server Sources**: búsqueda de contenido en los miembros fuente de varias
  bibliotecas a la vez, con listas de objetivos y de omisiones (se admiten
  comodines), un rango de columnas para que los comentarios del formato fijo no
  ahoguen el resultado, y modos de coincidencia. Los términos de búsqueda se añaden
  de uno en uno y se listan como etiquetas que se pueden quitar, cada una como
  **Matches** o **Does NOT match**, de modo que una búsqueda de varios términos se
  lee como una lista de decisiones y no como un muro de controles.
- **Dos maneras de buscar en el servidor**, elegidas desde la rueda dentada junto a
  las opciones o fijadas como predeterminada. **Unix Search** lee los miembros y
  ofrece todo lo anterior, y **IBM i Native Search** hace que el servidor busque en
  su propio fuente, varias veces más rápido sobre una biblioteca grande, para un
  solo término de texto sencillo. El panel ofrece únicamente lo que la manera
  elegida admite, así que la búsqueda se ejecuta siempre como se lee en pantalla.
- **Scan Local Sources**: la misma búsqueda sobre una carpeta de proyecto local.
- **Sources Scan Results**: el resultado de cada búsqueda en su propia pestaña, con
  los miembros a un lado y las sentencias que coinciden al otro. Ordenar las
  bibliotecas por prioridad y resaltar las copias de menor prioridad que una regla
  de primera coincidencia descartaría, filtrar por columna y exportar. Con el clic
  derecho sobre una pestaña se pueden **recuperar los criterios que la produjeron**
  en Scan Server o Scan Local Sources, o copiarlos como texto. Y la opción que más
  tiempo ahorra en una base de código antigua: **ocultar las coincidencias que caen
  sobre código comentado**, para que buscar un campo deje de devolver los veinte
  sitios donde se comentó hace años.

### Comparar y sincronizar

- **Sync Local Project**: comparar una carpeta local contra una biblioteca del
  servidor y ver, miembro por miembro, qué está sincronizado, qué difiere y qué
  existe en un solo lado. Desde ahí, subir al servidor el trabajo hecho localmente,
  reemplazando un miembro o creando el que aún no está, bajar los cambios del
  servidor, sincronizar descripciones en cualquier sentido, o comparar y editar
  ambos lados a la vez. Para subir un proyecto completo en una sola operación en
  lugar de miembro por miembro, use **Upload Local Project**.
- **Sync Server Library**: comparar una biblioteca de proyecto más reciente contra
  una o varias bibliotecas base ordenadas, y reconciliar las diferencias.

### Transferencia

- **Upload Local Project**: devolver un proyecto local a una biblioteca, con una
  vista previa de qué se va a crear y qué se va a reemplazar, y acotando la carga
  por archivo fuente, miembro o tipo. Cuando el archivo fuente de destino todavía no
  existe, usted decide con qué juego de caracteres se crea; y cuando un carácter de
  su fuente no tiene equivalente en el servidor, usted decide qué se escribe en su
  lugar, en vez de enterarse después. También crea o reemplaza objetos `*BNDDIR` a
  partir de los binding directories que el proyecto trae consigo.
- **SavF Manager**: listar los archivos de salvado de una biblioteca o de un valor
  especial (`*ALLUSR`, `*LIBL`, `*CURLIB`, `*ALL`), cada uno con lo que contiene:
  cantidad de objetos, bibliotecas guardadas, compresión, tamaño, propietario y
  última actualización. Recorrer los objetos que hay dentro de un archivo de salvado
  y restaurar todo, una biblioteca, un conjunto de objetos, o **un solo objeto en la
  biblioteca que usted elija**. Guardar objetos o una biblioteca entera en un archivo
  de salvado, añadir más objetos a uno que ya existe, crear, limpiar, eliminar o
  copiar un archivo de salvado a otra biblioteca, y moverlo entre el servidor y su
  máquina en cualquier dirección.

### Editores

- **Binding Directory Editor**: un `*BNDDIR` se mantiene normalmente una entrada a
  la vez, sin forma de ver el conjunto. Aquí la lista completa está en pantalla,
  ordenable y filtrable: añadir, editar y quitar varias entradas y confirmarlas en un
  solo guardado, o descartarlo todo y empezar de nuevo. Una sola pasada indica si
  cada objeto referenciado sigue existiendo en el servidor, y la comparación contra
  otro binding directory muestra qué falta, qué sobra y qué está enlazado con otra
  activación. Funciona contra el servidor o sobre un binding directory descargado a
  un proyecto, que la carga del proyecto puede aplicar después a una biblioteca.
- **Binding Directory Sync**: poner dos binding directories frente a frente, uno de
  destino y uno base, y ver exactamente en qué difieren. Entradas que le faltan al
  destino, entradas de más que el base no tiene, y entradas presentes en ambos pero
  enlazadas con distinto tipo o activación. Una sola acción alinea el destino con el
  base, añadiendo lo que falta, quitando lo que sobra y ajustando el resto, que es lo
  que hace falta cuando un binding directory de desarrollo se ha ido separando de
  aquel con el que se construyó producción.
- **Message File Editor**: abrir un `*MSGF` y ver, añadir y editar sus descripciones
  de mensaje, con búsqueda por ID, texto de primer nivel y ayuda.

### Archivos en spool y volcados

- **Spooled Files Manager**: encontrar archivos en spool por usuario, cola de salida,
  estado, tipo de formulario, dato de usuario, trabajo o rango de fecha y hora. Ver
  el contenido, descargarlo como texto, retener, liberar, cambiar atributos, copiar a
  otra cola de salida una vez que usted haya indicado cómo debe copiarse, eliminar, y
  saltar al trabajo que lo produjo. También abre el
  camino a obtener un PDF de un archivo en spool: la transformación la realiza el
  servidor, o una herramienta de conversión de terceros que usted instale localmente
  e indique en los ajustes.
- **Dump Files Viewer**: importar un volcado de programa ILE (`QPPGMDMP`) y leerlo
  como detalles, archivos, indicadores, variables y el texto en crudo, con búsqueda y
  expandir o contraer. También abre el fuente del programa que falló, en la sentencia
  donde se detuvo y resuelto desde su propia biblioteca o desde la lista de
  bibliotecas, de modo que el volcado y el código que lo produjo quedan uno junto al
  otro. Un buffer de registro puede leerse como los campos del archivo en lugar de
  como bytes, y cada archivo que el programa tenía abierto puede abrirse en el
  **File Viewer**.

### Trabajos

- **Jobs Manager**: filtrar trabajos activos y terminados por usuario, nombre, estado
  o subsistema, con filtros rápidos por columna y una pasada opcional de detalle
  adicional (tipo, hora de entrada, consumo de recursos). Actuar sobre uno o varios a
  la vez: retener, liberar, finalizar de forma controlada o inmediata, cambiar
  atributos. Y saltar directamente al registro del trabajo, a su información, a sus
  archivos en spool o al perfil del usuario.
- **Job Info**: un trabajo en diez pestañas: atributos, registro, pila de llamadas,
  lista de bibliotecas, archivos abiertos, grupos de activación, bloqueos,
  definición, sustituciones de archivo y control de compromiso. Se guarda todo como
  instantánea para reabrirla después, o se importa un informe impreso del trabajo
  para estudiarlo sin conexión alguna, útil cuando alguien le envía la evidencia en
  lugar del acceso.
- **Job Log Viewer**: el registro de un trabajo como una tabla en la que se puede
  trabajar de verdad, con hora, ID de mensaje, severidad, tipo, programa de origen y
  texto, con color según la severidad. Acotarlo a una ventana de tiempo, filtrar por
  tipo o severidad entre los valores presentes en ese registro, o buscar en el texto
  con navegación entre coincidencias. Expandir el texto de segundo nivel de un
  mensaje o de todos a la vez, y guardar el registro para reabrirlo después, o abrir
  uno guardado antes, que es la forma de leer el registro de un sistema al que no
  está conectado.
- **Job Description Info**: consultar objetos `*JOBD` por nombre y biblioteca, con
  comodines, y leer sus atributos en una rejilla agrupada: la lista de bibliotecas
  con la que arranca un trabajo, la cola de trabajos y las prioridades, la cola de
  salida, el nivel de registro de mensajes y el resto. Suele ser donde está la
  respuesta cuando un mismo programa se comporta distinto según cómo se sometió. El
  resultado se puede guardar y reabrir después.
- **Message Queue Viewer**: recorrer una cola de mensajes filtrada por usuario o por
  trabajo de origen, expandir la ayuda de segundo nivel, responder mensajes de
  consulta, y depurar lo ya visto mientras las consultas sin responder quedan
  protegidas. Una cola se puede guardar y reabrir después, que es la forma más simple
  de adjuntar evidencia a un ticket.

### Base de datos

- **File Viewer**: archivos físicos y lógicos, tablas, vistas e índices, eligiendo el
  miembro en un archivo multimiembro y el formato de registro en un lógico
  multiformato. Seis pestañas:
  - **Datos**: los registros, limitados a la cantidad que indique, filtrados por
    columna o con una condición construida haciendo clic sobre las columnas,
    mostrados por nombre corto de sistema o por nombre largo, y exportables a CSV. En
    un archivo físico o una tabla también se pueden **añadir, modificar y eliminar
    registros**.
  - **Info** y **Columnas/Campos**: los atributos del propio archivo y la definición
    de cada campo, incluida su posición en el registro, filtrables y exportables.
  - **Dependientes**: las relaciones de base de datos del archivo, es decir cada
    lógico, vista o índice construido sobre él, con su tipo de objeto, su descripción
    y su nombre largo, de modo que la pregunta «a quién rompo si cambio este formato
    de registro» se responde antes del cambio y no con el compilador después.
  - **Estructura de datos RPG**: generada en formato full free, free o fijo, con o
    sin posiciones, inicializada desde los valores por omisión del tipo de dato o
    desde el primer registro, con el prefijo y el sufijo que usted elija, lista para
    pegar.
  - **Campos personalizados**: leer un archivo como lo lee un programa heredado con
    un **archivo descrito por programa**. Dé el layout, es decir nombre, posiciones,
    tipo y decimales, a mano o importando especificaciones de entrada de RPG o una
    estructura de datos posicional, y los valores decodificados vuelven como una
    rejilla normal, exportable a CSV.
- **Journal Entries Viewer**: para un archivo, un área de datos o una cola de datos
  con journal, listar sus asientos y decodificar cada imagen de registro en las
  propias columnas del archivo, con las imágenes anterior y posterior de cada
  modificación una junto a otra. Acotar la búsqueda a un miembro, a un rango de fecha
  y hora, a un conjunto de tipos de asiento (altas, modificaciones, bajas o los
  códigos que necesite) y a un tope de filas, filtrar el resultado, exportarlo a CSV,
  y saltar al File Viewer para comparar lo que registró el journal con lo que el
  archivo contiene hoy.
- **Stored Procedures Manager**: filtrar procedimientos y funciones SQL por esquema,
  nombre, programa externo o texto dentro de la propia definición. Ver la definición
  y los parámetros, generar una plantilla de llamada, ejecutarla y eliminar la
  rutina.
- **Native Query Info**: todo lo que contiene una consulta `*QRYDFN`, en cuatro
  pestañas. Sus atributos, los archivos que usa con su estado de control de nivel, la
  definición misma con selección, orden y formato expandibles sección por sección, y
  la **sentencia equivalente**, lista para copiar cuando la consulta tiene que
  convertirse en algo que una herramienta moderna pueda ejecutar. Desde ahí se abre
  el analizador de control de nivel de esa biblioteca, y se puede guardar todo para
  reabrirlo después.
- **Data Area Info**: lo que contiene ahora mismo un `*DTAARA`, es decir tipo,
  longitud, posiciones decimales, su valor y su descripción, cada campo copiable con
  un clic. Muchas aplicaciones guardan su configuración y sus interruptores de
  ejecución en áreas de datos, así que suele ser la diferencia entre un programa que
  está mal y un programa al que le dijeron que se comportara así.

### Modelo de datos

Todas las herramientas de abajo trabajan sobre la misma copia del modelo, y nada
llega al archivo del modelo hasta que se pulsa **Save changes**, desde cualquiera de
ellas. **Discard** lo devuelve todo a como estaba guardado.

- **Data Model Extractor**: construir un modelo de datos desde el catálogo Db2, desde
  fuentes nativas DDS y SQL del servidor o del disco, o desde un script DDL.
  Bibliotecas completas o un solo objeto, fusionando o reemplazando, con el resultado
  en un área temporal hasta que usted lo guarde.
- **Data Model Editor**: añadir elementos al modelo a mano, y editar elementos,
  claves, relaciones y dependencias que ninguna extracción puede conocer. Agrupar
  elementos en procesos de negocio, y publicar el modelo en el IFS para el equipo.
- **Claves foráneas implícitas**: encontrar las relaciones que nunca se declararon
  como restricciones. Una tabla que contiene todas las columnas de la clave de otra
  es una candidata, con su nivel de confianza. Ninguna entra al modelo por
  suposición: cada una se confirma contra el catálogo o contra los propios datos,
  contando los registros que quedarían huérfanos.
- **Data Model Viewer**: aquí es donde se construyen los **diagramas
  Entidad-Relación (ERD)**, incluidos los elementos particulares de IBM i, con
  archivos físicos, archivos lógicos y lógicos multiformato dibujados sobre los
  físicos sobre los que se construyen, junto a tablas, vistas e índices. Se agrega un
  elemento, sus relacionados, o todo un proceso de negocio, y el diagrama crece
  alrededor de lo que se quiere explicar en lugar de mostrar la biblioteca entera. Se
  pueden fijar notas al lienzo, y guardar, reabrir y exportar los diagramas como
  imagen.
- **Data Model Dictionary**: un glosario de negocio a nivel de columna. Una fila por
  definición distinta de columna, porque dos columnas que comparten el nombre pero no
  el tipo de dato son dos cosas distintas, y describirlas como una sola produce un
  glosario equivocado. Cada fila lleva su descripción de negocio, el texto que trae
  la fuente, una referencia cruzada de en qué elementos se usa, una medida de cuánto
  está documentado, y exportación a CSV o Markdown.
- **Clasificación de información personal**: marcar qué columnas contienen
  información personal y de qué tipo, dentro del diccionario. La detección propone
  candidatas a partir del nombre de la columna, del texto de la fuente y de la
  descripción, pero **no aplica nada por su cuenta**: toda propuesta pasa por un
  diálogo de revisión. Avisa cuando un mismo nombre de columna quedó clasificado en
  unos archivos y en otros no, porque la exposición real está en lo que falta por
  marcar, y cuando una clasificación quedó suelta porque cambió la definición de la
  columna, para volver a asociarla o descartarla de forma deliberada.
- **Chequeos de salud del modelo**: lo que un modelo acumula con el tiempo.
  Relaciones que apuntan a elementos que no están, referencias a elementos que faltan
  en el modelo, elementos y relaciones duplicados, elementos que nada conecta, y
  caminos de acceso redundantes. Cada hallazgo salta al elemento del que habla.
- **Data Model Comparison**: comparar su modelo contra el servidor ahora, contra otro
  archivo de modelo, o una biblioteca contra otra. Cada diferencia se expresa como
  trabajo a hacer en **su** modelo, es decir añadir, quitar o actualizar, en cuatro
  pestañas: los objetos, cómo se enlazan, los procesos y los diagramas guardados.
  Objetos, dependencias, procesos y diagramas pueden traerse desde el propio panel, y
  el cambio queda sin guardar hasta que se guarde en el Editor. Un proceso o un
  diagrama que ambos modelos tienen ofrece elegir: **replace**, quedarse con la
  versión del otro, o **merge**, traer lo que el otro tiene conservando todo lo que ya
  había. Doble clic en una fila para ver el objeto o la dependencia completos, con
  cada diferencia marcada encima. La columna **Impact** dice hasta dónde llega un
  cambio fuera del modelo: un programa que quizá haya que recompilar, entradas del
  glosario que se desprenderían, y los diagramas y procesos en los que aparece el
  objeto.

### Referencias entre objetos e impacto (beta)

Dos de estas herramientas están en **prueba beta**: Procedure Change Impact Analysis
y Programs Signatures Analyzer. Son utilizables y se usan a diario, pero conviene
revisar sus resultados antes de actuar sobre ellos, y la barra lateral marca cada una
como beta a modo de recordatorio.

- **Programs Level Check Analyzer**: programas que darán error de nivel contra
  archivos de sus bibliotecas de datos, en tres vistas. La comparación de
  identificadores de nivel (con un filtro de «solo afectados» que además revela los
  desajustes en archivos con el control de nivel desactivado), la lista resultante de
  programas a recompilar, y los archivos implicados. Copiar la lista o exportar
  cualquiera de las vistas.
- **Native Query Level Check Analyzer**: consultas `*QRYDFN` que fallarán porque
  cambió la definición de un archivo.
- **Programs Signatures Analyzer**: los llamadores que fallarán al activarse porque
  el programa de servicio al que fueron enlazados ya no lleva la firma que ellos
  tienen, en tres vistas: la comparación, los llamadores a reenlazar y los programas
  de servicio implicados.
- **Object Change Impact Analysis**: qué rompería un cambio en un objeto.
  Dependientes a recrear, programas a recompilar, procedimientos almacenados
  afectados, y además el plan de reconstrucción en el orden en que hay que
  ejecutarlo. Opcionalmente recorre también el grafo de llamadas, para mostrar quién
  llama a los programas que hay que recompilar.
- **Procedure Change Impact Analysis**: para un subprocedimiento exportado, cada
  módulo, programa de servicio y programa a recompilar, en orden. **Confirm in
  source** lee los fuentes de los objetos enlazados directamente al que contiene el
  procedimiento e indica cuáles lo nombran. El objeto compilado no puede responder
  eso, así que no encontrarlo significa que no hay evidencia explícita, nunca que no
  se use. Opcionalmente lista también los programas que llaman a los afectados, solo
  para revisión.
- **Library Compile Order**: todos los fuentes de una biblioteca en un orden de
  construcción seguro según sus dependencias, primero los archivos, luego los
  módulos, después los programas de servicio y por último los programas. Abrir o
  copiar el fuente de un miembro, o ejecutar una acción de compilación sobre los que
  seleccione.
- **Object & Sources**: reconciliar miembros fuente contra objetos compilados.
  Objetos sin fuente, fuentes sin objeto y objetos desactualizados, con reglas de
  exclusión configurables.

### Sistema y usuarios

- **PTF Status**: PTF individuales o grupos completos de PTF, filtrados por
  identificador o por producto, con su estado de instalación (cargado, aplicado,
  reemplazado) y exportación a CSV.
- **User Info**: consultar un perfil de usuario por nombre, o varios a la vez con un
  comodín eligiendo entre las coincidencias, y leer cada atributo que lleva en una
  rejilla agrupada. Clase y autoridades especiales, perfil de grupo y grupos
  suplementarios, programa y menú iniciales, biblioteca actual, limitación de
  capacidades, estado de la contraseña y su caducidad, intentos de inicio de sesión y
  estado, almacenamiento usado, y cuándo se usó por última vez. Suficiente para
  responder «por qué este usuario puede hacer eso», o por qué no puede, en un solo
  sitio, y el resultado se puede guardar y reabrir después.
- **Review Authority Failures**: asientos de fallo de autorización del journal de
  auditoría de seguridad sobre un rango de fecha y hora (las últimas 24 horas por
  omisión), excluyendo los usuarios de servicio que solo generan ruido, con un tope
  de filas, detalle de las autoridades que hay sobre el objeto que rechazó el acceso,
  y exportación a CSV.

### Desde el editor

Con un miembro fuente abierto, el menú contextual del editor añade:

- **Extract SQL to Run**: seleccionar las líneas donde un fuente RPG o CL arma su
  consulta y la sentencia se abre lista para ejecutar, con los valores que aporta el
  programa dejados como marcas que rellenar. Cada línea dice de qué línea del fuente
  salió. Sin selección, un fuente RPG ofrece las sentencias que tiene escritas
  completas.
- **Copy Source to Location**: copiar el miembro a otra biblioteca o archivo fuente.
- **Download Source to Local Project**: llevarlo a una carpeta de proyecto local.
- **File Viewer**: saltar del fuente a los datos.
- **Open Referenced Object Source, desde el servidor o desde local**: seleccionar el
  nombre de un programa o copybook en el código y abrir su fuente, resuelto por el
  orden de la lista de bibliotecas (el mismo miembro que tomaría el compilador) o
  desde el proyecto abierto.

### Ajustes y Acerca de

- **Tools4i Settings**: todos los ajustes que aporta la extensión, en un solo
  formulario con búsqueda.
- **About Tools4i**: versión, autor, licencia y la compilación de Code for IBM i
  sobre la que se está ejecutando.

## Ajustes

Ejecute **Tools4i Settings** para ver, en un único formulario con búsqueda, todos los
ajustes que aporta la extensión: duplicación de archivos en spool, convenciones de
nombres para el orden de compilación, cómo se deja un fuente local en el servidor
antes de **Run Action on Server** y dónde se muestran sus errores de compilación,
valores por omisión de la reconciliación entre objetos y fuentes, registro de
diagnóstico, creación de PDF, almacenamiento del modelo de datos, colores y formas, y
las protecciones que se describen abajo. Cada sección puede volver a lo que trae
Tools4i con **Restore defaults**, que además deja esa sección siguiendo las mejoras
que esos valores reciban más adelante. Los mismos ajustes están disponibles en el
editor de configuración de VS Code buscando `@ext:tools4i.tools4i`.

**Bibliotecas protegidas**: bibliotecas que la extensión no debe modificar nunca. Ahí
se bloquean sus propias operaciones de copia, renombrado, borrado, cambio de
descripción, despliegues, escrituras de sincronización y guardados de los editores, y
sus miembros fuente se abren en modo de solo lectura.

**Protección de producción**: toda conexión cuyo nombre de host o dirección IP no
figure en su lista de sistemas de desarrollo se trata como producción. Se pueden
bloquear los cambios destructivos, la creación de objetos, las cargas y las
escrituras de sincronización, los guardados de los editores y los despliegues, y la
interfaz muestra un aviso rojo de producción.

## Privacidad y seguridad

Tools4i no realiza ninguna conexión de red propia, no lleva telemetría y no necesita
cuenta. El único sistema con el que habla es su propio IBM i, a través de la conexión
que ya tiene Code for IBM i.

Tampoco instala ningún componente de servidor. Una sola función opcional, apagada
mientras usted no la encienda, pregunta antes de compilar en su sistema un
programa CL de 55 líneas, y
[su fuente está publicado aquí](server/IUDUPSP3.clle) para que nadie tenga que
creérselo de palabra. Un ajuste cambia esa función a un modo que no compila nada,
o la desactiva por completo, y en producción el despliegue está bloqueado de
serie.

El detalle está en [SECURITY.md](SECURITY.md), en inglés.

## Soporte

- **¿Algo roto, o una idea?**
  [Abra una issue](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose).
  Puede escribirla en español.
- **¿Prefiere el correo?** tools4i.support@gmail.com
- **¿Quiere ayudar?** [CONTRIBUTING.md](CONTRIBUTING.md) cuenta qué es lo más
  útil, desde un buen reporte de fallo hasta corregir estas páginas.

## Colaboradores

**Juan J. Concepción**, autor y responsable del proyecto.

Tools4i se apoya en el trabajo de otros:

- **[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)**
  y todas las personas que han contribuido a él. Tools4i se construye sobre esa
  extensión y depende de ella; la extiende, no la reemplaza.
- **Cytoscape.js** y **Dagre**, que dibujan y distribuyen los diagramas del modelo de
  datos. Cada componente incluido y su licencia figuran en
  [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

Y gracias también a los programadores de IBM i cuyo trabajo diario decidió qué se
construía: cada herramienta empezó siendo una tarea que alguien estaba haciendo por
el camino largo.

## Licencia

MIT. Vea el archivo [LICENSE](LICENSE). Ese mismo archivo de licencia viaja dentro
del paquete de la extensión.
