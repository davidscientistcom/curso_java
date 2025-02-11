## Ejemplo 1: Operaciones Aritméticas con Números

Este programa lee dos números enteros introducidos por el usuario, realiza operaciones aritméticas (suma, resta, multiplicación y división) y muestra los resultados por consola.

```java
import java.util.Scanner;

public class OperacionesAritmeticas {
    public static void main(String[] args) {
        // Crear objeto Scanner para leer desde la consola
        Scanner sc = new Scanner(System.in);

        // Lectura de dos números enteros
        System.out.print("Introduce el primer número: ");
        int num1 = sc.nextInt();
        System.out.print("Introduce el segundo número: ");
        int num2 = sc.nextInt();

        // Realización de operaciones con variables
        int suma = num1 + num2;
        int resta = num1 - num2;
        int producto = num1 * num2;
        int division = 0;
        if(num2 != 0) {
            division = num1 / num2;  // División entera
        }

        // Escritura de los resultados en consola
        System.out.println("\n Resultados ");
        System.out.println("Suma: " + suma);
        System.out.println("Resta: " + resta);
        System.out.println("Producto: " + producto);
        if(num2 != 0) {
            System.out.println("División: " + division);
        } else {
            System.out.println("División: No se puede dividir por cero.");
        }
        
        // Cerrar el Scanner
        sc.close();
    }
}
```

## Ejemplo 2: Concatenación y Operaciones con Cadenas y Números

Este programa combina la lectura de datos de tipo cadena y número. Lee el nombre, el DNI y la edad del usuario, realiza una operación sencilla (calcular la edad para el próximo año) y utiliza la concatenación para formar mensajes que se muestran en la consola.

```java
import java.util.Scanner;

public class DatosPersonales {
    public static void main(String[] args) {
        // Crear objeto Scanner para leer datos desde la consola
        Scanner sc = new Scanner(System.in);

        // Lectura de datos personales
        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();
        
        System.out.print("Introduce tu DNI: ");
        String dni = sc.nextLine();
        
        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();
        
        // Operación: calcular la edad del próximo año
        int edadProxima = edad + 1;
        
        // Concatenación para formar un mensaje completo
        String mensaje = "El usuario " + nombre + " con DNI " + dni +
                         " tiene " + edad + " años y el próximo año tendrá " + edadProxima + " años.";
        
        // Escritura del mensaje en consola
        System.out.println("\n Información Personal ");
        System.out.println(mensaje);
        
        // Cerrar el Scanner
        sc.close();
    }
}
```



## Ejemplo 3: Combinando Variables, Operaciones y Lectura/Escritura

En este ejemplo se mezclan variables de diferentes tipos, se realizan operaciones sobre ellas y se muestra cómo interactuar con el usuario para obtener y presentar la información.

```java
import java.util.Scanner;

public class EjemploCombinado {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de datos
        System.out.print("Introduce el valor A (entero): ");
        int a = sc.nextInt();
        System.out.print("Introduce el valor B (entero): ");
        int b = sc.nextInt();
        
        // Consumir el salto de línea pendiente
        sc.nextLine();
        
        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();
        
        // Operaciones con variables numéricas
        int suma = a + b;
        int diferencia = a - b;
        int producto = a * b;
        int modulo = a % b;
        
        // Escritura de resultados numéricos
        System.out.println("\n Operaciones con Números ");
        System.out.println("Suma: " + suma);
        System.out.println("Diferencia: " + diferencia);
        System.out.println("Producto: " + producto);
        System.out.println("Módulo: " + modulo);
        
        // Uso de concatenación para crear un mensaje personalizado
        String mensaje = "Hola " + nombre + ", has introducido los números " + a + " y " + b + ".";
        System.out.println("\n Mensaje Personalizado ");
        System.out.println(mensaje);
        
        sc.close();
    }
}
```