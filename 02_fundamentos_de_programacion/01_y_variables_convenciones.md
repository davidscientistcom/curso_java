<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

## 1. Reglas de Convención de Nombres para Variables en Java

### 1.1. Reglas sintácticas básicas

- **Carácter inicial:**  
  Una variable debe comenzar con una letra (a–z o A–Z), el signo de dólar (`$`) o el guión bajo (`_`). **No debe comenzar con un dígito**.  
  - **Ejemplo válido:**  
    ```java
    int contador;
    String _nombre;
    double $valor;
    ```
  - **Ejemplo no válido:**  
    ```java
    int 2numero; // Incorrecto, empieza con un dígito
    ```

- **Carácter subsecuente:**  
  Después del primer carácter, se pueden usar letras, dígitos, guiones bajos o el signo de dólar.  
  - **Ejemplo:**  
    ```java
    String nombreCompleto; // Correcto: mezcla de letras y mayúsculas para separar palabras
    ```

- **Sensibilidad a mayúsculas y minúsculas:**  
  Java es sensible a las mayúsculas y minúsculas, por lo que `variable`, `Variable` y `VARIABLE` se consideran identificadores distintos.

### 1.2. Uso de la notación lowerCamelCase

- **lowerCamelCase:**  
  La convención más común para nombrar variables (ya sean locales, de instancia o parámetros) es utilizar la notación *lowerCamelCase*. Esto significa que:  
  - La primera palabra se escribe completamente en minúsculas.  
  - Cada palabra subsiguiente inicia con una letra mayúscula.
  
  **Ejemplos:**
  ```java
  int contador;             // Una sola palabra
  double precioTotal;       // Dos palabras
  String nombreCompleto;    // Tres palabras
  ```

- **No se recomienda el uso de guiones bajos o caracteres especiales**  
  Aunque técnicamente se permite el guión bajo y el signo de dólar, se reserva su uso para casos muy específicos:
  - El **guión bajo** (`_`) puede usarse, pero en la práctica se prefiere la notación lowerCamelCase.  
  - El **signo de dólar** (`$`) está reservado para código generado automáticamente o usos especiales; su uso en variables de aplicación no es recomendable.

### 1.3. Palabras reservadas y nombres significativos

- **No utilizar palabras reservadas:**  
  No se pueden utilizar palabras clave del lenguaje (por ejemplo, `class`, `int`, `public`, etc.) como nombre de variable.

- **Nombres significativos y descriptivos:**  
  El identificador debe describir el propósito o contenido de la variable.  
  - **Ejemplo correcto:**  
    ```java
    int numeroDeEstudiantes = 25;
    String mensajeBienvenida = "Hola, bienvenidos!";
    ```
  - **Ejemplo a evitar:**  
    ```java
    int n = 25;
    String msg = "Hola"; // Menos descriptivo, salvo en contextos muy reducidos o locales.
    ```



## 2. Buenas Prácticas para el Uso de Variables en Java

### 2.1. Consistencia y legibilidad

- **Usa nombres claros y consistentes:**  
  Los nombres de las variables deben reflejar su propósito. Por ejemplo, si la variable almacena la cantidad de usuarios conectados, es preferible `numeroUsuariosConectados` que simplemente `num` o `x`.

- **Evita abreviaciones innecesarias:**  
  Las abreviaturas pueden ahorrar tecleo, pero a menudo perjudican la legibilidad del código. Utiliza abreviaciones solo si son ampliamente conocidas y aceptadas (por ejemplo, `id` para identificador).

### 2.2. Variables de ámbito reducido

- **Minimiza el ámbito de las variables:**  
  Declara las variables en el ámbito más reducido posible para evitar confusiones y reducir errores.  
  - **Ejemplo:**  
    ```java
    public void procesarDatos() {
        // Variable declarada en el ámbito del método
        int total = 0;
        for (int i = 0; i < 10; i++) {
            total += i;
        }
        // 'i' solo existe dentro del bucle for.
    }
    ```

### 2.3. Constantes

- **Convención para constantes:**  
  Las constantes (variables declaradas como `static final`) deben nombrarse con mayúsculas y separadas por guiones bajos.  
  - **Ejemplo:**  
    ```java
    public static final int MAX_USUARIOS = 100;
    public static final String MENSAJE_ERROR = "Ha ocurrido un error.";
    ```

### 2.4. Nombres de parámetros y variables de clase

- **Parámetros de métodos:**  
  Utiliza la misma convención lowerCamelCase para los parámetros de los métodos, y asegúrate de que su nombre refleje claramente su función.  
  - **Ejemplo:**
    ```java
    public void actualizarSaldo(double saldoNuevo) {
        // ...
    }
    ```
- **Variables de instancia (campos):**  
  También se siguen las mismas reglas; aunque en algunos casos se prefiere un prefijo (por ejemplo, `this.`) para diferenciarlas de variables locales o parámetros, la notación sigue siendo lowerCamelCase.
  - **Ejemplo:**
    ```java
    public class CuentaBancaria {
        private double saldoActual;
        
        public CuentaBancaria(double saldoInicial) {
            this.saldoActual = saldoInicial;
        }
    }
    ```

### 2.5. Uso en colecciones y estructuras de datos

- **Variables de colecciones:**  
  Si una variable almacena una colección de elementos (por ejemplo, un arreglo, una lista, un conjunto), se recomienda usar un nombre en plural.  
  - **Ejemplo:**  
    ```java
    List<String> nombresEstudiantes = new ArrayList<>();
    int[] numerosPares = {2, 4, 6, 8};
    ```



## 3. Ejemplos Prácticos

### Ejemplo 1: Variables locales y parámetros

```java
public class Calculadora {

    // Método que calcula el promedio de dos números
    public double calcularPromedio(double primerValor, double segundoValor) {
        double sumaTotal = primerValor + segundoValor;
        double promedio = sumaTotal / 2;
        return promedio;
    }
}
```

*Puntos a destacar:*
- Los nombres `primerValor` y `segundoValor` son descriptivos y en lowerCamelCase.
- Las variables locales `sumaTotal` y `promedio` siguen la misma convención.

### Ejemplo 2: Constantes y variables de instancia

```java
public class Aplicacion {

    // Constante (nombre en mayúsculas con guiones bajos)
    public static final int MAX_INTENTOS = 5;
    
    // Variable de instancia (nombre en lowerCamelCase)
    private int contadorIntentos;

    public Aplicacion() {
        this.contadorIntentos = 0;
    }
    
    public void incrementarIntentos() {
        if (contadorIntentos < MAX_INTENTOS) {
            contadorIntentos++;
        }
    }
}
```

*Puntos a destacar:*
- `MAX_INTENTOS` está en mayúsculas con guiones bajos, siguiendo la convención para constantes.
- `contadorIntentos` utiliza lowerCamelCase, siendo claro y descriptivo.

