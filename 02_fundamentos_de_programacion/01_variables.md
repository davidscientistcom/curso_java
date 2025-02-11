# Capítulo: Variables en Java – Conceptos, Uso y Ejemplos

En la programación, **una variable es un elemento fundamental** que permite almacenar información en la memoria del ordenador durante la ejecución de un programa. Imagina que estás en una cocina: una variable es como una caja etiquetada en la que puedes guardar ingredientes. La etiqueta (el nombre) te dice qué contiene, y el contenido (el valor) puede cambiar según lo que necesites preparar. Sin variables, cada dato que necesites en el programa tendría que estar "escrito" directamente en el código, lo que limitaría enormemente la flexibilidad y la capacidad de realizar cálculos, comparaciones o almacenar información del usuario.



## 2.1 Tipos de Datos Básicos

Antes de usar una variable, debemos decidir qué tipo de dato va a almacenar. Esto es crucial porque el **tipo** determina qué operaciones se pueden realizar y qué espacio se reserva en la memoria. En Java, los tipos de datos se dividen en dos grandes grupos: los **primitivos** y los **no primitivos** (objetos).

### Tipos Primitivos

1. **Números Enteros:**  
   Se utilizan para almacenar números sin parte decimal.  
   - **`byte`**: Ocupa 8 bits. Ideal para valores pequeños (rango: -128 a 127).  
     *Ejemplo conceptual:* Imagina que guardas la cantidad de pelotas en una pequeña caja; es poco probable que tengas más de 127 pelotas.  
   - **`short`**: Ocupa 16 bits.  
   - **`int`**: Ocupa 32 bits y es el tipo entero más común.  
   - **`long`**: Ocupa 64 bits, para números muy grandes. Se añade una “L” al final del valor para indicar que es de tipo `long`.

2. **Números de Punto Flotante:**  
   Permiten almacenar números con decimales.  
   - **`float`**: Precisión simple. Se debe colocar una “f” al final del valor.  
   - **`double`**: Precisión doble, el más habitual para cálculos que requieren decimales.

3. **Caracteres:**  
   - **`char`**: Almacena un solo carácter (como una letra o símbolo). Internamente, Java utiliza un código numérico (Unicode) para representar cada carácter.  
     *Ejemplo conceptual:* La letra 'A' se representa internamente con un número (65 en el código ASCII).

4. **Booleanos:**  
   - **`boolean`**: Representa valores lógicos: `true` o `false`.  
     Este tipo es fundamental para tomar decisiones en el código (por ejemplo, para evaluar si se cumple una condición).

### Tipos No Primitivos

- **`String`**: Aunque no es un tipo primitivo, es muy utilizado para representar cadenas de texto. Un `String` es un objeto que contiene una secuencia de caracteres.  
  *Ejemplo:* `"Hola, Mundo"`.

> **Reflexión:**  
> La correcta elección del tipo de dato asegura que la variable ocupe el espacio justo en memoria y que se puedan aplicar las operaciones adecuadas. Por ejemplo, no tendría sentido intentar sumar letras o dividir booleanos.



## 2.2 Declaración de Variables

Declarar una variable es el proceso mediante el cual le indicamos al compilador que vamos a reservar un espacio en memoria para almacenar un dato. Esto se hace especificando el **tipo de dato** y el **nombre** de la variable.

### ¿Qué implica declarar una variable?

- **Reservar espacio en memoria:**  
  Cuando declaras una variable, el sistema asigna un espacio en la memoria para guardar su valor.
- **Definir el tipo de dato:**  
  Esto determina qué clase de valores se pueden almacenar y qué operaciones se pueden aplicar.

### Ejemplos y Explicación

- **Declaración simple:**

  ```java
  int edad;
  ```
  
  Aquí se declara una variable llamada `edad` de tipo `int`. En este punto, la variable existe, pero aún no tiene un valor asignado.

