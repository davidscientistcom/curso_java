A continuación tienes **un ejercicio completo**, resuelto paso a paso, que implementa un **Gestor de Fechas de Cumpleaños** sin crear clases adicionales para los datos (todo se maneja en paralelo con `ArrayList` o arreglos). El código está todo en una sola clase con el método `main`, ya que Java requiere al menos una clase para ejecutar, pero **no** definimos clases extra (como `class Persona`).



# Ejercicio: Gestor de Cumpleaños

## Objetivo

- Almacenar los nombres y las fechas de nacimiento de distintas personas.  
- Ofrecer un menú que permita:
  1. Agregar un nuevo registro (nombre + fecha).
  2. Buscar la fecha de nacimiento a partir de un nombre.
  3. Eliminar el registro de una persona por su nombre.
  4. Listar todos los cumpleaños.
  5. Salir del programa.

## Descripción de la Solución

1. **Estructuras de Almacenamiento**  
   - Usaremos dos `ArrayList<String>`:  
     - `listaNombres` para los nombres de las personas.  
     - `listaFechas` para sus fechas de cumpleaños (en el mismo índice).
   - Así, si `listaNombres.get(i)` es `"Ana"`, entonces `listaFechas.get(i)` contiene su fecha de nacimiento.

2. **Menú Principal**  
   - Lo mostraremos dentro de un bucle `while(true)` (o similar).  
   - El usuario elige una opción del 1 al 5.  
   - Dependiendo de la opción, ejecutamos la acción correspondiente.
   - Si elige “5. Salir”, rompemos el bucle.

3. **Agregar un Cumpleaños**  
   - Se pide el nombre y la fecha de nacimiento (ej. “dd/mm/aaaa”).  
   - Insertamos el nombre en `listaNombres` y la fecha en `listaFechas`.

4. **Buscar un Cumpleaños**  
   - Se pide el nombre a buscar.  
   - Recorremos `listaNombres` con un bucle para encontrar una coincidencia.  
   - Si `listaNombres.get(i).equals(nombreBuscado)`, mostramos `listaFechas.get(i)`.  
   - Si no lo encontramos, mostramos un mensaje de error.

5. **Eliminar un Cumpleaños**  
   - Similar a la búsqueda.  
   - Si encontramos el índice `i` donde está el nombre, hacemos `listaNombres.remove(i)` y `listaFechas.remove(i)`.  
   - Confirmamos que se ha eliminado.  
   - Si no existe, mostramos un mensaje correspondiente.

6. **Listar Todos**  
   - Recorremos `listaNombres` y `listaFechas` en un `for`, mostrando `"nombre - fecha"` para cada índice.

7. **Validaciones Mínimas**  
   - Si se introduce una opción de menú no válida, lo indicamos y volvemos a mostrar el menú.  
   - Podemos (opcionalmente) controlar que no se repita un nombre, etc. (no incluido en este ejemplo, pero se puede añadir).



## Código Completo Explicado

A continuación, un posible ejemplo **completamente funcional**. Incluye comentarios en el código para explicar cada paso.

