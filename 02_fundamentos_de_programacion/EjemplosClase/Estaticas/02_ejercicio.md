# Teoría de las Colecciones en Java

Las **colecciones** en Java son estructuras de datos que permiten almacenar, gestionar y manipular grupos de objetos de manera eficiente y flexible. Java proporciona el **Framework de Colecciones** (Java Collections Framework, JCF), que está diseñado para manejar distintos tipos de agrupaciones de objetos (listas, conjuntos, mapas, colas, etc.) y permite realizar operaciones como inserción, eliminación, búsqueda y recorrido de elementos.

A continuación se explican las interfaces principales y sus implementaciones más comunes, con ejemplos prácticos inspirados en situaciones reales.


## 1. Interfaz Collection

Es la interfaz base para la mayoría de las colecciones. Define operaciones generales como:
- `add(element)`: añadir un elemento.
- `remove(element)`: eliminar un elemento.
- `contains(element)`: verificar si existe un elemento.
- `size()`: conocer el número de elementos.

Todas las colecciones como `List`, `Set` o `Queue` heredan de esta interfaz.

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
        List<String> pacientes = new LinkedList<>();
        pacientes.add("Ana");
        pacientes.add("Carlos");
        pacientes.add("Luis");

        System.out.println("Pacientes en espera:");
        for (String nombre : pacientes) {
            System.out.println(nombre);
        }

        pacientes.remove("Carlos"); // El paciente es atendido
        System.out.println("Después de atender a Carlos:");
        System.out.println(pacientes);
    }
}
```

## 3. Set: Conjuntos sin elementos duplicados

Un **Set** es una colección que no permite duplicados y no tiene acceso por índice.

### 3.1 HashSet

**Cuándo usarlo:** Cuando necesitas almacenar elementos únicos sin importar el orden.

**Ejemplo real:** Lista de DNI registrados en un sistema.

```java
import java.util.HashSet;
import java.util.Set;

public class RegistroDNI {
    public static void main(String[] args) {
        Set<String> dniRegistrados = new HashSet<>();
        dniRegistrados.add("12345678A");
        dniRegistrados.add("87654321B");
        dniRegistrados.add("12345678A"); // No se inserta

        System.out.println("DNIs registrados:");
        for (String dni : dniRegistrados) {
            System.out.println(dni);
        }
    }
}
```



### 3.2 TreeSet

**Cuándo usarlo:** Cuando necesitas elementos únicos ordenados (alfabética o numéricamente).

**Ejemplo real:** Lista de ciudades visitadas en orden alfabético.

```java
import java.util.Set;
import java.util.TreeSet;

public class CiudadesVisitadas {
    public static void main(String[] args) {
        Set<String> ciudades = new TreeSet<>();
        ciudades.add("Madrid");
        ciudades.add("Barcelona");
        ciudades.add("Valencia");
        ciudades.add("Sevilla");

        System.out.println("Ciudades visitadas (ordenadas):");
        for (String ciudad : ciudades) {
            System.out.println(ciudad);
        }
    }
}
```

## 4. Map: Pares clave-valor

Un **Map** no hereda de `Collection`, pero forma parte del JCF. Almacena pares `clave -> valor` y no permite claves duplicadas.

### 4.1 HashMap

**Cuándo usarlo:** Cuando necesitas una estructura rápida para buscar valores por clave, sin importar el orden.

**Ejemplo real:** Agenda de teléfonos (clave = nombre, valor = teléfono).

```java
import java.util.HashMap;
import java.util.Map;

public class AgendaTelefonica {
    public static void main(String[] args) {
        Map<String, String> agenda = new HashMap<>();
        agenda.put("Ana", "654321000");
        agenda.put("Luis", "612345678");
        agenda.put("Carlos", "698745632");

        System.out.println("Teléfono de Luis: " + agenda.get("Luis"));

        System.out.println("Listado completo:");
        for (Map.Entry<String, String> entrada : agenda.entrySet()) {
            System.out.println(entrada.getKey() + " -> " + entrada.getValue());
        }
    }
}
```



### 4.2 TreeMap

**Cuándo usarlo:** Cuando necesitas mantener las claves ordenadas.

**Ejemplo real:** Notas de estudiantes (clave = ID estudiante, valor = nota), ordenadas por ID.

```java
import java.util.Map;
import java.util.TreeMap;

public class NotasEstudiantes {
    public static void main(String[] args) {
        Map<Integer, Double> notas = new TreeMap<>();
        notas.put(102, 8.5);
        notas.put(101, 9.0);
        notas.put(103, 7.2);

        System.out.println("Notas ordenadas por ID:");
        for (Map.Entry<Integer, Double> entrada : notas.entrySet()) {
            System.out.println("ID: " + entrada.getKey() + ", Nota: " + entrada.getValue());
        }
    }
}
```



## Conclusión

El **Java Collections Framework** permite resolver una gran variedad de problemas de programación de forma eficiente. Elegir la colección adecuada depende del contexto:

- Usa `ArrayList` para accesos rápidos por índice.
- Usa `LinkedList` si harás muchas inserciones/borrados.
- Usa `HashSet` cuando necesites evitar duplicados.
- Usa `TreeSet` para mantener orden.
- Usa `HashMap` si quieres asociar claves y valores sin orden.
- Usa `TreeMap` si quieres mantener las claves ordenadas.

Los ejemplos presentados muestran aplicaciones reales y cotidianas que pueden servir como base para comprender cómo y cuándo utilizar cada colección en tus programas Java.

