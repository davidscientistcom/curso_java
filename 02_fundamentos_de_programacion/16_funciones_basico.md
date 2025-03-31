<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

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

## 3. Retorno de Valores: ¿Una o Múltiples Salidas?

En Java, un método puede devolver **únicamente un valor**. Esto significa que la instrucción `return` solo puede devolver un único resultado. Sin embargo, ese "único" resultado puede ser una estructura de datos compleja (como un array, un objeto o una lista) que contenga múltiples valores. 

Por ejemplo, en Python podrías escribir:

```python
def datos():
    return 1, 2, 3  # Esto devuelve una tupla con tres elementos
```

En Java, deberás encapsular esos valores en una estructura, por ejemplo, utilizando un array o creando una clase:

### Ejemplo usando un array:

```java
public class RetornoMultiple {
    public static int[] obtenerValores() {
        // Se devuelve un array con tres enteros.
        return new int[] {1, 2, 3};
    }
    
    public static void main(String[] args) {
        int[] resultados = obtenerValores();
        System.out.println("Valores: " + resultados[0] + ", " + resultados[1] + ", " + resultados[2]);
    }
}
```

### Ejemplo usando una clase auxiliar:

```java
// Clase para encapsular dos valores
class Par {
    public int primero;
    public int segundo;
    
    public Par(int primero, int segundo) {
        this.primero = primero;
        this.segundo = segundo;
    }
}

public class RetornoObjeto {
    public static Par calcularPar() {
        // Devuelve un objeto Par con dos valores
        return new Par(5, 10);
    }
    
    public static void main(String[] args) {
        Par resultado = calcularPar();
        System.out.println("Primer valor: " + resultado.primero);
        System.out.println("Segundo valor: " + resultado.segundo);
    }
}
```

De esta manera, aunque Java no permite devolver "varios valores" de forma directa, podemos empaquetarlos en una sola entidad.
