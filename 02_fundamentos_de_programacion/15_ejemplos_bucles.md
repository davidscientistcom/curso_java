<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

## Ejemplo 1: Imprimir Números del 1 al 10 con Bucle _while_

**Descripción:**  
Utilizamos un bucle _while_ para imprimir en la consola los números del 1 al 10.

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

*Explicación:*  
Se declara la variable `contador` y se establece que mientras sea menor o igual que 10, se imprima su valor. Al final de cada iteración se incrementa en 1 para evitar bucles infinitos.



## Ejemplo 2: Imprimir Números del 1 al 10 con Bucle _do-while_

**Descripción:**  
Usamos un bucle _do-while_ para hacer lo mismo que en el ejemplo anterior, garantizando que el bloque se ejecute al menos una vez.

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

*Explicación:*  
El bloque del _do-while_ se ejecuta primero y luego se comprueba la condición. Así, se garantiza que aunque la condición inicial no se cumpla, el código se ejecuta al menos una vez.



## Ejemplo 3: Imprimir Números del 1 al 10 con Bucle _for_

**Descripción:**  
El bucle _for_ combina inicialización, condición y actualización en una única línea. En este ejemplo se imprime en la consola los números del 1 al 10.

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

*Explicación:*  
El bucle _for_ es especialmente útil cuando se conoce el número de iteraciones de antemano. Aquí se inicializa la variable `i` en 1, se verifica la condición `i <= 10` y se incrementa `i` al final de cada iteración.



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

*Explicación:*  
Se utiliza un bucle _for_ para recorrer los números del 1 al 10 y se acumula la suma en la variable `suma`. Al finalizar, se imprime el resultado.



## Ejemplo 5: Leer Números y Calcular su Suma (con Bucle _while_)

**Descripción:**  
El programa solicita al usuario que introduzca números enteros. La lectura se realiza en un bucle _while_ que se detiene cuando el usuario introduce el valor 0. Finalmente, se muestra la suma de todos los números introducidos.

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

*Explicación:*  
Se utiliza un bucle _while_ infinito (`while (true)`) y se interrumpe cuando se introduce 0. Se acumulan los números introducidos en la variable `suma`.



## Ejemplo 6: Imprimir Elementos de un Arreglo con un Bucle _for-each_

**Descripción:**  
Aunque no se ha explicado en detalle el bucle _for-each_, es una variante del _for_ que permite recorrer arreglos o colecciones. En este ejemplo se muestran los elementos de un arreglo de cadenas.

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

*Explicación:*  
El bucle _for-each_ recorre cada elemento del arreglo `dias` y lo imprime. Es muy útil para iterar sobre colecciones sin necesidad de gestionar índices.


