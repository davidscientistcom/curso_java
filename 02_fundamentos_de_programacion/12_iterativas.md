# Teoría de los Bucles en Java

Los bucles (o estructuras de repetición) permiten ejecutar repetidamente un bloque de código mientras se cumpla una condición determinada. Son fundamentales para procesar colecciones de datos, realizar cálculos iterativos o simplemente repetir tareas. En Java, las principales estructuras de bucle son:

1. **Bucle _while_:**  
   - **Concepto:** Ejecuta un bloque de código mientras una condición se evalúe como verdadera.  
   - **Sintaxis:**
     ```java
     while (condición) {
         // Bloque de código a repetir
     }
     ```
   - **Características:**  
     Se evalúa la condición antes de cada iteración. Si la condición es falsa desde el inicio, el bloque de código nunca se ejecuta. Es útil cuando no se sabe de antemano cuántas veces se repetirá el bucle.

2. **Bucle _do-while_:**  
   - **Concepto:** Similar al _while_, pero se garantiza que el bloque de código se ejecute al menos una vez, ya que la condición se evalúa después de la ejecución.  
   - **Sintaxis:**
     ```java
     do {
         // Bloque de código a repetir
     } while (condición);
     ```
   - **Características:**  
     Debido a la evaluación posterior de la condición, el bloque se ejecuta siempre al menos una vez, lo cual es útil cuando se necesita que la acción se realice sin importar la condición inicial.

3. **Bucle _for_:**  
   - **Concepto:** Combina la inicialización de la variable de control, la condición de continuación y la actualización de la variable en una única línea.  
   - **Sintaxis:**
     ```java
     for (inicialización; condición; actualización) {
         // Bloque de código a repetir
     }
     ```
   - **Características:**  
     Es muy útil cuando se conoce de antemano el número de iteraciones o cuando se requiere una sintaxis compacta para la repetición.  
     Por ejemplo, se puede inicializar una variable, comprobar que ésta sea menor o igual que un valor final y, luego, incrementarla en cada iteración.

4. **Bucle _for-each_:**  
   - **Concepto:** Es una variante del _for_ diseñada para recorrer arreglos o colecciones sin gestionar manualmente los índices.  
   - **Sintaxis:**
     ```java
     for (Tipo elemento : colección) {
         // Uso de "elemento" en cada iteración
     }
     ```
   - **Características:**  
     Facilita la lectura y el manejo de estructuras de datos, especialmente cuando no es necesario modificar el índice o la colección durante la iteración.

## EJEMPLOS

## Ejemplo 1: Imprimir Números del 1 al 10 con Bucle _while_

**Descripción:**  
Se utiliza un bucle _while_ para imprimir en la consola los números del 1 al 10.

```java
public class WhileEjemplo1 {
    public static void main(String[] args) {
        int contador = 1;  // Inicializamos el contador en 1

        while (contador <= 10) {  // Mientras contador sea menor o igual que 10
            System.out.println("Número: " + contador);
            contador++;  // Incrementamos el contador en 1
        }
    }
}
```



## Ejemplo 2: Imprimir Números del 1 al 10 con Bucle _do-while_

**Descripción:**  
Se utiliza un bucle _do-while_ para imprimir en la consola los números del 1 al 10, asegurando que el bloque se ejecute al menos una vez.

```java
public class DoWhileEjemplo1 {
    public static void main(String[] args) {
        int contador = 1;  // Inicializamos el contador

        do {
            System.out.println("Número: " + contador);
            contador++;  // Incrementamos el contador
        } while (contador <= 10);  // Se evalúa la condición después de la ejecución del bloque
    }
}
```



## Ejemplo 3: Imprimir Números del 1 al 10 con Bucle _for_

**Descripción:**  
Se utiliza un bucle _for_ para imprimir en la consola los números del 1 al 10, aprovechando su sintaxis compacta.

```java
public class ForEjemplo1 {
    public static void main(String[] args) {
        // Inicialización: int i = 1; Condición: i <= 10; Incremento: i++
        for (int i = 1; i <= 10; i++) {
            System.out.println("Número: " + i);
        }
    }
}
```



## Ejemplo 4: Sumar los Números del 1 al 10 con un Bucle _for_

**Descripción:**  
Calcula la suma de los números del 1 al 10 utilizando un bucle _for_ y muestra el resultado.

```java
public class SumaFor {
    public static void main(String[] args) {
        int suma = 0;  // Variable para acumular la suma

        // Bucle for para iterar del 1 al 10
        for (int i = 1; i <= 10; i++) {
            suma += i;  // Equivalente a: suma = suma + i;
        }
        
        System.out.println("La suma de los números del 1 al 10 es: " + suma);
    }
}
```



## Ejemplo 5: Leer Números y Calcular su Suma (con Bucle _while_)

**Descripción:**  
El programa solicita al usuario que introduzca números enteros. El bucle se detiene cuando el usuario introduce el valor 0, y luego se muestra la suma de todos los números introducidos.

```java
import java.util.Scanner;

public class SumaNumerosWhile {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int suma = 0;
        int numero;

        System.out.println("Introduce números para sumarlos (introduce 0 para terminar):");
        
        // Leer números hasta que el usuario introduzca 0
        while (true) {
            System.out.print("Número: ");
            numero = sc.nextInt();
            
            if (numero == 0) {
                break;  // Sale del bucle si el número es 0
            }
            
            suma += numero;
        }
        
        System.out.println("La suma total es: " + suma);
        sc.close();
    }
}
```



## Ejemplo 6: Imprimir Elementos de un Arreglo con un Bucle _for-each_

**Descripción:**  
Se recorre un arreglo de cadenas y se imprimen sus elementos utilizando el bucle _for-each_.

```java
public class ForEachEjemplo {
    public static void main(String[] args) {
        String[] dias = {"Lunes", "Martes", "Miércoles", "Jueves", "Viernes"};
        
        // Bucle for-each para recorrer el arreglo
        for (String dia : dias) {
            System.out.println("Día: " + dia);
        }
    }
}
```

## Ejemplo 6: Diferencia entre bucle normal y bucle **for each** 
```java
public class Bucle {

        public static void main(String[] args) {
            String[] dias = {"Lunes", "Martes", "Miércoles", "Jueves", "Viernes"};

            // Bucle for-each para recorrer el arreglo

            for (String dia : dias) {
                System.out.println("Día: " + dia);

            }

            for (int i=0; i<5; i++) {
                System.out.println("El elemento " + dias[i]+" está en la posición: "+i);

            }
        }
    }

```


