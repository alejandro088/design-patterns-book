# Abstract Factory \(Fábrica Abstracta\)

## Propósito

Proporciona una interfaz para crear familias de objetos relacionados o que dependen entre sí, sin especificar sus clases concretas.

## También conocido como

Kit

## Motivación

Pensemos en un toolkit de interfaces de usuario que admita múltiples estándares de interfaz de usuario, tales como Motif y Presentation Manager. Los distintos estándares interfaz de usuario definen distintos aspectos y formas de comportamiento de los “útiles” de la interfaz de usuario, como las barras de desplazamiento, ventanas y botones. Para que una aplicación pueda portarse a varios estándares de interfaz de usuario, ésta no debería codificar sus útiles para una interfaz de usuario en particular. Si la  aplicación crea instancias de clases o útiles específicos de la interfaz de usuario, será difícil cambiar ésta más tarde.

Podemos solucionar este problema definiendo una clase abstracta FabricaDeUtiles que declara una interfaz para crear cada tipo básico de útil \(widget\). También hay una clase abstracta para cada tipo de útil, y las subclases concretas implementan útiles para un estándar en concreto de interfaz de usuario. La interfaz de FabricaDeUtiles tiene una operación de devuelve un nuevo objeto para cada clase abstracta de útil. Los clientes llaman a estas operaciones para obtener instancias de útiles, pero no son conscientes de las clases concretas que están usando. De esta manera los clientes son independientes de la interfaz de usuario.

Hay una subclase concreta de FabricaDeUtiles para cada estándar de interfaz de usuario. Cada subclase implementa las operaciones que crean el útil apropiado para su interfaz de usuario. Por ejemplo, la operación CrearBarraDeDesplazamiento de la FabricaDeUtilesMotif crea y devuelve una instancia de una barra de desplazamiento Motif, mientras que la misma operación en FabricaDeUtilesPM devuelve una barra de desplazamiento para Presetantion Manager. Los clientes crean útiles únicamente a través de la interfaz FabricaDeUtiles y no tienen conocimiento de las clases que implementan los útiles para una determinada interfaz de usuario. En otras palabras, los clientes no tienen que atarse a una clase concreta, sino solo a una interfaz definida por una clase abstracta.

Una FabricaDeUtiles también fuerza a que se cumplan las dependencias entre las clases concretas de útiles. Una barra de desplazamiento Motif debería usarse con un botón Motif y un editor de texto Motif, y esa restricción se cumple automáticamente como consecuencia de usar una FabricaDeUtilesMotif.