- **Declaración e Inicialización:**

  ```java
  int edad = 18;
  ```

  Con esta línea, además de declarar la variable `edad`, se le asigna un valor inicial (18).  
  **¿Por qué es importante inicializar?**  
  No inicializar una variable puede dar lugar a errores o comportamientos inesperados, ya que en Java (a diferencia de algunos otros lenguajes) las variables locales deben tener un valor asignado antes de usarse.

> **Analogía:**  
> Piensa en declarar una variable como encargar una caja con etiqueta en una tienda. Inicializarla es como poner el contenido en la caja desde el inicio, de modo que cuando necesites el contenido, ya esté allí.



## 2.3 Constantes

En ocasiones, necesitamos almacenar valores que **no deben cambiar** a lo largo de la ejecución del programa. Para ello, Java nos permite definir **constantes** utilizando la palabra clave `final`.  
Una vez asignado, el valor de una constante no puede ser modificado.

### Ejemplo y Explicación

```java
final double PI = 3.1416;
```

- Aquí, `PI` es una constante. Se recomienda escribir sus identificadores en mayúsculas para diferenciarlas fácilmente.
- **¿Para qué se emplean?**  
  Las constantes se usan para valores fijos, como el valor de PI, límites de un rango, configuraciones que no deben cambiar, etc. Esto mejora la legibilidad y reduce el riesgo de errores, ya que no se puede modificar accidentalmente.



## 2.4 Operaciones Numéricas

Las variables de tipo numérico se utilizan en cálculos y operaciones aritméticas. Java permite realizar operaciones matemáticas básicas con estas variables, lo que es fundamental en cualquier aplicación que realice cálculos.

### Operadores Aritméticos y su Explicación

- **Suma (`+`):**  
  Se utiliza para agregar dos números.  
  *Ejemplo:* Si `a = 10` y `b = 5`, entonces `a + b` es 15.  
  **Uso en la vida real:** Sumar cantidades en una factura o acumular puntajes.

- **Resta (`-`):**  
  Resta el valor de una variable de otra.  
  *Ejemplo:* `10 - 5` da 5.

- **Multiplicación (`*`):**  
  Multiplica dos números.  
  *Ejemplo:* `10 * 5` da 50.

- **División (`/`):**  
  Divide un número entre otro. Es importante distinguir la división entera de la división real (decimal).  
  *Ejemplo:* `10 / 3` en enteros da 3 (se descarta la parte decimal); mientras que `10.0 / 3.0` da aproximadamente 3.33.

- **Módulo (`%`):**  
  Calcula el resto de una división.  
  *Ejemplo:* `10 % 3` es 1, ya que 10 dividido entre 3 da 3 de cociente y 1 de resto.

> **Importancia:**  
> Las operaciones numéricas permiten resolver problemas desde cálculos sencillos hasta algoritmos complejos, y son la base para el desarrollo de programas interactivos y aplicaciones que realizan procesamiento de datos.



## 2.5 Operaciones con Caracteres

Aunque los caracteres (`char`) representan letras o símbolos, en Java se tratan internamente como números (según el estándar Unicode). Esto abre la posibilidad de realizar operaciones aritméticas con ellos.

### Ejemplo y Explicación

- **Obtener el código Unicode:**  
  Cada carácter tiene un valor numérico.  
  ```java
  char letra = 'A';
  int codigo = letra;  // Se convierte implícitamente a su valor numérico, que es 65 en ASCII/Unicode.
  ```
  **¿Para qué se emplea esto?**  
  Puede ser útil para comparar caracteres, ordenar textos o incluso para generar patrones (por ejemplo, para obtener la siguiente letra en el alfabeto).

- **Operar para obtener el siguiente carácter:**
  ```java
  char letra = 'A';
  char siguiente = (char) (letra + 1);  // Se obtiene 'B'
  ```
  Esto ilustra cómo, al tratar a los caracteres como números, podemos realizar cálculos y luego volver a convertirlos en caracteres.



