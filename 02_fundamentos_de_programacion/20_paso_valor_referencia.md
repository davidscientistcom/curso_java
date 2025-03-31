<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

### **Paso de Parámetros en Java: Por Valor vs. Por Referencia**
En Java, todos los parámetros se **pasan por valor**, pero el comportamiento varía dependiendo de si el valor es un **tipo primitivo** o una **referencia a un objeto**. 


## **1. Paso por Valor**
Cuando pasamos un **tipo primitivo** (como `int`, `double`, `char`, etc.) a una función, se pasa una **copia** del valor. Esto significa que cualquier cambio dentro de la función **no afecta la variable original**.

### **Ejemplo 1: Paso de un Número (`int`)**
```java
public class PasoPorValor {
    public static void main(String[] args) {
        int numero = 10;
        modificarNumero(numero);
        System.out.println("Después de la función: " + numero);
    }

    public static void modificarNumero(int n) {
        n = 100; // Solo cambia la copia de la variable
        System.out.println("Dentro de la función: " + n);
    }
}
```
### **Salida Esperada**
```
Dentro de la función: 100
Después de la función: 10
```

## **2. Paso de Objetos (Referencias)**
Cuando pasamos **objetos**, lo que se pasa por valor es la **referencia** al objeto en memoria. **La variable sigue apuntando al mismo objeto**, por lo que los cambios dentro de la función **sí afectan al objeto original**.

### **Ejemplo 2: Paso de un `ArrayList`**
```java
import java.util.ArrayList;

public class PasoPorReferencia {
    public static void main(String[] args) {
        ArrayList<String> lista = new ArrayList<>();
        lista.add("Hola");

        modificarLista(lista);
        System.out.println("Después de la función: " + lista);
    }

    public static void modificarLista(ArrayList<String> l) {
        l.add("Mundo"); // Modificamos el mismo objeto
        System.out.println("Dentro de la función: " + l);
    }
}
```
### **Salida Esperada**
```
Dentro de la función: [Hola, Mundo]
Después de la función: [Hola, Mundo]
```
🔹 **Explicación:**  
- `lista` es un **objeto** de tipo `ArrayList<String>`.
- Cuando pasamos `lista` a `modificarLista`, se copia la **referencia** al objeto, no los datos.
- **Como la referencia apunta al mismo objeto en memoria**, los cambios afectan al objeto original.



## **3. Excepción: `String` No se Modifica**
En Java, los `String` son **inmutables**. Aunque se pase la referencia, no se pueden modificar sus caracteres internos.

### **Ejemplo 3: Paso de una Cadena (`String`)**
```java
public class PasoDeString {
    public static void main(String[] args) {
        String texto = "Hola";
        modificarString(texto);
        System.out.println("Después de la función: " + texto);
    }

    public static void modificarString(String s) {
        s = s + " Mundo"; // Se crea un nuevo objeto, pero no modifica el original
        System.out.println("Dentro de la función: " + s);
    }
}
```
### **Salida Esperada**
```
Dentro de la función: Hola Mundo
Después de la función: Hola
```
🔹 **Explicación:**  
- `String` es **inmutable**: cada vez que lo modificamos, se crea un nuevo objeto.
- En `modificarString`, la variable `s` apunta a un **nuevo objeto** `"Hola Mundo"`, pero la original (`texto`) **sigue apuntando a `"Hola"`**.
- **No se altera el valor original** porque `String` no se modifica directamente.



## **4. Paso por Referencia: Cómo Modificar una Cadena**
Para modificar una `String`, hay que usar un objeto **mutable**, como `StringBuilder`.

### **Ejemplo 4: Modificar un `StringBuilder`**
```java
public class PasoDeStringBuilder {
    public static void main(String[] args) {
        StringBuilder texto = new StringBuilder("Hola");
        modificarTexto(texto);
        System.out.println("Después de la función: " + texto);
    }

    public static void modificarTexto(StringBuilder sb) {
        sb.append(" Mundo"); // Modificamos el mismo objeto
        System.out.println("Dentro de la función: " + sb);
    }
}
```
### **Salida Esperada**
```
Dentro de la función: Hola Mundo
Después de la función: Hola Mundo
```
🔹 **Explicación:**  
- `StringBuilder` **sí es mutable**. Cuando le agregamos `" Mundo"`, modificamos el mismo objeto.
- Por eso, la variable original (`texto`) también cambia.



## **5. Ámbito de las Variables en Funciones**
El **ámbito** de una variable define dónde se puede usar dentro del código. Hay tres niveles principales:

### **5.1 Variables Locales**
- Se definen dentro de una función y solo existen en ella.

```java
public class AmbitoVariables {
    public static void main(String[] args) {
        int x = 10; // Variable local de main
        prueba();
        System.out.println("Valor de x en main: " + x);
    }

    public static void prueba() {
        int x = 20; // Variable local de prueba (distinta de la de main)
        System.out.println("Valor de x en prueba: " + x);
    }
}
```
### **Salida Esperada**
```
Valor de x en prueba: 20
Valor de x en main: 10
```
🔹 **Explicación:**  
- Las variables `x` en `main` y `prueba` son **independientes**. Cambiar una no afecta la otra.



### **5.2 Variables Globales (Atributos de Clase)**
- Se definen fuera de todas las funciones, dentro de una clase.
- Son accesibles desde cualquier función de la clase.

```java
public class VariableGlobal {
    static int contador = 0; // Variable global

    public static void main(String[] args) {
        incrementar();
        incrementar();
        System.out.println("Valor del contador: " + contador);
    }

    public static void incrementar() {
        contador++;
    }
}
```
### **Salida Esperada**
```
Valor del contador: 2
```
🔹 **Explicación:**  
- `contador` es **global** porque se define fuera de `main`.
- Todas las funciones pueden modificar su valor.

