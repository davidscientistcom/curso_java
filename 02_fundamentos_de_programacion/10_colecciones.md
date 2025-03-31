<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

# Teoría de las Colecciones en Java

Las **colecciones** en Java son estructuras de datos que permiten almacenar, gestionar y manipular grupos de objetos de manera eficiente y flexible. Java proporciona el **Framework de Colecciones** (Java Collections Framework, JCF), que está diseñado para manejar distintos tipos de agrupaciones de objetos (listas, conjuntos, mapas, colas, etc.) y permite realizar operaciones como inserción, eliminación, búsqueda y recorrido de elementos.

A continuación se explican las interfaces principales y sus implementaciones más comunes, con ejemplos prácticos inspirados en situaciones reales y ampliados con operaciones frecuentes.



## 1. Interfaz Collection

Es la interfaz base para la mayoría de las colecciones. Define operaciones generales como:
- `add(element)`: añadir un elemento.
- `remove(element)`: eliminar un elemento.
- `contains(element)`: verificar si existe un elemento.
- `size()`: conocer el número de elementos.
- `isEmpty()`: verificar si está vacía.
- `clear()`: vaciar la colección.



## 2. List: Colecciones ordenadas y que permiten duplicados

Una **List** mantiene el orden de inserción y permite elementos duplicados. Se accede a los elementos por índice, como si fuera un array, pero con tamaño dinámico.

### 2.1 ArrayList

**Cuándo usarlo:** Cuando necesitas acceder frecuentemente a los elementos por su posición (por índice), y las inserciones y eliminaciones no son muy frecuentes.

**Ejemplo real:** Lista de productos en un carrito de compras.

```java
import java.util.ArrayList;
import java.util.List;

public class CarritoCompra {
    public static void main(String[] args) {
        List<String> carrito = new ArrayList<>();
        carrito.add("Pan");
        carrito.add("Leche");
        carrito.add("Huevos");
        carrito.add("Leche"); // Producto duplicado

        System.out.println("Productos en el carrito:");
        for (String producto : carrito) {
            System.out.println(producto);
        }

        // Buscar un producto
        System.out.println("¿El carrito contiene Leche? " + carrito.contains("Leche"));

        // Eliminar un producto
        carrito.remove("Leche"); // Elimina la primera ocurrencia
        System.out.println("Carrito tras eliminar una Leche:");
        System.out.println(carrito);

        // Vaciar el carrito
        carrito.clear();
        System.out.println("¿Carrito vacío? " + carrito.isEmpty());
    }
}
```



### 2.2 LinkedList

**Cuándo usarlo:** Cuando necesitas insertar o eliminar elementos frecuentemente en cualquier posición de la lista.

**Ejemplo real:** Cola de pacientes en una sala de espera.

```java
import java.util.LinkedList;
import java.util.List;

public class SalaDeEspera {
    public static void main(String[] args) {
        LinkedList<String> pacientes = new LinkedList<>();
        pacientes.add("Ana");
        pacientes.add("Carlos");
        pacientes.add("Luis");

        // Insertar al inicio
        pacientes.addFirst("Sofía");

        // Insertar al final
        pacientes.addLast("Pedro");

        System.out.println("Pacientes en espera:");
        System.out.println(pacientes);

        // Atender al primer paciente (eliminar al principio)
        String atendido = pacientes.removeFirst();
        System.out.println("Paciente atendido: " + atendido);
        System.out.println("Restantes: " + pacientes);

        // Eliminar por nombre
        pacientes.remove("Carlos");
        System.out.println("Después de eliminar a Carlos: " + pacientes);
    }
}
```



## 3. Set: Conjuntos sin elementos duplicados

Un **Set** es una colección que no permite duplicados y no tiene acceso por índice.

### 3.1 HashSet

**Cuándo usarlo:** Cuando necesitas almacenar elementos únicos sin importar el orden.

