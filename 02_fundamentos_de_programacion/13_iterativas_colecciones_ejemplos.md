# Funciones en Java: Aspectos Básicos y Consideraciones

En Java, todas las funciones (llamadas métodos) deben definirse dentro de una clase. Para simular funciones "libres" (como en Python o C), utilizamos métodos estáticos. Esto implica que, en el método `main` (que es estático), podemos invocar directamente otros métodos estáticos sin necesidad de crear una instancia de la clase. Sin embargo, si deseáramos llamar a métodos no estáticos, tendríamos que instanciar la clase primero.

## 1. Uso de Métodos Estáticos

El método `main` se declara como `public static void main(String[] args)`, y, por estar dentro de un contexto estático, únicamente puede llamar directamente a otros métodos estáticos. Por ejemplo:

```java
public class FuncionesEjemplo {

    // Este método es estático, por lo que se puede llamar desde main sin instanciar la clase.
    public static int sumar(int a, int b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        // Llamada directa a un método estático.
        int resultado = sumar(10, 15);
        System.out.println("La suma es: " + resultado);
    }
}
```

Si un método no es estático, para invocarlo desde `main` deberíamos crear un objeto de la clase, lo que no resulta práctico cuando lo que se desea es una función “libre”.

## 2. Modificadores de Acceso en Funciones

En Java, un método puede declararse con distintos modificadores de acceso, como `public` o `private`.  
- **`public`**: Permite que el método sea invocado desde otras clases.  
- **`private`**: Restringe el acceso al método únicamente dentro de la misma clase.

Dentro de la misma clase, incluso desde el método `main`, podemos llamar a métodos `private`. Por ejemplo:

```java
public class FuncionesEjemplo {
    
    // Método privado: solo puede usarse dentro de la clase
    private static void mostrarMensaje(String mensaje) {
        System.out.println(mensaje);
    }
    
    public static void main(String[] args) {
        // Se puede llamar a un método privado, ya que main está dentro de la misma clase.
        mostrarMensaje("Este es un mensaje privado llamado desde main.");
    }
}
```

La elección de `public` o `private` dependerá de si se espera que el método sea accesible desde fuera de la clase o se use únicamente como una función auxiliar interna.

## 3. Pasar y Devolver ArrayList en Funciones

En Java, también es posible pasar y devolver `ArrayList` como argumento y valor de retorno en un método. Esto es útil cuando se necesita manipular listas dinámicas dentro de funciones.

### **Ejemplo: Pasar un ArrayList como Parámetro**
```java
import java.util.ArrayList;

public class ManejoArrayList {
    
    // Método que imprime todos los elementos de un ArrayList
    public static void mostrarLista(ArrayList<String> lista) {
        for (String elemento : lista) {
            System.out.println(elemento);
        }
    }
    
    public static void main(String[] args) {
        ArrayList<String> nombres = new ArrayList<>();
        nombres.add("Ana");
        nombres.add("Carlos");
        nombres.add("Beatriz");
        
        System.out.println("Elementos en la lista:");
        mostrarLista(nombres);
    }
}
```

### **Ejemplo: Devolver un ArrayList desde una Función**
```java
import java.util.ArrayList;

public class GenerarArrayList {
    
    // Método que genera y devuelve un ArrayList de números enteros
    public static ArrayList<Integer> generarNumeros(int cantidad) {
        ArrayList<Integer> numeros = new ArrayList<>();
        for (int i = 1; i <= cantidad; i++) {
            numeros.add(i);
        }
        return numeros;
    }
    
    public static void main(String[] args) {
        ArrayList<Integer> listaNumeros = generarNumeros(5);
        System.out.println("Lista de números generada: " + listaNumeros);
    }
}
```