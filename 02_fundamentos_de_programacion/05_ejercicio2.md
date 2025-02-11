## Ejercicios Prácticos

### Ejercicio 1: Calculadora Básica  
**Enunciado:**  
Pide al usuario que introduzca dos números enteros. Calcula y muestra en la consola la suma, la resta, el producto y la división (si el segundo número no es cero) de dichos números.



### Ejercicio 2: Datos Personales  
**Enunciado:**  
Pide al usuario que introduzca su nombre, apellido, edad y DNI (en formato "12345678A"). Muestra un mensaje en consola que contenga todos estos datos y, además, calcula la edad que tendrá el próximo año.



### Ejercicio 3: Manipulación del DNI  
**Enunciado:**  
Pide al usuario que introduzca su DNI en formato "12345678A". A partir de la cadena leída, extrae e imprime por separado la parte numérica (los 8 dígitos) y la letra.



### Ejercicio 4: Operaciones con Caracteres  
**Enunciado:**  
Pide al usuario que introduzca un carácter (por ejemplo, una letra). Muestra en consola el código ASCII (valor numérico) del carácter introducido y, a continuación, muestra el siguiente carácter (por ejemplo, si el usuario introduce 'A', se debe mostrar 'B').



### Ejercicio 5: Inversión de Valor Booleano  
**Enunciado:**  
Pide al usuario que introduzca un valor booleano (true o false). Muestra en consola el valor inverso. Por ejemplo, si el usuario introduce `true`, el programa mostrará `false`, y viceversa.



## Soluciones de los Ejercicios

### Solución Ejercicio 1: Calculadora Básica

```java
import java.util.Scanner;

public class CalculadoraBasica {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Lectura de dos números enteros
        System.out.print("Introduce el primer número: ");
        int num1 = sc.nextInt();
        System.out.print("Introduce el segundo número: ");
        int num2 = sc.nextInt();

        // Operaciones aritméticas
        int suma = num1 + num2;
        int resta = num1 - num2;
        int producto = num1 * num2;
        System.out.println("\n Resultados ");
        System.out.println("Suma: " + suma);
        System.out.println("Resta: " + resta);
        System.out.println("Producto: " + producto);
        
        // División (controlar división por cero)
        if (num2 != 0) {
            int division = num1 / num2;
            System.out.println("División: " + division);
        } else {
            System.out.println("División: No se puede dividir por cero.");
        }
        
        sc.close();
    }
}
```



### Solución Ejercicio 2: Datos Personales

```java
import java.util.Scanner;

public class DatosPersonales {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de datos personales
        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();
        System.out.print("Introduce tu apellido: ");
        String apellido = sc.nextLine();
        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();
        sc.nextLine();  // Consumir salto de línea pendiente
        System.out.print("Introduce tu DNI (ejemplo: 12345678A): ");
        String dni = sc.nextLine();
        
        // Operación: calcular la edad del próximo año
        int edadProxima = edad + 1;
        
        // Mensaje concatenado con todos los datos
        String mensaje = "Nombre: " + nombre + " " + apellido + "\n" +
                         "Edad: " + edad + " (el próximo año tendrás " + edadProxima + " años)\n" +
                         "DNI: " + dni;
        System.out.println("\n Datos Personales ");
        System.out.println(mensaje);
        
        sc.close();
    }
}
```



### Solución Ejercicio 3: Manipulación del DNI

```java
import java.util.Scanner;

public class ManipulacionDNI {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura del DNI
        System.out.print("Introduce tu DNI (ejemplo: 12345678A): ");
        String dni = sc.nextLine();
        
        // Extracción de la parte numérica y la letra
        String numeros = dni.substring(0, 8);  // desde el índice 0 hasta el 7
        String letra = dni.substring(8);       // desde el índice 8 hasta el final
        
        System.out.println("\n Análisis del DNI ");
        System.out.println("Parte numérica: " + numeros);
        System.out.println("Letra: " + letra);
        
        sc.close();
    }
}
```



### Solución Ejercicio 4: Operaciones con Caracteres

```java
import java.util.Scanner;

public class OperacionesConCaracteres {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de un carácter
        System.out.print("Introduce un carácter: ");
        char c = sc.next().charAt(0);
        
        // Obtener el código ASCII y el siguiente carácter
        int codigoAscii = c;  // Conversión implícita a int
        char siguiente = (char) (codigoAscii + 1);
        
        System.out.println("\n Operaciones con el Carácter ");
        System.out.println("El código ASCII de '" + c + "' es: " + codigoAscii);
        System.out.println("El siguiente carácter es: " + siguiente);
        
        sc.close();
    }
}
```



### Solución Ejercicio 5: Inversión de Valor Booleano

```java
import java.util.Scanner;

public class InversionBooleano {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de un valor booleano
        System.out.print("Introduce un valor booleano (true o false): ");
        boolean valor = sc.nextBoolean();
        
        // Inversión del valor
        boolean valorInvertido = !valor;
        
        System.out.println("\n Inversión de Valor Booleano ");
        System.out.println("Valor introducido: " + valor);
        System.out.println("Valor invertido: " + valorInvertido);
        
        sc.close();
    }
}
```
