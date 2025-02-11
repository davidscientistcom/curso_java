# Capítulo: Variables y Operaciones en Java  
*(Enfocado en ejemplos prácticos, incluyendo booleanos y cadenas)*

En Java, una variable es un contenedor en memoria que almacena datos durante la ejecución de un programa. Cada variable tiene un tipo (por ejemplo, `int`, `double`, `boolean`, `String`, etc.) y un nombre. La correcta utilización de las variables y sus operaciones básicas (aritméticas, lógicas, de concatenación y conversión) es esencial para manipular información de forma flexible y dinámica.



## 1. Declaración e Inicialización de Variables

Antes de utilizar una variable, se debe declarar indicando su tipo y nombre. Posteriormente, se le puede asignar (inicializar) un valor.

**Ejemplos:**

- **Sin inicializar:**

  ```java
  int edad;
  String dni;
  boolean activo;
  ```

- **Declaración e inicialización conjunta:**

  ```java
  int edad = 30;
  String dni = "12345678A";
  boolean esEstudiante = true;
  ```

> **Consejo:** Inicializar las variables al declararlas evita errores al usarlas sin un valor asignado.



## 2. Operaciones Aritméticas con Variables Numéricas

Las operaciones aritméticas se aplican a variables numéricas. Aquí se muestran las operaciones básicas:

```java
public class EjemploAritmetica {
    public static void main(String[] args) {
        int a = 10, b = 5;
        
        // Suma, resta, multiplicación y división
        int suma = a + b;        // 10 + 5 = 15
        int resta = a - b;       // 10 - 5 = 5
        int producto = a * b;    // 10 * 5 = 50
        int divisionEntera = a / b;  // 10 / 5 = 2
        
        // División real (decimal)
        double divisionReal = (double) a / b;  // 10 / 5 = 2.0
        
        // Módulo (resto de la división)
        int modulo = 10 % 3;     // 10 % 3 = 1
        
        System.out.println("Suma: " + suma);
        System.out.println("Resta: " + resta);
        System.out.println("Producto: " + producto);
        System.out.println("División entera: " + divisionEntera);
        System.out.println("División real: " + divisionReal);
        System.out.println("Módulo: " + modulo);
        
        // Incremento y decremento
        a++;  // a pasa de 10 a 11
        b--;  // b pasa de 5 a 4
        System.out.println("Después de incremento/decremento: a = " + a + ", b = " + b);
    }
}
```



## 3. Operaciones Booleanas

Las variables booleanas almacenan los valores `true` o `false` y son fundamentales para representar estados o condiciones. Aunque las estructuras de control (como `if`) usan estos valores, aquí se muestran ejemplos de cómo se realizan operaciones con booleanos sin introducir condicionales complejos.

### 3.1 Declaración y Uso de Variables Booleanas

```java
public class EjemploBooleanos {
    public static void main(String[] args) {
        // Declaración e inicialización de variables booleanas
        boolean esMayorDeEdad = true;
        boolean tieneCarnet = false;
        
        System.out.println("¿Es mayor de edad? " + esMayorDeEdad);
        System.out.println("¿Tiene carnet? " + tieneCarnet);
    }
}
```

### 3.2 Operaciones Lógicas con Booleanos

Los operadores lógicos permiten combinar valores booleanos:

- **AND (`&&`):** Verdadero solo si ambas condiciones son verdaderas.
- **OR (`||`):** Verdadero si al menos una condición es verdadera.
- **NOT (`!`):** Invierte el valor booleano.

**Ejemplo:**

```java
public class EjemploOperacionesBooleanas {
    public static void main(String[] args) {
        boolean esAdulto = true;
        boolean tienePermiso = false;
        
        // Operador AND: ambos deben ser verdaderos para que el resultado sea true.
        boolean puedeConducir = esAdulto && tienePermiso;  // false, porque tienePermiso es false
        
        // Operador OR: basta que una sea verdadera.
        boolean puedeEntrar = esAdulto || tienePermiso;  // true, porque esAdulto es true
        
        // Operador NOT: invierte el valor de la variable.
        boolean noEsAdulto = !esAdulto;  // false
        
        System.out.println("Puede conducir (adulto y con permiso): " + puedeConducir);
        System.out.println("Puede entrar (adulto o con permiso): " + puedeEntrar);
        System.out.println("No es adulto: " + noEsAdulto);
    }
}
```

### 3.3 Ejemplo de Cambio de Estado Booleano

A veces es necesario cambiar el valor de una variable booleana (por ejemplo, para activar o desactivar una función).

