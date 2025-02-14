## 1. Introducción a ArrayList

La clase `ArrayList` forma parte del framework de colecciones de Java y se utiliza para almacenar una lista dinámica de elementos. A diferencia de los arrays tradicionales, un `ArrayList` puede cambiar de tamaño dinámicamente conforme se van agregando o eliminando elementos. Está basada en un array interno y ofrece acceso aleatorio a sus elementos.

**Características principales:**

- **Dinámico:** El tamaño se ajusta automáticamente a medida que se insertan o eliminan elementos.
- **Acceso rápido:** Permite acceder a los elementos por índice de forma muy eficiente.
- **Permite duplicados:** Acepta elementos duplicados.
- **Ordenada:** Mantiene el orden de inserción de los elementos.
- **Genérica:** Utiliza generics para asegurar el tipo de datos que almacena, lo que ayuda a prevenir errores en tiempo de compilación.



## 2. Operaciones Básicas con ArrayList

### 2.1 Creación e Inicialización

Para crear un `ArrayList` es habitual utilizar el siguiente patrón:

```java
import java.util.ArrayList;
import java.util.List;

public class EjemploBasico {
    public static void main(String[] args) {
        // Declaración e inicialización de un ArrayList para almacenar cadenas
        List<String> lista = new ArrayList<>();
        
        // También es posible inicializar un ArrayList a partir de otra colección:
        // List<String> lista = new ArrayList<>(otraColeccion);
        
        // Imprimir tamaño inicial
        System.out.println("Tamaño inicial: " + lista.size());
    }
}
```

### 2.2 Agregar Elementos

Los elementos se pueden agregar al final de la lista usando el método `add()`. También se pueden insertar en una posición específica.

```java
public class AgregarElementos {
    public static void main(String[] args) {
        List<String> frutas = new ArrayList<>();
        
        // Agregar elementos al final
        frutas.add("Manzana");
        frutas.add("Banana");
        frutas.add("Cereza");
        
        // Insertar en una posición determinada (por ejemplo, en la posición 1)
        frutas.add(1, "Durazno");
        
        System.out.println("Frutas: " + frutas);
    }
}
```

### 2.3 Acceder y Modificar Elementos

Para acceder a un elemento, se utiliza el método `get(int index)`. Para modificar un elemento existente, se usa `set(int index, E element)`.

```java
public class AccederModificar {
    public static void main(String[] args) {
        List<String> ciudades = new ArrayList<>();
        ciudades.add("Madrid");
        ciudades.add("Barcelona");
        ciudades.add("Valencia");
        
        // Acceder a un elemento
        String ciudad = ciudades.get(1);  // "Barcelona"
        System.out.println("Ciudad en la posición 1: " + ciudad);
        
        // Modificar un elemento
        ciudades.set(2, "Sevilla");
        System.out.println("Ciudades modificadas: " + ciudades);
    }
}
```

### 2.4 Eliminar Elementos

Existen varias formas de eliminar elementos: por índice o por objeto.

```java
public class EliminarElementos {
    public static void main(String[] args) {
        List<String> colores = new ArrayList<>();
        colores.add("Rojo");
        colores.add("Verde");
        colores.add("Azul");
        colores.add("Verde");
        
        // Eliminar por índice: elimina "Verde" (el primero)
        colores.remove(1);
        System.out.println("Después de eliminar por índice: " + colores);
        
        // Eliminar por objeto: elimina la primera aparición de "Verde"
        colores.remove("Verde");
        System.out.println("Después de eliminar por objeto: " + colores);
    }
}
```

### 2.5 Buscar Elementos

Se pueden buscar elementos utilizando métodos como `contains()`, `indexOf()` y `lastIndexOf()`.

```java
public class BuscarElementos {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>();
        nombres.add("Ana");
        nombres.add("Luis");
        nombres.add("Carlos");
        nombres.add("Ana");
        
        // Verificar si la lista contiene "Carlos"
        boolean contieneCarlos = nombres.contains("Carlos");
        System.out.println("¿Contiene 'Carlos'? " + contieneCarlos);
        
        // Obtener el índice de la primera aparición de "Ana"
        int indiceAna = nombres.indexOf("Ana");
        System.out.println("Primera aparición de 'Ana': " + indiceAna);
        
        // Obtener el índice de la última aparición de "Ana"
        int ultimoIndiceAna = nombres.lastIndexOf("Ana");
        System.out.println("Última aparición de 'Ana': " + ultimoIndiceAna);
    }
}
```



## 3. Recorrer un ArrayList

Existen varias técnicas para recorrer un ArrayList, combinando bucles e instrucciones condicionales.

### 3.1 Con Bucle For-each

```java
public class RecorrerForEach {
    public static void main(String[] args) {
        List<String> animales = new ArrayList<>();
        animales.add("Perro");
        animales.add("Gato");
        animales.add("Loro");
        
        for (String animal : animales) {
            System.out.println("Animal: " + animal);
        }
    }
}
```

### 3.2 Con Bucle For Tradicional

Esto es útil cuando se necesita conocer el índice de cada elemento.

```java
public class RecorrerFor {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            numeros.add(i * 2);
        }
        
        for (int i = 0; i < numeros.size(); i++) {
            System.out.println("Número en la posición " + i + ": " + numeros.get(i));
        }
    }
}
```

### 3.3 Con Bucle While

```java
public class RecorrerWhile {
    public static void main(String[] args) {
        List<String> paises = new ArrayList<>();
        paises.add("España");
        paises.add("Francia");
        paises.add("Italia");
        
        int i = 0;
        while (i < paises.size()) {
            System.out.println("País: " + paises.get(i));
            i++;
        }
    }
}
```



## 4. Operaciones Avanzadas con ArrayList

### 4.1 Filtrar Elementos con Condicionales

Es común necesitar procesar solo aquellos elementos que cumplen una condición. Por ejemplo, mostrar únicamente cadenas que tengan más de 4 caracteres:

```java
public class FiltrarElementos {
    public static void main(String[] args) {
        List<String> palabras = new ArrayList<>();
        palabras.add("Sol");
        palabras.add("Luna");
        palabras.add("Estrella");
        palabras.add("Mar");
        
        System.out.println("Palabras con más de 4 caracteres:");
        for (String palabra : palabras) {
            if (palabra.length() > 4) {
                System.out.println(palabra);
            }
        }
    }
}
```

### 4.2 Ordenar un ArrayList

El ordenamiento se realiza utilizando el método `sort` de la clase `Collections` o directamente el método `sort` de `List` (a partir de Java 8).

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class OrdenarArrayList {
    public static void main(String[] args) {
        List<String> nombres = new ArrayList<>();
        nombres.add("Zoe");
        nombres.add("Ana");
        nombres.add("Luis");
        nombres.add("Carlos");
        
        // Ordenar alfabéticamente
        Collections.sort(nombres);
        System.out.println("Nombres ordenados: " + nombres);
        
        // Ordenar en orden inverso
        Collections.sort(nombres, Collections.reverseOrder());
        System.out.println("Nombres en orden inverso: " + nombres);
    }
}
```

### 4.3 Eliminar Elementos Basados en una Condición

A partir de Java 8 se puede usar el método `removeIf` para eliminar elementos que cumplan una condición, lo que simplifica la eliminación de elementos.

```java
public class EliminarConCondicion {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        numeros.add(3);
        numeros.add(7);
        numeros.add(2);
        numeros.add(9);
        numeros.add(1);
        
        // Eliminar números menores o iguales a 3
        numeros.removeIf(n -> n <= 3);
        System.out.println("Lista después de eliminar elementos <= 3: " + numeros);
    }
}
```