![](file:///C:/Users/ALEJAN~1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

## Aplicabilidad

Úsese el patrón Abstract Factory cuando

·Un sistema debe ser independiente de como se crean, componen y presentan sus productos.

·Un sistema debe ser configurado con una familia de productos de entre varias.

·Una familia de objetos producto relacionados está diseñada para ser usada conjuntamente, y es necesario hacer cumplir esta restricción.

·Quiere proporcionar una biblioteca de clases de productos, y solo quiere revelar sus interfaces, no sus implementaciones.

## Estructura

![](file:///C:/Users/ALEJAN~1/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

## Participantes

·FabricaAbstracta \(FabricaDeUtiles\)

oDeclara una interfaz para operaciones que crean objetos producto abstractos.

·FabricaConcreta \(FabricaDeUtilesMotif, FabricaDeUtilesPM\)

oImplementa las operaciones para crear objetos producto concretos.

·ProductoAbstracto \(Ventana, BarraDeDesplazamiento\)

oDeclara una interfaz para un tipo de objeto producto.

·ProductoConcreto \(VentanaMotif, BarraDeDesplazamientoMotif\)

oDefine un objeto producto para que sea creado por la fabrica correspondiente.

oImplementa la interfaz ProductoAbstracto

·Cliente

oSolo unas interfaces declaradas por las clases FabricaAbstracta y ProductoAbstracto.

## Colaboraciones

·Normalmente solo se crea una única instancia de una clase FabricaConcreta en tiempo de ejecución. Esta fabrica concreta crea objetos producto que tienen una determinada implementación. Para crear diferentes objetos producto, los clientes deben ser una fábrica concreta diferente.

·FabricaAbstracta delega la creación de objetos producto en su subclase FabricaConcreta

## Consecuencias.

El patron Abstract Factory tiene las siguientes ventajas e inconvenientes:

1.Aísla las clases concretas. El patron Abstract Factory ayuda a controlar las clases de objetos que crea una aplicación. Como una fabrica encapsula la responsabilidad y el proceso de creación de objetos producto, aísla a los clientes de las clases de implementación. Los clientes manipulan instancias a través de sus interfaces abstractas. Los nombres de las clases producto quedan aisladas en la implementación de la fabrica concreta; no aparecen en el código cliente.

2.Facilita el intercambio de familias de productos. La clase de una fabrica concreta solo aparece una vez en una aplicación –cuando se crea--. Esto facilita cambiar la fabrica concreta que usa una aplicación. Como una fabrica abstracta crea una familia completa de productos, toda la familia de productos cambia de una vez. En nuestro ejemplo de la interfaz de usuario, podemos cambiar de útiles Motif a útiles Presentation Manager simplemente cambiando los correspondientes objetos fábrica y volviendo a crear la interfaz.

3.Promueve la consistencia entre productos. Cuando se diseñan objetos producto en una familia para trabajar juntos, es importante que una aplicación use objetos de una sola familia a la vez. FabricaAbstracta facilita que se cumpla esta restricción.

4.Es difícil dar cabida a nuevos tipos de productos. Ampliar las fabricas abstractas para producir nuevos tipos de productos no es fácil. Esto se debe a que la interfaz FabricaAbstracta fija el conjunto de productos que se pueden crear. Permitir nuevos tipos de productos requiere ampliar la interfaz de la fábrica, lo que a su vez implica cambiar la clase FabricaAbstracta y todas sus subclases. En la sección de implementación se analiza una solución a este problema.

## Implementación

Estas son algunas técnicas útiles para implementar el patrón Abstract Factory

1.Fabricas únicas. Normalmente una aplicación solo necesita una instancia de una FabricaConcreta por cada familia de productos. Por tanto, suele implementarse mejor como un Singleton.

2.Crear los productos. FabricaAbstracta solo declara una interfaz para crear productos. Se deja a las subclases ProductoConcreto el crearlos realmente. El modo más común es hacer esto definiendo un método de fabricación para cada producto \(véase el patrón Factory Method\). Una fabrica concreta especificará sus productos redefiniendo el método fabrica de cada uno. Si bien esta implementación es sencilla, requiere una nueva subclase fabrica concreta para cada familia de productos, incluso aunque las familias de productos difieran solo ligeramente.  
 En caso de que sea posible tener muchas familias de productos, la fábrica concreta puede implementarse usando el patrón Prototype. La fabrica concreta se inicializa con una instancia prototípica de cada producto de la familia, y crea un nuevo producto clonando su prototipo. El enfoque basado en prototipos elimina la necesidad de una nueva clase de fabrica concreta para cada nueva familia de productos.

3.Definir fabricas extensibles. FabricaAbstracta por lo general define una operación diferente para cada tipo de producto que puede producir. Los tipos de producto están codificados en las signaturas de las operaciones. Añadir un nuevo tipo de producto requiere cambiar la interfaz de FabricaAbstracta y todas las clases que dependen de ella.  
 Un diseño más flexible, aunque menos seguro, es añadir un parámetro a las operaciones que crean objetos. Este parámetro especifica el tipo de objeto a ser creado. Podría tratarse de un identificador de clase, un entero, una cadena de texto o cualquier otra cosa que identifique el tipo de producto. De hecho, con este enfoque, FabricaAbstracta solo necesita una única operación “Hacer” con un parámetro que indique el tipo de objeto a crear. Esta es la técnica usada en las fábricas abstractas basadas en clases y en prototipos que se examinaron anteriormente.

## Código de ejemplo

Aplicaremos el patrón Abstract Factory para crear una conexión a un motor de base de datos y utilizar su correspondiente ORM. Dicho código junto con la estructura del patrón, está disponible en nuestro repositorio de github [https://github.com/alejandro088/design-patterns-code](https://github.com/alejandro088/design-patterns-code).

El código básicamente lo que hace, es proporcionar una clase abstracta Connection y varias subclases que heredan de esta clase, cada una deberá implementar, el algoritmo correspondiente para la conexión del motor de base de datos que hayamos especificado en el Cliente. En el código de ejemplo, solo se mostrará los datos de la conexión según el driver que hayamos establecido, no hemos proporcionado ninguna lógica adicional.

Como ejercicio, usted deberá implementar en cada conexión, el algoritmo para realizar el acceso a la base de datos de cada motor.

ź

