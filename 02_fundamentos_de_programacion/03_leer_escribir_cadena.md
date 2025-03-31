<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

# Lectura y Escritura en Consola en Java

La interacción con la consola es fundamental en las aplicaciones de línea de comandos, ya que permite:

- **Escribir mensajes:** Informar al usuario, mostrar resultados, formatear salidas, etc.
- **Leer datos:** Recoger información introducida por el usuario, lo que permite que el programa responda de forma dinámica.

En Java, para **escribir en la consola** se utilizan principalmente métodos de la clase `System.out` y para **leer datos** se utiliza, de manera habitual, la clase `Scanner` que forma parte del paquete `java.util`.



## 1. Escribir en la Consola

La forma más básica de escribir en la consola es mediante los métodos `System.out.println()` y `System.out.print()`. Además, `System.out.printf()` permite formatear la salida.

### 1.1 Uso de `System.out.println()` y `System.out.print()`

- **`System.out.println()`**: Imprime el contenido en la consola y añade automáticamente un salto de línea al final.

  ```java
  public class EjemploImpresion {
      public static void main(String[] args) {
          System.out.println("Hola, Mundo!");
          System.out.println("Esta es una nueva línea.");
      }
  }
  ```
  *Salida:*
  ```
  Hola, Mundo!
  Esta es una nueva línea.
  ```

- **`System.out.print()`**: Imprime el contenido en la consola sin añadir un salto de línea. Es útil para imprimir varias partes de un mensaje en la misma línea.

  ```java
  public class EjemploImpresionSinSalto {
      public static void main(String[] args) {
          System.out.print("Hola, ");
          System.out.print("Mundo!");
      }
  }
  ```
  *Salida:*
  ```
  Hola, Mundo!
  ```

### 1.2 Uso de `System.out.printf()` y Formateo de la Salida

El método `printf()` (o `format()`) permite formatear la salida de texto de forma similar a la función `printf()` en C. Con él, puedes especificar el formato de números, cadenas y otros datos.

**Ejemplo básico de `printf`:**

```java
public class EjemploPrintf {
    public static void main(String[] args) {
        int edad = 28;
        double salario = 1234.56789;
        
        // %d para enteros, %f para flotantes; %.2f especifica 2 decimales
        System.out.printf("Edad: %d años\nSalario: %.2f euros\n", edad, salario);
    }
}
```

*Salida:*
```
Edad: 28 años
Salario: 1234.57 euros
```

### 1.3 Caracteres de Escape para Formatear la Salida

Los **caracteres de escape** se usan dentro de las cadenas para insertar caracteres especiales:

- **`\n`**: Salto de línea.
- **`\t`**: Tabulación horizontal.
- **`\"`**: Comillas dobles.
- **`\\`**: Barra invertida.

**Ejemplo con caracteres de escape:**

```java
public class EjemploCaracteresEscape {
    public static void main(String[] args) {
        System.out.println("Línea 1\nLínea 2");
        System.out.println("Columna1\tColumna2\tColumna3");
        System.out.println("Ella dijo: \"Hola, ¿cómo estás?\"");
    }
}
```

*Salida:*
```
Línea 1
Línea 2
Columna1	Columna2	Columna3
Ella dijo: "Hola, ¿cómo estás?"
```



## 2. Leer de la Consola

Para leer datos introducidos por el usuario en la consola, Java dispone de la clase `Scanner`. Esta clase permite leer diferentes tipos de datos (cadenas, números enteros, números decimales, etc.).

### 2.1 Importar y Crear un Objeto Scanner

Antes de usar `Scanner`, es necesario importarla:

```java
import java.util.Scanner;
```

Luego se crea un objeto de la clase `Scanner` pasando como parámetro `System.in`, que indica que se leerá desde la consola:

```java
Scanner sc = new Scanner(System.in);
```

### 2.2 Métodos Básicos para Leer Datos