```java
import java.util.ArrayList;
import java.util.Scanner;

public class GestorCumpleanios {
    public static void main(String[] args) {
        // 1. Creamos nuestras estructuras de almacenamiento
        ArrayList<String> listaNombres = new ArrayList<>();
        ArrayList<String> listaFechas = new ArrayList<>();

        // 2. Creamos un objeto Scanner para leer desde consola
        Scanner sc = new Scanner(System.in);

        while (true) {
            // 3. Mostramos el menú principal
            System.out.println("\n===== GESTOR DE CUMPLEAÑOS =====");
            System.out.println("1. Agregar Cumpleaños");
            System.out.println("2. Buscar Cumpleaños");
            System.out.println("3. Eliminar Cumpleaños");
            System.out.println("4. Listar Cumpleaños");
            System.out.println("5. Salir");
            System.out.print("Elige una opción: ");

            // 4. Leemos la opción elegida
            int opcion = 0;
            try {
                opcion = Integer.parseInt(sc.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("Opción inválida. Debes introducir un número.");
                continue; // Volvemos al menú
            }

            // 5. Ejecutamos la acción según la opción
            switch (opcion) {
                case 1:
                    // Opción 1: Agregar cumpleaños
                    System.out.print("Introduce el nombre: ");
                    String nombre = sc.nextLine();
                    System.out.print("Introduce la fecha de nacimiento (dd/mm/aaaa): ");
                    String fecha = sc.nextLine();

                    listaNombres.add(nombre);
                    listaFechas.add(fecha);
                    System.out.println(">>> Cumpleaños añadido con éxito <<<");
                    break;

                case 2:
                    // Opción 2: Buscar cumpleaños
                    System.out.print("Introduce el nombre a buscar: ");
                    String nombreBuscado = sc.nextLine();
                    
                    // Variable para saber si hemos encontrado el nombre
                    boolean encontrado = false;
                    
                    // Recorremos la lista en busca del nombre
                    for (int i = 0; i < listaNombres.size(); i++) {
                        if (listaNombres.get(i).equalsIgnoreCase(nombreBuscado)) {
                            // Si coincide, mostramos la fecha
                            System.out.println("La fecha de nacimiento de " + nombreBuscado
                                    + " es: " + listaFechas.get(i));
                            encontrado = true;
                            break;
                        }
                    }
                    
                    if (!encontrado) {
                        System.out.println("No se ha encontrado un cumpleaños para la persona: " + nombreBuscado);
                    }
                    break;

                case 3:
                    // Opción 3: Eliminar cumpleaños
                    System.out.print("Introduce el nombre cuyo registro deseas eliminar: ");
                    String nombreEliminar = sc.nextLine();
                    boolean eliminado = false;
                    
                    for (int i = 0; i < listaNombres.size(); i++) {
                        if (listaNombres.get(i).equalsIgnoreCase(nombreEliminar)) {
                            listaNombres.remove(i);
                            listaFechas.remove(i);
                            System.out.println(">>> Registro eliminado con éxito <<<");
                            eliminado = true;
                            break;
                        }
                    }
                    
                    if (!eliminado) {
                        System.out.println("No se encontró registro con ese nombre para eliminar.");
                    }
                    break;

                case 4:
                    // Opción 4: Listar cumpleaños
                    if (listaNombres.isEmpty()) {
                        System.out.println("No hay registros de cumpleaños.");
                    } else {
                        System.out.println("Lista de Cumpleaños:");
                        for (int i = 0; i < listaNombres.size(); i++) {
                            System.out.println("- " + listaNombres.get(i)
                                    + " : " + listaFechas.get(i));
                        }
                    }
                    break;

                case 5:
                    // Opción 5: Salir
                    System.out.println("Saliendo del programa...");
                    sc.close();
                    return; // Finaliza el main

                default:
                    System.out.println("Opción no válida, por favor selecciona entre 1 y 5.");
            }
        }
    }
}
```

### Explicación Paso a Paso

1. **Importaciones**  
   ```java
   import java.util.ArrayList;
   import java.util.Scanner;
   ```
   - Importamos `ArrayList` para poder usar listas dinámicas.  
   - Importamos `Scanner` para leer desde la consola.

2. **Declaración de la clase principal**  
   ```java
   public class GestorCumpleanios {
       public static void main(String[] args) {
           // ...
       }
   }
   ```
   - En Java, necesitamos al menos una clase para ejecutar el programa.  
   - No creamos clases para guardar la información de cumpleaños; todo va en listas.

3. **Creación de estructuras de datos**  
   ```java
   ArrayList<String> listaNombres = new ArrayList<>();
   ArrayList<String> listaFechas = new ArrayList<>();
   ```
   - `listaNombres` guardará los nombres de las personas.  
   - `listaFechas` guardará las fechas de nacimiento en el mismo índice correspondiente.

4. **Creación de `Scanner`**  
   ```java
   Scanner sc = new Scanner(System.in);
   ```
   - Con esto leeremos la entrada de usuario por consola.

5. **Bucle para el Menú Principal**  
   ```java
   while (true) {
       // Mostrar menú
       // Leer opción
       // Procesar la opción con un switch
   }
   ```
   - Este `while(true)` permite que el menú se repita hasta que elijamos la opción de salir.

6. **Lectura de la opción**  
   ```java
   int opcion = 0;
   try {
       opcion = Integer.parseInt(sc.nextLine());
   } catch (NumberFormatException e) {
       System.out.println("Opción inválida. Debes introducir un número.");
       continue;
   }
   ```
   - Leemos la opción como texto y la convertimos a entero.  
   - Si el usuario escribe algo que no sea un número, capturamos la excepción y volvemos a mostrar el menú.

7. **`switch` para procesar la opción**  
   ```java
   switch (opcion) {
       case 1: // Agregar cumpleaños
           ...
           break;
       case 2: // Buscar
           ...
           break;
       case 3: // Eliminar
           ...
           break;
       case 4: // Listar
           ...
           break;
       case 5: // Salir
           ...
           return;
       default:
           System.out.println("Opción no válida...");
   }
   ```
   - Cada caso corresponde a una de las acciones de nuestro menú.

