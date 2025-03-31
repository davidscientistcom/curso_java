<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

## Redondeo y Truncamiento en Java

Cuando trabajamos con números en punto flotante en Java, es común necesitar manipular su precisión. Esto puede incluir:

- **Truncar:** Quedarse únicamente con la parte entera, eliminando la parte decimal sin redondear.  
- **Redondear:** Aproximar el número a un entero o a un número con un número fijo de decimales, ya sea redondeando hacia arriba, hacia abajo o de forma "clásica" (al entero más cercano).

A continuación se explican diversas técnicas y ejemplos para cada caso.



### 1. Truncar un Número

El truncamiento consiste en descartar la parte decimal de un número. Esto se puede lograr fácilmente convirtiendo el número a un tipo entero mediante un _casting_:

```java
double valor = 3.14159;
int parteEntera = (int) valor;  // Resultado: 3
System.out.println("Parte entera: " + parteEntera);
```

> **Nota:**  
> Con números negativos, el _casting_ descarta la parte decimal, pero no equivale a la función `Math.floor()` (que redondea hacia el entero inferior).  
> Por ejemplo:
> ```java
> double valorNegativo = -3.14159;
> int truncado = (int) valorNegativo;  // Resultado: -3
> double piso = Math.floor(valorNegativo);  // Resultado: -4.0
> ```



### 2. Redondeo a Entero

Java ofrece métodos en la clase `Math` para redondear números a su valor entero más cercano o redondear hacia arriba/abajo:

#### 2.1. Redondeo Clásico: `Math.round()`

Redondea al entero más cercano. Para valores con parte decimal igual a 0.5, se redondea hacia el entero mayor.

```java
double valor = 3.14159;
long redondeado = Math.round(valor);  // Resultado: 3
System.out.println("Redondeo clásico: " + redondeado);
```

> Para usarlo en variables de tipo `int`, puedes hacer:
> ```java
> int redondeadoInt = (int) Math.round(valor);
> ```

#### 2.2. Redondeo Hacia Abajo: `Math.floor()`

Devuelve el mayor entero menor o igual al valor dado (redondeo hacia abajo).

```java
double valor2 = 3.14159;
double piso = Math.floor(valor2);  // Resultado: 3.0
System.out.println("Redondeo hacia abajo (floor): " + piso);
```

#### 2.3. Redondeo Hacia Arriba: `Math.ceil()`

Devuelve el menor entero mayor o igual al valor dado (redondeo hacia arriba).

```java
double valor3 = 3.14159;
double techo = Math.ceil(valor3);  // Resultado: 4.0
System.out.println("Redondeo hacia arriba (ceil): " + techo);
```



### 3. Redondear a un Número con Decimales Fijos

Muchas veces necesitamos redondear un número a un número específico de decimales (por ejemplo, 2 o 3 decimales). Existen varios métodos para hacerlo:

#### 3.1. Usando `Math.round()`

Una técnica común consiste en multiplicar el número por 10 elevado al número de decimales deseados, redondear y luego dividir:

```java
double valor = 3.14159;
double factor = 100.0;  // Para 2 decimales (10^2)
double redondeado2Decimales = Math.round(valor * factor) / factor;
System.out.println("Redondeado a 2 decimales: " + redondeado2Decimales);
```

Para 3 decimales, se usa 1000.0 (10³):

```java
double factor3 = 1000.0;
double redondeado3Decimales = Math.round(valor * factor3) / factor3;
System.out.println("Redondeado a 3 decimales: " + redondeado3Decimales);
```

#### 3.2. Usando `BigDecimal`

La clase `BigDecimal` proporciona mayor control y precisión en el redondeo:

```java
import java.math.BigDecimal;
import java.math.RoundingMode;

public class RedondeoConBigDecimal {
    public static void main(String[] args) {
        double valor = 3.14159;
        
        // Redondear a 2 decimales (redondeo clásico: HALF_UP)
        BigDecimal bd = new BigDecimal(valor);
        bd = bd.setScale(2, RoundingMode.HALF_UP);
        System.out.println("BigDecimal a 2 decimales: " + bd.doubleValue());
        
        // Redondear a 3 decimales, redondeando siempre hacia arriba (CEILING)
        bd = new BigDecimal(valor);
        bd = bd.setScale(3, RoundingMode.CEILING);
        System.out.println("BigDecimal a 3 decimales (ceil): " + bd.doubleValue());
    }
}
```

#### 3.3. Usando Formateo de Cadenas

Si el objetivo es solo mostrar el número con un formato fijo, se puede utilizar `String.format()` o `System.out.printf()`. Esto no cambia el valor almacenado, sino solo la forma en que se muestra:

```java
double valor = 3.14159;
System.out.printf("Valor con 2 decimales: %.2f\n", valor);  // Imprime 3.14
System.out.printf("Valor con 3 decimales: %.3f\n", valor);  // Imprime 3.142
```



### Resumen

- **Truncamiento:**  
  Para obtener la parte entera sin redondear, se utiliza el cast a `int`:
  ```java
  int truncado = (int) valor;
  ```

- **Redondeo a Entero:**  
  - `Math.round(valor)` redondea al entero más cercano.  
  - `Math.floor(valor)` redondea hacia abajo.  
  - `Math.ceil(valor)` redondea hacia arriba.

- **Redondeo a n Decimales:**  
  - **Con Math.round():** Multiplicar por 10ⁿ, redondear y dividir entre 10ⁿ.
  - **Con BigDecimal:** Utilizar `setScale(n, RoundingMode.X)` para obtener mayor precisión.
  - **Con Formateo:** Utilizar `String.format()` o `System.out.printf()` para presentar el número formateado.
