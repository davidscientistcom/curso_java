## Diferencias entre tipos primitivos y clases envoltorio en Java

En Java, existen dos grandes grupos de tipos de datos:

1. **Tipos primitivos**: son los tipos básicos del lenguaje, como `int`, `double`, `boolean`, etc.  
2. **Clases envoltorio (wrapper classes)**: son clases que permiten trabajar con los tipos primitivos como si fueran objetos. Por ejemplo: `Integer`, `Double`, `Boolean`, etc.

### Tabla comparativa

| Tipo primitivo | Clase envoltorio |
|----------------|------------------|
| `int`          | `Integer`        |
| `double`       | `Double`         |
| `boolean`      | `Boolean`        |
| `char`         | `Character`      |
| `long`         | `Long`           |
| `float`        | `Float`          |
| `byte`         | `Byte`           |
| `short`        | `Short`          |

### Diferencias clave

1. **`int` es un tipo de dato primitivo**, mientras que **`Integer` es una clase**.
2. Los tipos primitivos **no pueden ser null**, mientras que las clases envoltorio **sí pueden ser null**.
3. Los tipos primitivos **no tienen métodos**, las clases envoltorio **sí**.
4. Las clases envoltorio permiten que los valores primitivos puedan utilizarse en estructuras que requieren objetos (como colecciones).


### Ejemplo comparativo entre `int` e `Integer`

```java
int a = 5;  // tipo primitivo
Integer b = 5;  // clase envoltorio (autoboxing)

System.out.println(a + 1);       // Operación directa
System.out.println(b.toString()); // Llamada a método porque es objeto

Integer c = null;
// int d = null;  // Error: un primitivo no puede ser null
```

## Diferencias entre `String` y `StringBuilder`

En Java, `String` y `StringBuilder` se usan para trabajar con texto, pero su comportamiento es diferente:

| Característica             | `String`                    | `StringBuilder`                 |
|---------------------------|-----------------------------|----------------------------------|
| Inmutabilidad              | Inmutable (no cambia)       | Mutable (sí cambia)              |
| Rendimiento en concatenación | Bajo (crea nuevos objetos) | Alto (modifica el mismo objeto)  |
| Uso recomendado            | Texto fijo o poco cambiante | Texto que se modifica frecuentemente |



### ¿Qué significa que `String` es inmutable?

Cada vez que se modifica un `String`, se crea un **nuevo objeto** en memoria.

```java
String texto = "Hola";
texto = texto + " mundo";  // Se crea un nuevo objeto, no se modifica el original
```

En cambio, `StringBuilder` **modifica directamente el contenido**, sin crear nuevos objetos.

```java
StringBuilder sb = new StringBuilder("Hola");
sb.append(" mundo");  // Se modifica el mismo objeto
System.out.println(sb.toString());  // "Hola mundo"
```


### Ejemplo de diferencia de rendimiento

Concatenar muchas cadenas con `String`:

```java
public class Main_bak {
    public static void main(String[] args) {
        final int N = 100_000;

        // Medir con String
        long inicioString = System.nanoTime();
        String texto = "";
        for (int i = 0; i < N; i++) {
            texto += i;
        }
        long finString = System.nanoTime();
        long tiempoString = finString - inicioString;
        System.out.println("Tiempo con String: " + tiempoString + " nanosegundos");

        // Medir con StringBuilder
        long inicioBuilder = System.nanoTime();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < N; i++) {
            sb.append(i);
        }
        long finBuilder = System.nanoTime();
        long tiempoBuilder = finBuilder - inicioBuilder;
        System.out.println("Tiempo con StringBuilder: " + tiempoBuilder + " nanosegundos");

        // Comparación
        System.out.println("StringBuilder fue " + (double) tiempoString / tiempoBuilder + " veces más rápido");
    }
}

```

## Ejemplos:

### 1. **Un tipo primitivo no puede ser `null`, pero un envoltorio sí**

```java
int a = 5;
// a = null;  // Error de compilación

Integer b = 5;
b = null;     // Válido porque Integer es una clase
```



### 2. **`Integer` se puede usar en colecciones, `int` no**

```java
import java.util.*;

List<Integer> lista = new ArrayList<>();
lista.add(10);
lista.add(20);

// List<int> lista2 = new ArrayList<>();  // No se puede usar tipos primitivos en colecciones
```



### 3. **Comparación entre objetos `Integer` (uso de `==` vs `.equals()`)**

```java
Integer x = 100;
Integer y = 100;
System.out.println(x == y);       // true (por caché de enteros entre -128 y 127)
System.out.println(x.equals(y));  // true

Integer z = 200;
Integer w = 200;
System.out.println(z == w);       // false (no está cacheado)
System.out.println(z.equals(w));  // true
```



### 4. **Autoboxing y unboxing**

En Java, cada tipo primitivo tiene una clase envoltorio correspondiente:

- `int` → `Integer`
- `double` → `Double`
- `char` → `Character`
- `boolean` → `Boolean`
- `long` → `Long`
- `float` → `Float`
- `short` → `Short`
- `byte` → `Byte`

Java permite convertir entre ambos mediante:

1. **Autoboxing**: de primitivo a objeto automáticamente
2. **Unboxing**: de objeto a primitivo automáticamente
3. **Conversiones manuales** usando constructores o métodos estáticos


### Autoboxing (de primitivo a envoltorio)

```java
int a = 10;
Integer obj = a;  // autoboxing automático

double x = 3.14;
Double obj2 = x;

char letra = 'A';
Character letraObj = letra;
```

### Unboxing (de envoltorio a primitivo)

```java
Integer obj = 25;
int b = obj;  // unboxing automático

Double obj2 = 5.67;
double y = obj2;

Boolean flag = true;
boolean bandera = flag;
```

