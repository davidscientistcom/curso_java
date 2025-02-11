## Ejercicio 6: Saludo Personalizado  
**Enunciado:**  
Pide al usuario que introduzca su nombre y muestra en la consola el mensaje:  
```
¡Hola, [nombre]!
```  

**Solución:**

```java
import java.util.Scanner;

public class SaludoPersonalizado {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicita el nombre del usuario
        System.out.print("Introduce tu nombre: ");
        String nombre = sc.nextLine();
        
        // Muestra el saludo personalizado
        System.out.println("¡Hola, " + nombre + "!");
        
        sc.close();
    }
}
```



## Ejercicio 7: Edad en 5 Años  
**Enunciado:**  
Pide al usuario que introduzca su edad actual y calcula cuál será su edad dentro de 5 años. Muestra el resultado en la consola.

**Solución:**

```java
import java.util.Scanner;

public class EdadEnCincoAnios {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicita la edad actual del usuario
        System.out.print("Introduce tu edad actual: ");
        int edad = sc.nextInt();
        
        // Calcula la edad en 5 años
        int edadFutura = edad + 5;
        
        // Muestra el resultado
        System.out.println("En 5 años, tendrás " + edadFutura + " años.");
        
        sc.close();
    }
}
```



## Ejercicio 8: Conversión de Temperatura  
**Enunciado:**  
Pide al usuario que introduzca una temperatura en grados Celsius y convierte ese valor a Fahrenheit utilizando la fórmula:  
\[
\text{Fahrenheit} = \text{Celsius} \times \frac{9}{5} + 32
\]  
Muestra el resultado en la consola.

**Solución:**

```java
import java.util.Scanner;

public class ConversionTemperatura {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicita la temperatura en Celsius
        System.out.print("Introduce la temperatura en grados Celsius: ");
        double celsius = sc.nextDouble();
        
        // Realiza la conversión a Fahrenheit
        double fahrenheit = celsius * 9 / 5 + 32;
        
        // Muestra el resultado
        System.out.printf("La temperatura en Fahrenheit es: %.2f%n", fahrenheit);
        
        sc.close();
    }
}
```



## Ejercicio 9: Concatenación de Frases  
**Enunciado:**  
Pide al usuario que introduzca dos palabras (por ejemplo, un adjetivo y un sustantivo) y muestra en la consola la concatenación de ambas palabras separadas por un espacio.

**Solución:**

```java
import java.util.Scanner;

public class ConcatenacionFrases {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicita la primera palabra
        System.out.print("Introduce la primera palabra: ");
        String palabra1 = sc.nextLine();
        
        // Solicita la segunda palabra
        System.out.print("Introduce la segunda palabra: ");
        String palabra2 = sc.nextLine();
        
        // Concatena las dos palabras con un espacio en medio
        String resultado = palabra1 + " " + palabra2;
        
        // Muestra el resultado
        System.out.println("La concatenación es: " + resultado);
        
        sc.close();
    }
}
```