La clase `Scanner` proporciona varios métodos para leer distintos tipos de datos:

- **Leer una cadena (String):**  
  `nextLine()` lee una línea completa.
  ```java
  String linea = sc.nextLine();
  ```

- **Leer un entero (int):**  
  `nextInt()` lee el siguiente entero.
  ```java
  int numero = sc.nextInt();
  ```

- **Leer un número decimal (double):**  
  `nextDouble()` lee el siguiente número con decimales.
  ```java
  double valor = sc.nextDouble();
  ```

- **Leer una palabra (String):**  
  `next()` lee una palabra (hasta encontrar un espacio).
  ```java
  String palabra = sc.next();
  ```

### 2.3 Ejemplo Completo: Lectura de Datos desde la Consola

A continuación, se presenta un ejemplo que lee varios tipos de datos introducidos por el usuario y luego los muestra en la consola:

```java
import java.util.Scanner;

public class EjemploLecturaConsola {
    public static void main(String[] args) {
        // Crear un objeto Scanner para leer desde la consola
        Scanner sc = new Scanner(System.in);
        
        // Leer una cadena completa (por ejemplo, nombre)
        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();
        
        // Leer un entero (por ejemplo, edad)
        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();
        
        // Leer un número decimal (por ejemplo, salario)
        System.out.print("Introduce tu salario: ");
        double salario = sc.nextDouble();
        
        // Consumir el salto de línea pendiente (si se usó nextInt o nextDouble)
        sc.nextLine();
        
        // Leer un DNI (cadena), que puede incluir letras y ceros iniciales
        System.out.print("Introduce tu DNI: ");
        String dni = sc.nextLine();
        
        // Mostrar la información introducida
        System.out.println("\n Datos Introducidos ");
        System.out.println("Nombre: " + nombre);
        System.out.println("Edad: " + edad);
        System.out.printf("Salario: %.2f euros\n", salario);
        System.out.println("DNI: " + dni);
        
        // Cerrar el objeto Scanner (buena práctica)
        sc.close();
    }
}
```

> **Puntos a Destacar:**
> - **Importación de Scanner:** Es imprescindible importar `java.util.Scanner` para poder usarlo.
> - **Creación del objeto:** `Scanner sc = new Scanner(System.in);` indica que se leerá desde la entrada estándar (la consola).
> - **Métodos de lectura:** Se usan `nextLine()`, `nextInt()` y `nextDouble()` según el tipo de dato que se desea leer.
> - **Cierre del Scanner:** Al finalizar, se cierra el objeto Scanner con `sc.close();` para liberar recursos.
> - **Atención con el salto de línea:** Tras usar `nextInt()` o `nextDouble()`, es recomendable consumir el salto de línea residual con un `sc.nextLine()` para evitar problemas en la lectura de líneas completas posteriormente.
Cuando usas métodos como `nextInt()` o `nextDouble()` de la clase `Scanner`, éstos leen únicamente el valor numérico y dejan en el búfer de entrada el carácter de nueva línea (`\n`) que se genera al pulsar Enter. Esto significa que, tras leer un número, el salto de línea sigue "pendiente" en el flujo de entrada.

Si inmediatamente después llamas a `nextLine()` para leer una línea completa, éste leerá ese salto de línea residual en lugar de esperar una nueva entrada del usuario, devolviendo una cadena vacía. Para evitar este comportamiento, es recomendable "consumir" o descartar ese salto de línea llamando a `sc.nextLine()` después de `nextInt()` o `nextDouble()` y antes de usar `nextLine()` para leer una línea de texto.

**Ejemplo:**

```java
import java.util.Scanner;

public class EjemploScanner {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();
        
        // Consumir el salto de línea pendiente
        sc.nextLine();
        
        System.out.print("Introduce tu nombre completo: ");
        String nombre = sc.nextLine();
        
        System.out.println("Edad: " + edad + ", Nombre: " + nombre);
        
        sc.close();
    }
}
```