### Conversión manual (primitivo → envoltorio)

```java
int a = 42;
Integer obj = Integer.valueOf(a);

double d = 2.718;
Double dobj = Double.valueOf(d);

boolean estado = false;
Boolean estadoObj = Boolean.valueOf(estado);
```

### Conversión manual (envoltorio → primitivo)

```java
Integer obj = Integer.valueOf(100);
int a = obj.intValue();

Double dobj = Double.valueOf(9.81);
double d = dobj.doubleValue();

Boolean flagObj = Boolean.valueOf(true);
boolean flag = flagObj.booleanValue();
```

### Conversión envoltorio → otros tipos

```java
Integer num = 100;
double d = num.doubleValue();   // 100.0
long l = num.longValue();       // 100
byte b = num.byteValue();       // 100 (cast automático si cabe en el rango)
```

### Comparación segura con null

```java
Integer edad = null;

// int e = edad;  // NullPointerException

if (edad != null && edad > 18) {
    System.out.println("Mayor de edad");
}
```

### Uso en colecciones

```java
List<Integer> lista = new ArrayList<>();
lista.add(10);  // autoboxing
int valor = lista.get(0);  // unboxing
```

### Conversión a String y desde String

```java
Integer n = 123;
String texto = n.toString();  // "123"

String s = "456";
int x = Integer.parseInt(s);  // 456

Double d = Double.valueOf("3.14");  // desde String
```

```java
Integer obj = 50;   // autoboxing: int -> Integer
int prim = obj;     // unboxing: Integer -> int

System.out.println(prim + 1);  // 51
```



### 5. **Un envoltorio tiene métodos, un primitivo no**

```java
int a = 123;
// System.out.println(a.toString());  //  Error: int no tiene métodos

Integer b = 123;
System.out.println(b.toString());  // ✅ "123"
```



### 6. **Calcular suma de una lista con `Integer` (necesario para estructuras)**

```java
List<Integer> numeros = List.of(1, 2, 3, 4, 5);

int suma = 0;
for (Integer n : numeros) {
    suma += n;  // Unboxing automático
}

System.out.println("Suma: " + suma);  // 15
```



### 7. **Conversión a otros tipos y uso de métodos**

```java
Integer numero = 42;

System.out.println(numero.doubleValue());  // 42.0
System.out.println(numero.byteValue());    // 42
System.out.println(numero.compareTo(50));  // -1
```



### 8. **Comparar `null` de forma segura**

```java
Integer edad = null;

// if (edad > 18) { ... }  //  NullPointerException

if (edad != null && edad > 18) {
    System.out.println("Mayor de edad");
}
```



### 9. **Casting entre primitivos vs envoltorios**

```java
int a = (int) 3.14;          // Truncado a 3
Integer b = (int) 3.14;      // También válido con autoboxing

Double d = 5.6;
int c = d.intValue();        // 5
```


### 10. **Uso en parámetros de funciones**

```java
public static void mostrar(Integer numero) {
    System.out.println("Valor: " + numero);
}

public static void main(String[] args) {
    int x = 100;
    mostrar(x);  // ✅ Autoboxing de int a Integer
}
```

## ¿Qué es la caché de enteros en Java?

Cuando haces esto:

```java
Integer x = 100;
Integer y = 100;
System.out.println(x == y);  // true
```

Java **no crea dos objetos distintos**, sino que **recicla el mismo objeto** si el valor está entre **-128 y 127**. Esto lo hace para **optimizar memoria** porque son los valores que más se usan.

A este mecanismo se le llama **Integer Cache**.


## ⚠️ Fuera de ese rango, no hay caché

```java
Integer x = 200;
Integer y = 200;
System.out.println(x == y);  // false
```

En este caso, **se crean dos objetos diferentes**, y por eso el `==` da `false`, aunque el valor interno sea el mismo.


## 📌 ¿Qué hace `==` con objetos?

- `==` compara si **las referencias apuntan al mismo objeto en memoria**
- `.equals()` compara si **el contenido (valor) es igual**


## 🧪 Ejemplo completo para clase:

```java
public class CacheEnteros {
    public static void main(String[] args) {
        Integer a = 100;
        Integer b = 100;
        Integer c = 200;
        Integer d = 200;

        System.out.println("a == b: " + (a == b));           // true (está cacheado)
        System.out.println("a.equals(b): " + a.equals(b));   // true

        System.out.println("c == d: " + (c == d));           // false (no cacheado)
        System.out.println("c.equals(d): " + c.equals(d));   // true
    }
}
```


## 🔍 ¿Por qué ocurre esto?

Internamente, Java usa un array estático con valores precargados:

```java
// Esto ocurre dentro de Integer.valueOf(int i)
if (i >= -128 && i <= 127) {
    return IntegerCache.cache[i + 128];  // Devuelve el mismo objeto
} else {
    return new Integer(i);  // Crea un nuevo objeto
}
```

Esto aplica **cuando usas `Integer x = valor;`** o `Integer.valueOf(valor)`, **no cuando haces `new Integer(valor)`**, que **siempre crea un objeto nuevo**.


## Reglas

| Comparación           | Resultado | Motivo                      |
|-----------------------|-----------|-----------------------------|
| `Integer a = 100;`<br>`Integer b = 100;`<br>`a == b` | `true`     | Dentro de caché `[-128,127]` |
| `Integer a = 200;`<br>`Integer b = 200;`<br>`a == b` | `false`    | Fuera de caché               |
| `a.equals(b)`         | `true`    | Compara contenido           |
| `Integer a = new Integer(100);`<br>`Integer b = new Integer(100);`<br>`a == b` | `false` | Siempre distintos objetos   |