8. **Agregar cumpleaños (case 1)**  
   ```java
   System.out.print("Introduce el nombre: ");
   String nombre = sc.nextLine();
   System.out.print("Introduce la fecha de nacimiento (dd/mm/aaaa): ");
   String fecha = sc.nextLine();

   listaNombres.add(nombre);
   listaFechas.add(fecha);
   System.out.println(">>> Cumpleaños añadido con éxito <<<");
   ```
   - Pedimos nombre y fecha al usuario y los añadimos a las listas.

9. **Buscar cumpleaños (case 2)**  
   ```java
   System.out.print("Introduce el nombre a buscar: ");
   String nombreBuscado = sc.nextLine();
   
   boolean encontrado = false;
   for (int i = 0; i < listaNombres.size(); i++) {
       if (listaNombres.get(i).equalsIgnoreCase(nombreBuscado)) {
           System.out.println("La fecha de nacimiento de " + nombreBuscado
                   + " es: " + listaFechas.get(i));
           encontrado = true;
           break;
       }
   }
   if (!encontrado) {
       System.out.println("No se ha encontrado un cumpleaños para la persona: " + nombreBuscado);
   }
   ```
   - Recorremos `listaNombres`.  
   - Si coincide el nombre (ignorando mayúsculas/minúsculas con `equalsIgnoreCase`), mostramos la fecha correspondiente.  
   - Si terminamos el bucle sin encontrar nada, indicamos que no existe.

10. **Eliminar cumpleaños (case 3)**  
    ```java
    System.out.print("Introduce el nombre cuyo registro deseas eliminar: ");
    String nombreEliminar = sc.nextLine();
    boolean eliminado = false;
    
    for (int i = 0; i < listaNombres.size(); i++) {
        if (listaNombres.get(i).equalsIgnoreCase(nombreEliminar)) {
            listaNombres.remove(i);
            listaFechas.remove(i);
            System.out.println(">>> Registro eliminado con éxito <<<");
            eliminado = true;
            break;
        }
    }
    if (!eliminado) {
        System.out.println("No se encontró registro con ese nombre para eliminar.");
    }
    ```
    - Volvemos a buscar el nombre en el `ArrayList`.  
    - Si lo encontramos, usamos `remove(i)` en ambas listas para eliminarlo.  
    - Mostramos mensaje de confirmación o de error si no existe.

11. **Listar todos los cumpleaños (case 4)**  
    ```java
    if (listaNombres.isEmpty()) {
        System.out.println("No hay registros de cumpleaños.");
    } else {
        System.out.println("Lista de Cumpleaños:");
        for (int i = 0; i < listaNombres.size(); i++) {
            System.out.println("- " + listaNombres.get(i)
                    + " : " + listaFechas.get(i));
        }
    }
    ```
    - Comprobamos si la lista está vacía.  
    - Si no lo está, mostramos todos los elementos emparejados por índice.

12. **Salir (case 5)**  
    ```java
    System.out.println("Saliendo del programa...");
    sc.close();
    return;
    ```
    - Cerramos el `Scanner` y finalizamos el `main` para salir del programa.



# Ejemplo de Ejecución

Imaginemos una posible interacción (resumida):

```
===== GESTOR DE CUMPLEAÑOS =====
1. Agregar Cumpleaños
2. Buscar Cumpleaños
3. Eliminar Cumpleaños
4. Listar Cumpleaños
5. Salir
Elige una opción: 1

Introduce el nombre: Ana
Introduce la fecha de nacimiento (dd/mm/aaaa): 12/10/1995
>>> Cumpleaños añadido con éxito <<<

===== GESTOR DE CUMPLEAÑOS =====
1. Agregar Cumpleaños
2. Buscar Cumpleaños
3. Eliminar Cumpleaños
4. Listar Cumpleaños
5. Salir
Elige una opción: 4

Lista de Cumpleaños:
- Ana : 12/10/1995

===== GESTOR DE CUMPLEAÑOS =====
1. Agregar Cumpleaños
2. Buscar Cumpleaños
3. Eliminar Cumpleaños
4. Listar Cumpleaños
5. Salir
Elige una opción: 2

Introduce el nombre a buscar: Ana
La fecha de nacimiento de Ana es: 12/10/1995

===== GESTOR DE CUMPLEAÑOS =====
...
Elige una opción: 5
Saliendo del programa...
```


