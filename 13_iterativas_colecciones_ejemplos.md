## Ejemplo 1: Crear y Recorrer un ArrayList de Nombres

**Descripción:**  
Se crea un ArrayList de tipo String, se añaden algunos nombres y se recorre la lista con un bucle _for-each_ para imprimir cada elemento.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploArrayListBasico {
    public static void main(String[] args) {
        // Crear un ArrayList de cadenas
        List<String> nombres = new ArrayList<>();
        
        // Añadir elementos al ArrayList
        nombres.add("Ana");
        nombres.add("Luis");
        nombres.add("Carlos");
        nombres.add("Beatriz");
        
        // Recorrer el ArrayList con un bucle for-each e imprimir cada nombre
        System.out.println("Lista de nombres:");
        for (String nombre : nombres) {
            System.out.println(nombre);
        }
    }
}
```



## Ejemplo 2: Verificar la Existencia de un Elemento con if y ArrayList

**Descripción:**  
Se crea un ArrayList con nombres y se utiliza una estructura _if_ junto con el método `contains()` para verificar si un nombre determinado está en la lista.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploBusqueda {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>();
        nombres.add("Ana");
        nombres.add("Luis");
        nombres.add("Carlos");
        nombres.add("Beatriz");
        
        // Nombre a buscar
        String busqueda = "Carlos";
        
        // Usar if para verificar si el ArrayList contiene el nombre
        if (nombres.contains(busqueda)) {
            System.out.println(busqueda + " se encuentra en la lista.");
        } else {
            System.out.println(busqueda + " NO se encuentra en la lista.");
        }
    }
}
```



## Ejemplo 3: Filtrar Elementos Según una Condición con un Bucle y if

**Descripción:**  
Se recorre un ArrayList de números enteros y se imprime únicamente aquellos que sean mayores que un valor dado. Se utiliza un bucle _for-each_ junto con una estructura _if_.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploFiltrar {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        // Añadir algunos números al ArrayList
        numeros.add(5);
        numeros.add(12);
        numeros.add(7);
        numeros.add(20);
        numeros.add(3);
        
        // Valor de referencia para filtrar
        int umbral = 10;
        System.out.println("Números mayores que " + umbral + ":");
        
        // Recorrer la lista y usar if para filtrar
        for (int numero : numeros) {
            if (numero > umbral) {
                System.out.println(numero);
            }
        }
    }
}
```



## Ejemplo 4: Buscar y Contar Elementos que Cumplen una Condición

**Descripción:**  
Se crea un ArrayList de cadenas (nombres) y se utiliza un bucle para contar cuántos nombres comienzan con la letra "A". Se utiliza la función `startsWith()` y una estructura _if_.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploContarNombres {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>();
        nombres.add("Ana");
        nombres.add("Luis");
        nombres.add("Alberto");
        nombres.add("Beatriz");
        nombres.add("Andrea");
        
        int contador = 0;
        
        // Recorrer el ArrayList y contar nombres que empiezan con "A"
        for (String nombre : nombres) {
            if (nombre.startsWith("A")) {
                contador++;
            }
        }
        
        System.out.println("Cantidad de nombres que comienzan con 'A': " + contador);
    }
}
```



## Ejemplo 5: Eliminar Elementos que Cumplen una Condición

**Descripción:**  
Se recorre un ArrayList de números y se eliminan aquellos que sean menores o iguales a un determinado umbral. Para evitar problemas de concurrencia al eliminar elementos mientras se recorre la lista, se utiliza un bucle _while_ con un índice.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploEliminar {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        // Añadir números al ArrayList
        numeros.add(15);
        numeros.add(8);
        numeros.add(22);
        numeros.add(5);
        numeros.add(17);
        
        int umbral = 10;
        System.out.println("Lista original: " + numeros);
        
        // Usar un bucle while con índice para eliminar elementos
        int i = 0;
        while (i < numeros.size()) {
            // Si el número es menor o igual que el umbral, lo eliminamos
            if (numeros.get(i) <= umbral) {
                numeros.remove(i);
                // No incrementamos i porque al eliminar se desplaza el siguiente elemento
            } else {
                i++;
            }
        }
        
        System.out.println("Lista después de eliminar números <= " + umbral + ": " + numeros);
    }
}
```



## Ejemplo 6: Uso de ArrayList con Lectura de Datos, Bucles e if

**Descripción:**  
Se pide al usuario que ingrese nombres hasta introducir la palabra "fin". Se agregan los nombres a un ArrayList y, al finalizar, se recorre la lista para mostrar únicamente los nombres que tengan más de 3 caracteres.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class EjemploArrayListUsuario {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        List<String> nombres = new ArrayList<>();
        
        System.out.println("Introduce nombres (escribe 'fin' para terminar):");
        while (true) {
            System.out.print("Nombre: ");
            String nombre = sc.nextLine();
            
            if (nombre.equalsIgnoreCase("fin")) {
                break;
            }
            
            nombres.add(nombre);
        }
        
        System.out.println("\nNombres con más de 3 caracteres:");
        for (String nombre : nombres) {
            // Usamos if para filtrar los nombres
            if (nombre.length() > 3) {
                System.out.println(nombre);
            }
        }
        
        sc.close();
    }
}
```


