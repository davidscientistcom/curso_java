# **Arrays en Java**
Los arrays en Java son estructuras de datos que permiten almacenar múltiples valores del mismo tipo en una única variable. Se dividen en **arrays de una dimensión** y **arrays de dos dimensiones**.


## **1. Arrays de Una Dimensión**
Un **array unidimensional** es una colección de elementos del mismo tipo almacenados en una secuencia.

### **Declaración y Creación de un Array**
```java
int[] numeros = new int[5]; // Crea un array de 5 enteros
```
También se puede inicializar directamente con valores:
```java
int[] numeros = {10, 20, 30, 40, 50}; // Array con 5 valores
```

### **Acceder a los Elementos**
```java
System.out.println(numeros[0]); // Muestra el primer elemento (10)
```

### **Modificar un Elemento**
```java
numeros[2] = 100; // Cambia el tercer elemento a 100
```

### **Recorrer un Array con un Bucle**
```java
for (int i = 0; i < numeros.length; i++) {
    System.out.println(numeros[i]);
}
```

### **Ejercicio 1: Sumar Elementos de un Array**
**Problema:** Escribe un programa que sume los elementos de un array y muestre el resultado.

#### **Código en Java**
```java
public class SumaArray {
    public static void main(String[] args) {
        int[] numeros = {5, 10, 15, 20, 25};
        int suma = 0;

        for (int i = 0; i < numeros.length; i++) {
            suma += numeros[i];
        }

        System.out.println("La suma de los elementos es: " + suma);
    }
}
```


## **2. Arrays de Dos Dimensiones**
Un **array bidimensional** es una tabla con filas y columnas.