## 2.6 Concatenación de Cadenas

La **concatenación** es el proceso de unir dos o más cadenas de texto. En Java, el operador `+` se utiliza para este propósito.  
Esto permite construir mensajes dinámicos y formar textos a partir de datos variables.

### Ejemplo y Explicación

```java
String saludo = "Hola";
String nombre = "Carlos";
String mensaje = saludo + ", " + nombre + "!";
```

- **¿Qué ocurre aquí?**  
  Se combinan las cadenas para formar el mensaje `"Hola, Carlos!"`.
- **Aplicación práctica:**  
  Es muy útil para generar informes, mostrar resultados al usuario o construir mensajes de error.

> **Consejo:**  
> Cuando se concatena una cadena con otro tipo de dato (por ejemplo, un número), Java convierte automáticamente ese otro dato en su representación textual. Esto facilita la creación de mensajes sin necesidad de hacer conversiones explícitas.



## 2.7 Operaciones Lógicas y de Comparación

Las variables también se utilizan para tomar decisiones en un programa. Para ello, se emplean operaciones lógicas y de comparación que evalúan condiciones y devuelven un valor booleano (`true` o `false`).

### Explicación de los Operadores

- **Comparación:**
  - **Igualdad (`==`):** Compara si dos valores son iguales.  
    *Ejemplo:* `5 == 5` devuelve `true`.
  - **Desigualdad (`!=`):** Verifica si dos valores son diferentes.
  - **Mayor/Menor que (`>`, `<`, `>=`, `<=`):** Permiten comparar magnitudes.

- **Lógicos:**
  - **AND (`&&`):** Devuelve `true` solo si ambas condiciones son verdaderas.  
    *Ejemplo:* `(edad > 18) && (edad < 65)` es `true` solo si la edad está en ese rango.
  - **OR (`||`):** Devuelve `true` si al menos una de las condiciones es verdadera.
  - **Negación (`!`):** Invierte el valor lógico de una expresión.

> **Uso en la práctica:**  
> Estas operaciones son esenciales para estructuras de control (como `if`, `while`, etc.), permitiendo decidir qué camino debe seguir la ejecución del programa en función de las condiciones evaluadas.



## 2.8 Conversión de Tipos de Datos

Muchas veces, necesitamos transformar una variable de un tipo a otro. Esto se denomina **casting** o conversión de tipos, y es muy importante para asegurar que las operaciones se realicen de forma correcta y sin pérdidas inesperadas.

### Tipos de Conversión

1. **Conversión Implícita (Widening):**  
   Ocurre cuando se asigna un valor de un tipo de menor capacidad a uno de mayor capacidad.  
   *Ejemplo:*
   ```java
   int numeroEntero = 10;
   double numeroDecimal = numeroEntero;  // La conversión se hace automáticamente, 10 se convierte en 10.0.
   ```

2. **Conversión Explícita (Narrowing):**  
   Se requiere cuando se convierte un valor de mayor capacidad a uno de menor, lo que puede conllevar pérdida de información. Se realiza indicando el tipo destino entre paréntesis.  
   *Ejemplo:*
   ```java
   double valorDecimal = 9.99;
   int valorEntero = (int) valorDecimal;  // Se trunca la parte decimal, obteniendo 9.
   ```

3. **Conversiones entre `char` e `int`:**  
   Dado que un `char` es en realidad un número (código Unicode), se pueden hacer conversiones en ambos sentidos:
   ```java
   char letra = 'A';
   int codigo = letra;  // Implicitamente se convierte a su valor numérico (65).
   
   int otroCodigo = 66;
   char otraLetra = (char) otroCodigo;  // Se obtiene 'B'.
   ```

> **Precaución:**  
> Siempre que se realice una conversión explícita, es importante tener en cuenta la posible pérdida de datos (por ejemplo, la parte decimal al convertir de `double` a `int`).


