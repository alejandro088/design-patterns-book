# Catálogo de Patrones de diseño.

#### Abstract Factory \(Fábrica Abstracta\)

Proporciona una interfaz para crear familias de objetos relacionados o que dependen entre sí.

#### Adapter \(Adaptador\)

Convierte la interfaz de una clase en otra distinta que es la que esperan los clientes. Permite que cooperen clases que de otra manera no podrían por tener interfaces incompatibles.

#### Bridge \(Puente\)

Desacopla una abstracción de su implementación, de manera que ambas puedan variar de forma independiente.

#### Builder \(Constructor\)

Separa la construcción de un objeto complejo de su representación, de forma que el mismo proceso de construcción pueda crear diferentes representaciones.

#### Chain of Responsibility \(Cadena de Responsabilidad\)

Evita acoplar el emisor de una petición a su receptor, al dar a mas de un objeto la posibilidad de responder a la petición. Crea una cadena con los objetos receptores y pasa la petición a través de la cadena hasta que ésta sea trata por algún objeto.

#### Command \(Orden\)

Encapsula una petición en un objeto, permitiendo así parametrizar a los clientes con distintas peticiones, encolar o llevar un registro de las peticiones y poder deshacer las operaciones.

#### Composite \(Compuesto\)

Combina objetos en estructuras de árbol para representar jerarquías de parte-todo. Pemite que los clientes traten de manera uniforme a los objetos individuales y a los compuestos.

#### Decorator \(Decorador\)

Añade dinámicamente nuevas responsabilidades a un objeto, proporcionando una alternativa flexible a la herencia para extender la funcionalidad.

#### Facade \(Fachada\)

Proporciona una interfaz unificada para un conjunto de interfaces de un subsistema. Define una interfaz de alto nivel que hace que el subsistema sea más fácil de usar.

#### Factory Method \(Método de Fabricación\)

Define una interfaz para crear un objeto, pero deja que sean las subclases quienes decidan que clase instanciar. Permite que una clase delegue en sus subclases la creación de objetos.

#### Flyweight \(Peso Ligero\)

Usa el comportamiento para permitir un gran número de objetos de grano fino de forma eficiente.

#### Interpreter \(Intérprete\)

Dado un lenguaje, define una representación de su gramática junto con un intérprete que usa dicha representación para interpretar sentencias del lenguaje.

#### Iterator \(Iterador\)

Proporciona un modo de acceder secuencialmente a los elementos de un objeto agregado sin exponer su representación interna.

#### Mediator \(Mediador\)

Define un objeto que encapsula cómo interactúan un conjunto de objetos. Promueve un bajo acoplamiento al evitar que los objetos se refieran unos a otros explícitamente, y permite variar la interacción entre ellos de forma independiente.

#### Memento \(Recuerdo\)

Representa y externaliza el estado interno de un objeto sin violar la encapsulación, de forma que éste puede volver a dicho estado más tarde.

#### Observer \(Observador\)

Define una dependencia de uno-a-muchos entre objetos, de forma que cuando un objeto cambie de estado se notifica y se actualizan automáticamente todos los objetos que dependen de él.

#### Prototype \(Prototipo\)

Especifica los tipos de objetos a crear por medio de una instancia prototípica, y crea nuevos objetos copiando de este prototipo.

#### Proxy \(Apoderado\)

Proporciona un sustituto o representante de otro objeto para controlar el acceso a éste.

#### Singleton \(Único\)

Garantiza que una clase sólo tenga una instancia, y proporciona un punto de acceso global a ella.

#### State \(Estado\)

Permite que un objeto modifique su comportamiento cada vez que cambie su estado interno. Parecerá que cambia la clase del objeto.

#### Strategy \(Estrategia\)

Define una familia de algoritmos, encapsula cada uno de ellos y los hace intercambiables. Permite que un algoritmo varíe independientemente de los clientes que lo usan.

#### Template Method \(Método Plantilla\)

Define en una operación el esqueleto de un algoritmo, delegando en las subclases algunos de sus pasos. Permite que las subclases redefinan ciertos pasos del algoritmo sin cambiar su estructura.

#### Visitor \(Visitante\)

Representa una operación sobre los elementos de una estructura de objetos. Permite definir una nueva operación sin cambiar las clases de los elementos sobre los que opera.

# Organización del catálogo

Los patrones de diseño varían en su granularidad y nivel de abstracción. Dado que existen muchos patrones de diseño, es necesario un modo de organizarlos. Esta sección clasifica los patrones de diseño de manera que podamos referirnos a familias de patrones relacionados. La clasificación ayuda a aprender más rápidamente los patrones del catálogo.

_Tabla: Patrones de diseño._

|  |  | Propósito |  |  |
| :--- | :--- | :--- | :--- | :--- |
|  |  | **De creación** | **Estructurales** | **De comportamiento** |
| **Ámbito** | **Clase** | Factory Method | Adapter \(de clases\) | InterpreterTemplate Method |
|  | **Objeto** | Abstract FactoryBuilderPrototypeSingleton | Adapter \(de objetos\)BridgeCompositeDecoratorFacadeFlyweightProxy | Chain of ResponsabilityCommandIteratorMediatorMementoObserverStateStrategyVisitor |



Esta clasificación está basada en dos criterios. El primero de ellos denominado propósito, refleja que hace un patrón. Los patrones pueden tener un propósito de creación, estructural o de comportamiento. Los patrones de creación tienen que ver con el proceso de creación de objetos. Los patrones estructurales tratan con la composición de clases u objetos. Los de comportamiento caracterizan el modo en que las clases y objetos interactúan y se reparten la responsabilidad.

El segundo criterio, denominado ámbito, especifica si el patrón se aplica principalmente a clases o a objetos. Los patrones de clases se ocupan de las relaciones entre las clases y sus subclases. Estas relaciones se establecen a través de la herencia, de modo que son relaciones estáticas. Los patrones de objetos tratan con las relaciones entre objetos, que pueden cambiarse en tiempo de ejecución y son más dinámicas.





