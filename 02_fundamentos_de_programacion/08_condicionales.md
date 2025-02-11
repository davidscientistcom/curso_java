# Condicionales en Java

Las estructuras condicionales permiten que un programa tome decisiones y ejecute diferentes bloques de código según se cumplan o no determinadas condiciones. Esto es fundamental para crear aplicaciones dinámicas que respondan de manera distinta según la entrada del usuario o el estado del sistema.

En Java existen principalmente dos formas de estructurar condicionales:
  
1. **La estructura `if` (y sus variantes `if-else` y `if-else if`):**  
   Se utilizan para evaluar expresiones booleanas (que resultan en `true` o `false`).  
2. **La sentencia `switch`:**  
   Es útil cuando se tiene que evaluar el valor de una única variable frente a múltiples casos discretos.

En esta sección nos centraremos en la estructura `if` y sus variantes, aunque también se explicará el `switch` brevemente.



## 1. La Estructura `if`

### 1.1 Concepto

La sentencia `if` evalúa una condición y, si esta es verdadera, ejecuta un bloque de código. Si la condición es falsa, el bloque se omite. La sintaxis básica es:

```java
if (condición) {
    // Bloque de código que se ejecuta si la condición es true
}
```

**Ejemplo básico:**

```java
public class EjemploIf {
    public static void main(String[] args) {
        int numero = 10;
        
        // Si el número es mayor que 5, se ejecuta el bloque dentro del if
        if (numero > 5) {
            System.out.println("El número es mayor que 5.");
        }
    }
}
```

*Explicación:*  
Aquí, la condición `numero > 5` se evalúa como `true` (ya que 10 es mayor que 5), por lo que se imprime el mensaje.



## 2. La Estructura `if-else`

### 2.1 Concepto

La estructura `if-else` permite definir un camino alternativo. Si la condición es verdadera se ejecuta un bloque y, en caso contrario, se ejecuta otro.

La sintaxis es:

```java
if (condición) {
    // Código a ejecutar si la condición es true
} else {
    // Código a ejecutar si la condición es false
}
```

**Ejemplo:**

```java
public class EjemploIfElse {
    public static void main(String[] args) {
        int edad = 16;
        
        // Se evalúa si la persona es mayor de edad
        if (edad >= 18) {
            System.out.println("Eres mayor de edad.");
        } else {
            System.out.println("Eres menor de edad.");
        }
    }
}
```

*Explicación:*  
Si la variable `edad` es 18 o mayor, se imprime que es mayor de edad; de lo contrario, se indica que es menor de edad.



## 3. La Estructura `if-else if-else`

### 3.1 Concepto

Cuando se deben evaluar múltiples condiciones, se puede encadenar la estructura `if` con uno o varios `else if` y, opcionalmente, un `else` final para capturar el caso que no cumpla ninguna de las condiciones anteriores.

La sintaxis es:

```java
if (condición1) {
    // Código a ejecutar si condición1 es true
} else if (condición2) {
    // Código a ejecutar si condición1 es false y condición2 es true
} else {
    // Código a ejecutar si ninguna de las condiciones anteriores es true
}
```

**Ejemplo: Clasificación de notas**

```java
public class EjemploIfElseIf {
    public static void main(String[] args) {
        int nota = 75;
        
        if (nota >= 90) {
            System.out.println("Sobresaliente");
        } else if (nota >= 75) {
            System.out.println("Notable");
        } else if (nota >= 60) {
            System.out.println("Aprobado");
        } else {
            System.out.println("Suspenso");
        }
    }
}
```

*Explicación:*  
Dependiendo del valor de la variable `nota`, el programa elige el mensaje apropiado. Aquí, con una nota de 75, se imprime "Notable".



## 4. La Sentencia `switch`

### 4.1 Concepto

La sentencia `switch` es una alternativa a múltiples estructuras `if-else if` cuando se evalúa el valor de una variable frente a múltiples casos concretos. Es especialmente útil para evaluar variables de tipo entero, carácter o incluso cadenas (a partir de Java 7).

La sintaxis básica es:

```java
switch (variable) {
    case valor1:
        // Bloque de código para valor1
        break;
    case valor2:
        // Bloque de código para valor2
        break;
    // Se pueden añadir más casos
    default:
        // Bloque de código si ningún caso coincide
        break;
}
```

**Ejemplo: Días de la semana**

```java
public class EjemploSwitch {
    public static void main(String[] args) {
        int dia = 3;
        String nombreDia;
        
        switch (dia) {
            case 1:
                nombreDia = "Lunes";
                break;
            case 2:
                nombreDia = "Martes";
                break;
            case 3:
                nombreDia = "Miércoles";
                break;
            case 4:
                nombreDia = "Jueves";
                break;
            case 5:
                nombreDia = "Viernes";
                break;
            case 6:
                nombreDia = "Sábado";
                break;
            case 7:
                nombreDia = "Domingo";
                break;
            default:
                nombreDia = "Día inválido";
                break;
        }
        
        System.out.println("El día seleccionado es: " + nombreDia);
    }
}
```

*Explicación:*  
El `switch` evalúa el valor de `dia` y, en este caso, como es 3, se asigna "Miércoles" a la variable `nombreDia`.



## 5. Ejemplos Combinados

A continuación se muestran ejemplos que combinan condicionales con la lectura y escritura en consola para resolver problemas sencillos.

### Ejemplo 1: Verificar Mayoría de Edad (con `if-else`)

```java
import java.util.Scanner;

public class VerificarEdad {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Introduce tu edad: ");
        int edad = sc.nextInt();
        
        if (edad >= 18) {
            System.out.println("Eres mayor de edad.");
        } else {
            System.out.println("Eres menor de edad.");
        }
        
        sc.close();
    }
}
```

*Explicación:*  
Se lee la edad del usuario y, mediante un condicional, se determina si es mayor o menor de edad.

### Ejemplo 2: Calcular la Calificación de un Estudiante

```java
import java.util.Scanner;

public class CalificacionEstudiante {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Introduce la nota del estudiante (0-100): ");
        int nota = sc.nextInt();
        
        if (nota >= 90) {
            System.out.println("Sobresaliente");
        } else if (nota >= 75) {
            System.out.println("Notable");
        } else if (nota >= 60) {
            System.out.println("Aprobado");
        } else {
            System.out.println("Suspenso");
        }
        
        sc.close();
    }
}
```

*Explicación:*  
El programa clasifica la calificación del estudiante según el valor introducido, utilizando la estructura `if-else if-else`.