```java
public class EjemploToggleBooleano {
    public static void main(String[] args) {
        boolean interruptor = false;
        System.out.println("Interruptor inicial: " + interruptor);
        
        // Simulamos un cambio de estado
        interruptor = !interruptor;  // Pasa a true
        System.out.println("Interruptor después de cambiar: " + interruptor);
        
        // Se puede alternar el valor varias veces
        interruptor = !interruptor;  // Vuelve a false
        System.out.println("Interruptor tras segundo cambio: " + interruptor);
    }
}
```



## 4. Operaciones con Cadenas (Strings)

Las **cadenas de texto** son variables de tipo `String` que permiten almacenar y manipular secuencias de caracteres. En Java, se pueden realizar múltiples operaciones con ellas, como concatenar, extraer subcadenas, convertir a mayúsculas o minúsculas, y obtener su longitud.

### 4.1 Concatenación de Cadenas

La concatenación se realiza con el operador `+` y permite unir múltiples cadenas o combinar texto con otros tipos de datos.

```java
public class EjemploConcatenacionCadenas {
    public static void main(String[] args) {
        String nombre = "Carlos";
        String apellido = "García";
        
        // Concatenación simple
        String nombreCompleto = nombre + " " + apellido;
        System.out.println("Nombre completo: " + nombreCompleto);
        
        // Concatenación con otros tipos
        int edad = 40;
        String mensaje = "El señor " + nombreCompleto + " tiene " + edad + " años.";
        System.out.println(mensaje);
    }
}
```

### 4.2 Operaciones Adicionales con Cadenas

Aquí se muestran algunas operaciones adicionales útiles al trabajar con cadenas:

- **Obtener la longitud de una cadena:**

  ```java
  public class EjemploLongitudCadena {
      public static void main(String[] args) {
          String dni = "12345678A";
          int longitud = dni.length();
          System.out.println("La longitud del DNI es: " + longitud);
      }
  }
  ```

- **Convertir una cadena a mayúsculas o minúsculas:**

  ```java
  public class EjemploMayusMinus {
      public static void main(String[] args) {
          String mensaje = "Hola Mundo";
          System.out.println("Mayúsculas: " + mensaje.toUpperCase());
          System.out.println("Minúsculas: " + mensaje.toLowerCase());
      }
  }
  ```

- **Extraer una subcadena (substring):**

  ```java
  public class EjemploSubstring {
      public static void main(String[] args) {
          String dni = "12345678A";
          // Extraer los 8 dígitos numéricos
          String numeros = dni.substring(0, 8);
          // Extraer la letra final
          String letra = dni.substring(8);
          System.out.println("Números: " + numeros);
          System.out.println("Letra: " + letra);
      }
  }
  ```

- **Comparar cadenas:**

  Es importante usar el método `.equals()` en lugar del operador `==` para comparar el contenido de dos cadenas.

  ```java
  public class EjemploComparacionCadenas {
      public static void main(String[] args) {
          String cadena1 = "Hola";
          String cadena2 = "hola";
          
          // Comparación sensible a mayúsculas y minúsculas
          boolean iguales = cadena1.equals(cadena2);
          System.out.println("¿Las cadenas son iguales? " + iguales);
          
          // Comparación ignorando mayúsculas y minúsculas
          boolean igualesIgnoreCase = cadena1.equalsIgnoreCase(cadena2);
          System.out.println("¿Las cadenas son iguales (ignorando mayúsculas)? " + igualesIgnoreCase);
      }
  }
  ```



## 5. Ejemplo Práctico Combinado

En este ejemplo se combinan variables de distintos tipos, incluyendo booleanos y cadenas, para simular el manejo de datos personales como un DNI, nombre y estado activo.

```java
public class EjemploDatosCombinados {
    public static void main(String[] args) {
        // Datos personales
        String nombre = "Laura";
        String dni = "87654321B";
        int edad = 35;
        boolean esActivo = true;
        
        // Concatenación de cadenas para crear un informe
        String informe = "Nombre: " + nombre + "\n" +
                         "DNI: " + dni + "\n" +
                         "Edad: " + edad + "\n" +
                         "Estado: " + (esActivo ? "Activo" : "Inactivo");
        
        System.out.println(informe);
        
        // Operación con el DNI: extraer dígitos y letra
        String numerosDNI = dni.substring(0, 8);
        String letraDNI = dni.substring(8);
        System.out.println("Dígitos DNI: " + numerosDNI);
        System.out.println("Letra DNI: " + letraDNI);
    }
}
```

> **Explicación del Ejemplo:**  
> En este caso se combinan variables de tipo `String`, `int` y `boolean` para formar un informe completo. Además, se muestra cómo extraer parte del contenido de una cadena (como separar los dígitos y la letra del DNI).
