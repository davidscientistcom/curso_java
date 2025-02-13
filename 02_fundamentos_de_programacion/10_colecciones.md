# Teoría de las Colecciones en Java

Las colecciones son estructuras de datos que permiten almacenar y gestionar grupos de objetos de forma dinámica. Java proporciona el **Framework de Colecciones** (Java Collections Framework, JCF), que ofrece una serie de interfaces y clases que facilitan la manipulación de grupos de elementos. Entre las principales interfaces del framework se encuentran:

- **Collection:**  
  Es la raíz de la jerarquía de colecciones. Define operaciones básicas como agregar, eliminar y comprobar si contiene un elemento.

- **List:**  
  Una colección ordenada que permite elementos duplicados. Las implementaciones comunes son:
  - **ArrayList:** Basada en un array dinámico, de acceso rápido por índice.
  - **LinkedList:** Basada en una lista enlazada, adecuada para inserciones y eliminaciones frecuentes.

- **Set:**  
  Una colección que no permite elementos duplicados. Algunas implementaciones son:
  - **HashSet:** Basada en una tabla hash, sin orden garantizado.
  - **TreeSet:** Basada en un árbol binario (generalmente un árbol rojo-negro) y que almacena los elementos en orden natural o según un comparador.

- **Map:**  
  No implementa la interfaz Collection, pero es parte del framework. Permite asociar claves con valores (pares clave-valor). Ejemplos:
  - **HashMap:** Basada en una tabla hash, sin orden específico.
  - **TreeMap:** Implementa un árbol binario y ordena las claves de forma natural o mediante un comparador.

El Framework de Colecciones proporciona métodos comunes para agregar, eliminar, buscar y recorrer los elementos de la colección. Además, estas estructuras son inmutables o modificables según la implementación y permiten utilizar genéricos para garantizar la seguridad en tiempo de compilación.



# Ejemplos Prácticos de Colecciones en Java

A continuación se muestran ejemplos prácticos organizados de lo más sencillo a lo más complejo.



## Ejemplo 1: Uso de ArrayList

**Descripción:**  
Se crea una lista de cadenas (por ejemplo, nombres de frutas), se añaden algunos elementos, se recorre la lista e imprime cada elemento.

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploArrayList {
    public static void main(String[] args) {
        // Crear una lista de tipo String
        List<String> frutas = new ArrayList<>();
        
        // Agregar elementos a la lista
        frutas.add("Manzana");
        frutas.add("Banana");
        frutas.add("Naranja");
        frutas.add("Kiwi");
        
        // Recorrer la lista usando un bucle for-each e imprimir los elementos
        System.out.println("Lista de frutas:");
        for (String fruta : frutas) {
            System.out.println(fruta);
        }
        
        // Mostrar el tamaño de la lista
        System.out.println("Número de frutas: " + frutas.size());
    }
}
```



## Ejemplo 2: Uso de LinkedList

**Descripción:**  
Se utiliza una LinkedList para almacenar una serie de números enteros. Se muestran operaciones de adición, eliminación y recorrido.

```java
import java.util.LinkedList;
import java.util.List;

public class EjemploLinkedList {
    public static void main(String[] args) {
        // Crear una LinkedList de tipo Integer
        List<Integer> numeros = new LinkedList<>();
        
        // Agregar elementos a la lista
        numeros.add(10);
        numeros.add(20);
        numeros.add(30);
        numeros.add(40);
        
        // Recorrer la lista e imprimir cada número
        System.out.println("Contenido de la LinkedList:");
        for (int num : numeros) {
            System.out.println(num);
        }
        
        // Eliminar un elemento (por ejemplo, el número 20)
        numeros.remove(Integer.valueOf(20));
        System.out.println("Después de eliminar el número 20:");
        System.out.println(numeros);
    }
}
```



## Ejemplo 3: Uso de HashSet

**Descripción:**  
Se crea un HashSet para almacenar números enteros sin duplicados. Se añade una serie de números, incluyendo duplicados, y se recorre el conjunto.

```java
import java.util.HashSet;
import java.util.Set;

public class EjemploHashSet {
    public static void main(String[] args) {
        // Crear un HashSet de tipo Integer
        Set<Integer> numeros = new HashSet<>();
        
        // Agregar elementos a la colección (los duplicados se ignoran)
        numeros.add(10);
        numeros.add(20);
        numeros.add(30);
        numeros.add(20); // Este duplicado no se añadirá
        
        // Recorrer el HashSet e imprimir los elementos
        System.out.println("Contenido del HashSet:");
        for (int num : numeros) {
            System.out.println(num);
        }
    }
}
```



## Ejemplo 4: Uso de TreeSet

**Descripción:**  
Se utiliza un TreeSet para almacenar cadenas y ordenarlas de forma natural (alfabéticamente).

```java
import java.util.Set;
import java.util.TreeSet;

public class EjemploTreeSet {
    public static void main(String[] args) {
        // Crear un TreeSet de tipo String
        Set<String> nombres = new TreeSet<>();
        
        // Agregar elementos a la colección
        nombres.add("Carlos");
        nombres.add("Ana");
        nombres.add("Beatriz");
        nombres.add("David");
        
        // Recorrer el TreeSet e imprimir los elementos (ordenados alfabéticamente)
        System.out.println("Nombres en orden alfabético:");
        for (String nombre : nombres) {
            System.out.println(nombre);
        }
    }
}
```



## Ejemplo 5: Uso de HashMap

**Descripción:**  
Se crea un HashMap para asociar claves (por ejemplo, códigos de identificación) a valores (nombres de personas). Se muestran operaciones de inserción, búsqueda y recorrido.

```java
import java.util.HashMap;
import java.util.Map;

public class EjemploHashMap {
    public static void main(String[] args) {
        // Crear un HashMap donde la clave es String y el valor también es String
        Map<String, String> personas = new HashMap<>();
        
        // Agregar pares clave-valor al mapa
        personas.put("001", "Ana");
        personas.put("002", "Carlos");
        personas.put("003", "Beatriz");
        personas.put("004", "David");
        
        // Buscar un valor a partir de una clave
        String nombre = personas.get("002");
        System.out.println("La persona con código 002 es: " + nombre);
        
        // Recorrer el HashMap y mostrar todas las entradas
        System.out.println("Listado completo de personas:");
        for (Map.Entry<String, String> entrada : personas.entrySet()) {
            System.out.println("Código: " + entrada.getKey() + ", Nombre: " + entrada.getValue());
        }
    }
}
```



## Ejemplo 6: Uso de TreeMap

**Descripción:**  
Se utiliza un TreeMap para almacenar claves y valores, lo que permite que las claves se mantengan en orden natural.

```java
import java.util.Map;
import java.util.TreeMap;

public class EjemploTreeMap {
    public static void main(String[] args) {
        // Crear un TreeMap de tipo <Integer, String>
        Map<Integer, String> estudiantes = new TreeMap<>();
        
        // Agregar pares clave-valor
        estudiantes.put(3, "María");
        estudiantes.put(1, "Juan");
        estudiantes.put(2, "Luis");
        
        // Recorrer el TreeMap e imprimir los elementos (ordenados por clave)
        System.out.println("Estudiantes ordenados por clave:");
        for (Map.Entry<Integer, String> entrada : estudiantes.entrySet()) {
            System.out.println("Clave: " + entrada.getKey() + ", Nombre: " + entrada.getValue());
        }
    }
}
```