**Ejemplo real:** Lista de correos electrónicos únicos para enviar una newsletter.

```java
import java.util.HashSet;
import java.util.Set;

public class Newsletter {
    public static void main(String[] args) {
        Set<String> correos = new HashSet<>();
        correos.add("ana@gmail.com");
        correos.add("luis@gmail.com");
        correos.add("ana@gmail.com"); // Duplicado ignorado

        System.out.println("Correos registrados:");
        for (String email : correos) {
            System.out.println(email);
        }

        // Comprobar si un correo está registrado
        System.out.println("¿Registrado ana@gmail.com? " + correos.contains("ana@gmail.com"));

        // Eliminar un correo
        correos.remove("luis@gmail.com");
        System.out.println("Correos tras eliminar a Luis: " + correos);
    }
}
```



### 3.2 TreeSet

**Cuándo usarlo:** Cuando necesitas elementos únicos ordenados (alfabética o numéricamente).

**Ejemplo real:** Lista de palabras clave ordenadas alfabéticamente.

```java
import java.util.Set;
import java.util.TreeSet;

public class PalabrasClave {
    public static void main(String[] args) {
        Set<String> keywords = new TreeSet<>();
        keywords.add("java");
        keywords.add("programacion");
        keywords.add("colections");
        keywords.add("arrays");

        System.out.println("Palabras clave ordenadas:");
        for (String palabra : keywords) {
            System.out.println(palabra);
        }

        // Eliminar una palabra
        keywords.remove("arrays");
        System.out.println("Después de eliminar 'arrays': " + keywords);
    }
}
```



## 4. Map: Pares clave-valor

Un **Map** no hereda de `Collection`, pero forma parte del JCF. Almacena pares `clave -> valor` y no permite claves duplicadas.

### 4.1 HashMap

**Cuándo usarlo:** Cuando necesitas una estructura rápida para buscar valores por clave, sin importar el orden.

**Ejemplo real:** Diccionario de términos (clave = palabra, valor = definición).

```java
import java.util.HashMap;
import java.util.Map;

public class Diccionario {
    public static void main(String[] args) {
        Map<String, String> definiciones = new HashMap<>();
        definiciones.put("Array", "Estructura de datos secuencial");
        definiciones.put("HashMap", "Estructura clave-valor sin orden");

        // Buscar definición
        System.out.println("Definición de Array: " + definiciones.get("Array"));

        // Eliminar una entrada
        definiciones.remove("Array");
        System.out.println("Diccionario tras eliminar 'Array': " + definiciones);

        // Recorrer todas las entradas
        for (Map.Entry<String, String> entry : definiciones.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```



### 4.2 TreeMap

**Cuándo usarlo:** Cuando necesitas mantener las claves ordenadas.

**Ejemplo real:** Agenda de clases (clave = hora, valor = asignatura).

```java
import java.util.Map;
import java.util.TreeMap;

public class AgendaClases {
    public static void main(String[] args) {
        Map<String, String> horario = new TreeMap<>();
        horario.put("08:00", "Matemáticas");
        horario.put("10:00", "Programación");
        horario.put("09:00", "Inglés");

        // Mostrar clases ordenadas por hora
        System.out.println("Horario:");
        for (Map.Entry<String, String> clase : horario.entrySet()) {
            System.out.println(clase.getKey() + " - " + clase.getValue());
        }

        // Buscar una clase
        System.out.println("Clase a las 09:00: " + horario.get("09:00"));

        // Eliminar una clase
        horario.remove("10:00");
        System.out.println("Horario actualizado: " + horario);
    }
}
```

- Usa `ArrayList` para accesos rápidos por índice y cuando el orden importa.
- Usa `LinkedList` si harás muchas inserciones/borrados intermedios.
- Usa `HashSet` para eliminar duplicados y verificar existencia rápida.
- Usa `TreeSet` para mantener elementos únicos ordenados.
- Usa `HashMap` si quieres asociar claves y valores sin preocuparte del orden.
- Usa `TreeMap` para mantener las claves en orden natural o con un comparador.