### **Declaración y Creación de un Array 2D**
```java
int[][] matriz = new int[3][3]; // Matriz de 3x3
```
También se puede inicializar con valores:
```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

### **Acceder a los Elementos**
```java
System.out.println(matriz[1][2]); // Accede al elemento de la fila 1, columna 2 (valor 6)
```

### **Modificar un Elemento**
```java
matriz[0][1] = 99; // Cambia el valor en la fila 0, columna 1
```

### **Recorrer una Matriz con Bucles Anidados**
```java
for (int i = 0; i < matriz.length; i++) {
    for (int j = 0; j < matriz[i].length; j++) {
        System.out.print(matriz[i][j] + " ");
    }
    System.out.println();
}
```

### **Ejercicio 2: Sumar Todos los Elementos de una Matriz**
**Problema:** Escribe un programa que sume todos los elementos de una matriz de 3x3.

#### **Código en Java**
```java
public class SumaMatriz {
    public static void main(String[] args) {
        int[][] matriz = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        int suma = 0;

        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                suma += matriz[i][j];
            }
        }

        System.out.println("La suma de los elementos de la matriz es: " + suma);
    }
}
```


## **Ejercicio 3: Encontrar el Mayor Elemento en un Array**
**Problema:** Escribe un programa que encuentre el número mayor dentro de un array.

#### **Código en Java**
```java
public class MayorElemento {
    public static void main(String[] args) {
        int[] numeros = {12, 34, 56, 78, 90, 23, 45};
        int mayor = numeros[0];

        for (int i = 1; i < numeros.length; i++) {
            if (numeros[i] > mayor) {
                mayor = numeros[i];
            }
        }

        System.out.println("El mayor número es: " + mayor);
    }
}
```


## **Ejercicio 4: Transponer una Matriz**
**Problema:** Escribe un programa que intercambie las filas por columnas en una matriz cuadrada.

#### **Código en Java**
```java
public class TransponerMatriz {
    public static void main(String[] args) {
        int[][] matriz = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int[][] transpuesta = new int[3][3];

        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                transpuesta[j][i] = matriz[i][j];
            }
        }

        System.out.println("Matriz transpuesta:");
        for (int i = 0; i < transpuesta.length; i++) {
            for (int j = 0; j < transpuesta[i].length; j++) {
                System.out.print(transpuesta[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```


## **Ejercicio 5: Contar Elementos Pares en un Array**
**Problema:** Escribe un programa que cuente cuántos números pares hay en un array.

#### **Código en Java**
```java
public class ContarPares {
    public static void main(String[] args) {
        int[] numeros = {4, 7, 10, 13, 16, 19, 22, 25, 28};
        int contador = 0;

        for (int num : numeros) {
            if (num % 2 == 0) {
                contador++;
            }
        }

        System.out.println("Cantidad de números pares: " + contador);
    }
}
```

# **Arrays en Java** 

Los arrays en Java son estructuras de datos que permiten almacenar múltiples valores del mismo tipo en una única variable. Se dividen en **arrays de una dimensión** y **arrays de dos dimensiones**.



## **1. Arrays de Una Dimensión**
Un **array unidimensional** es una colección de elementos del mismo tipo almacenados en una secuencia.

### **Declaración y Creación de un Array**
```java
int[] numeros = new int[5]; // Crea un array de 5 enteros con valores por defecto (0)
```
También se puede inicializar directamente con valores:
```java
int[] numeros = {10, 20, 30, 40, 50}; // Array con 5 valores
```

### **Acceder a los Elementos**
```java
System.out.println(numeros[0]); // Muestra el primer elemento (10)
```

### **Modificar un Elemento**
```java
numeros[2] = 100; // Cambia el tercer elemento a 100
```

### **Recorrer un Array con un Bucle**
```java
for (int i = 0; i < numeros.length; i++) {
    System.out.println(numeros[i]);
}
```


## **2. Insertar un Elemento en un Array (Simulación)**
Como los arrays en Java **tienen un tamaño fijo**, para "insertar" un elemento debemos:
1. Crear un **nuevo array** con un tamaño mayor.
2. Copiar los valores antiguos al nuevo array.
3. Insertar el nuevo valor en la posición deseada.

### **Ejemplo: Insertar un elemento en la posición 2**
```java
import java.util.Arrays;

public class InsertarElemento {
    public static void main(String[] args) {
        int[] numeros = {10, 20, 40, 50}; // Array original (sin espacio extra)
        int nuevoValor = 30;
        int posicion = 2; // Queremos insertar en la posición 2 (índice 2)

        // Creamos un nuevo array con un elemento más
        int[] nuevoArray = new int[numeros.length + 1];

        // Copiamos los elementos hasta la posición deseada
        for (int i = 0; i < posicion; i++) {
            nuevoArray[i] = numeros[i];
        }

        // Insertamos el nuevo elemento
        nuevoArray[posicion] = nuevoValor;

        // Copiamos el resto de los elementos
        for (int i = posicion; i < numeros.length; i++) {
            nuevoArray[i + 1] = numeros[i];
        }

        System.out.println("Array después de la inserción: " + Arrays.toString(nuevoArray));
    }
}
```

### **Salida esperada**
```
Array después de la inserción: [10, 20, 30, 40, 50]
```



## **3. Modificar un Elemento en un Array**
Para **modificar** un elemento en un array, simplemente accedemos a la posición y cambiamos su valor.

### **Ejemplo: Modificar el tercer elemento**
```java
import java.util.Arrays;

public class ModificarElemento {
    public static void main(String[] args) {
        int[] numeros = {10, 20, 30, 40, 50};

        numeros[2] = 99; // Cambiar el valor en la posición 2

        System.out.println("Array después de la modificación: " + Arrays.toString(numeros));
    }
}
```

### **Salida esperada**
```
Array después de la modificación: [10, 20, 99, 40, 50]
```



## **4. Eliminar un Elemento de un Array (Simulación)**
Como los arrays son de tamaño fijo, para **eliminar un elemento** debemos:
1. Crear un **nuevo array** con un tamaño menor.
2. Copiar los valores, omitiendo el elemento a eliminar.

### **Ejemplo: Eliminar el elemento en la posición 2**
```java
import java.util.Arrays;

public class EliminarElemento {
    public static void main(String[] args) {
        int[] numeros = {10, 20, 30, 40, 50};
        int posicion = 2; // Queremos eliminar el tercer elemento

        // Creamos un nuevo array con un tamaño menor
        int[] nuevoArray = new int[numeros.length - 1];

        // Copiamos los elementos excepto el que queremos eliminar
        for (int i = 0, j = 0; i < numeros.length; i++) {
            if (i != posicion) {
                nuevoArray[j++] = numeros[i];
            }
        }

        System.out.println("Array después de la eliminación: " + Arrays.toString(nuevoArray));
    }
}
```

### **Salida esperada**
```
Array después de la eliminación: [10, 20, 40, 50]
```



## **5. Arrays de Dos Dimensiones**
Un **array bidimensional** es una tabla con filas y columnas.

### **Declaración y Creación de un Array 2D**
```java
int[][] matriz = new int[3][3]; // Matriz de 3x3
```
También se puede inicializar con valores:
```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

### **Acceder a los Elementos**
```java
System.out.println(matriz[1][2]); // Accede al elemento de la fila 1, columna 2 (valor 6)
```

### **Modificar un Elemento**
```java
matriz[0][1] = 99; // Cambia el valor en la fila 0, columna 1
```

### **Recorrer una Matriz con Bucles Anidados**
```java
for (int i = 0; i < matriz.length; i++) {
    for (int j = 0; j < matriz[i].length; j++) {
        System.out.print(matriz[i][j] + " ");
    }
    System.out.println();
}
```



## **Ejemplo Completo: Insertar, Modificar y Eliminar en una Matriz**
```java
import java.util.Arrays;

public class OperacionesMatriz {
    public static void main(String[] args) {
        int[][] matriz = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        // Modificar un elemento
        matriz[1][1] = 99; // Cambia el elemento en fila 1, columna 1

        // Eliminar un elemento (reemplazándolo por 0)
        matriz[0][2] = 0; 

        // Imprimir la matriz modificada
        System.out.println("Matriz después de modificar y eliminar:");
        for (int i = 0; i < matriz.length; i++) {
            System.out.println(Arrays.toString(matriz[i]));
        }
    }
}
```

### **Salida esperada**
```
Matriz después de modificar y eliminar:
[1, 2, 0]
[4, 99, 6]
[7, 8, 9]
```