v# Teoría de las Colecciones en Java

Las **colecciones** en Java son estructuras de datos que permiten almacenar, gestionar y manipular grupos de objetos de manera eficiente y flexible. Java proporciona el **Framework de Colecciones** (Java Collections Framework, JCF), que está diseñado para manejar distintos tipos de agrupaciones de objetos (listas, conjuntos, mapas, colas, etc.) y permite realizar operaciones como inserción, eliminación, búsqueda y recorrido de elementos.



## 5. Ejemplos de uso en problemas reales

A continuación, se presentan situaciones concretas de problemas del mundo real y se argumenta qué colección es la más adecuada y por qué.

### Ejemplo 1: Registro de acceso de usuarios por orden de llegada

**Problema:** Se quiere almacenar el orden en el que los usuarios acceden a una página web para luego analizar el flujo de navegación.

**Colección recomendada:** `LinkedList`

**Razón:** Permite insertar rápidamente al final y recorrer en orden de llegada.

```java
LinkedList<String> accesos = new LinkedList<>();
accesos.add("usuario1");
accesos.add("usuario2");
accesos.add("usuario3");
System.out.println("Último usuario en llegar: " + accesos.getLast());
```



### Ejemplo 2: Autocompletado de términos en un buscador

**Problema:** Mostrar términos previamente buscados ordenados alfabéticamente, sin duplicados.

**Colección recomendada:** `TreeSet`

**Razón:** Garantiza orden natural y evita duplicados.

```java
TreeSet<String> busquedas = new TreeSet<>();
busquedas.add("java");
busquedas.add("javascript");
busquedas.add("java"); // Ignorado
System.out.println("Términos sugeridos: " + busquedas);
```



### Ejemplo 3: Gestión de inventario con códigos de producto

**Problema:** Se desea asociar cada código de producto a su descripción, y permitir búsquedas rápidas por código.

**Colección recomendada:** `HashMap`

**Razón:** Ofrece acceso rápido a través de clave y evita duplicados de clave.

```java
HashMap<String, String> inventario = new HashMap<>();
inventario.put("A101", "Taladro eléctrico");
inventario.put("A102", "Destornillador");
System.out.println("Producto A101: " + inventario.get("A101"));
```



### Ejemplo 4: Alumnos registrados en un curso (sin repetidos)

**Problema:** Evitar que un alumno se registre más de una vez.

**Colección recomendada:** `HashSet`

**Razón:** Almacena elementos únicos y permite comprobar rápidamente si ya existe.

```java
HashSet<String> alumnos = new HashSet<>();
alumnos.add("Juan Pérez");
alumnos.add("Ana Gómez");
alumnos.add("Juan Pérez"); // Ignorado
System.out.println("Total alumnos únicos: " + alumnos.size());
```



### Ejemplo 5: Encuesta donde se deben mantener las respuestas en orden

**Problema:** Recoger las respuestas en el mismo orden en el que las personas las proporcionan y permitir duplicados.

**Colección recomendada:** `ArrayList`

**Razón:** Mantiene el orden de inserción y permite duplicados.

```java
ArrayList<String> respuestas = new ArrayList<>();
respuestas.add("Sí");
respuestas.add("No");
respuestas.add("Sí");
System.out.println("Respuestas: " + respuestas);
```



### Ejemplo 6: Agenda telefónica ordenada por nombre

**Problema:** Gestionar contactos y poder acceder a ellos ordenadamente por nombre.

**Colección recomendada:** `TreeMap`

**Razón:** Ordena las claves automáticamente.

```java
TreeMap<String, String> agenda = new TreeMap<>();
agenda.put("Luis", "612345678");
agenda.put("Ana", "654321000");
agenda.put("Carlos", "698745632");
System.out.println("Agenda ordenada: " + agenda);
```


