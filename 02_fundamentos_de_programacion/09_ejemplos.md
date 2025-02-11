## Ejemplo 1: Determinar si un Número es Par o Impar

**Descripción:**  
Se pide al usuario un número entero y se utiliza un condicional para determinar si es par o impar.

```java
import java.util.Scanner;

public class NumeroParImpar {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicitar un número al usuario
        System.out.print("Introduce un número entero: ");
        int numero = sc.nextInt();
        
        // Evaluar si el número es par o impar
        if (numero % 2 == 0) {
            System.out.println("El número " + numero + " es par.");
        } else {
            System.out.println("El número " + numero + " es impar.");
        }
        
        sc.close();
    }
}
```

---

## Ejemplo 2: Comparar Dos Números

**Descripción:**  
Se leen dos números enteros y se compara cuál es mayor, o si son iguales, utilizando la estructura if–else if–else.

```java
import java.util.Scanner;

public class MayorOMenor {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de dos números
        System.out.print("Introduce el primer número: ");
        int num1 = sc.nextInt();
        System.out.print("Introduce el segundo número: ");
        int num2 = sc.nextInt();
        
        // Comparar los dos números
        if (num1 > num2) {
            System.out.println(num1 + " es mayor que " + num2);
        } else if (num1 < num2) {
            System.out.println(num1 + " es menor que " + num2);
        } else {
            System.out.println("Ambos números son iguales.");
        }
        
        sc.close();
    }
}
```

---

## Ejemplo 3: Clasificación de Calificaciones

**Descripción:**  
Se solicita al usuario la nota de un estudiante (de 0 a 100) y se clasifica la calificación en función de intervalos definidos usando if–else if–else.

```java
import java.util.Scanner;

public class ClasificacionNotas {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Lectura de la nota
        System.out.print("Introduce la nota del estudiante (0-100): ");
        int nota = sc.nextInt();
        
        // Clasificación de la nota
        if (nota >= 90) {
            System.out.println("Calificación: Sobresaliente");
        } else if (nota >= 75) {
            System.out.println("Calificación: Notable");
        } else if (nota >= 60) {
            System.out.println("Calificación: Aprobado");
        } else {
            System.out.println("Calificación: Suspenso");
        }
        
        sc.close();
    }
}
```

---

## Ejemplo 4: Determinar el Día de la Semana (con Switch)

**Descripción:**  
El usuario introduce un número del 1 al 7 y se utiliza la sentencia switch para mostrar el día de la semana correspondiente.

```java
import java.util.Scanner;

public class DiaSemana {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicitar el número del día
        System.out.print("Introduce un número (1-7) para el día de la semana: ");
        int dia = sc.nextInt();
        String nombreDia;
        
        // Uso de switch para determinar el día
        switch(dia) {
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
                nombreDia = "Número inválido";
                break;
        }
        
        System.out.println("El día de la semana es: " + nombreDia);
        sc.close();
    }
}
```

---

## Ejemplo 5: Aprobar Examen Basado en Nota y Asistencia

**Descripción:**  
Se solicitan la nota del examen y el porcentaje de asistencia del estudiante. Para aprobar, el estudiante debe tener una nota mayor o igual a 60 y una asistencia de al menos 75%.

```java
import java.util.Scanner;

public class AprobarExamen {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicitar la nota y la asistencia
        System.out.print("Introduce la nota del examen (0-100): ");
        int nota = sc.nextInt();
        System.out.print("Introduce el porcentaje de asistencia (0-100): ");
        int asistencia = sc.nextInt();
        
        // Evaluar si el estudiante aprueba
        if (nota >= 60 && asistencia >= 75) {
            System.out.println("El estudiante ha aprobado el examen.");
        } else {
            System.out.println("El estudiante no ha aprobado el examen.");
        }
        
        sc.close();
    }
}
```

---

## Ejemplo 6: Evaluar si un Número es Positivo, Negativo o Cero

**Descripción:**  
El usuario introduce un número y se evalúa si el número es mayor que cero (positivo), menor que cero (negativo) o igual a cero.

```java
import java.util.Scanner;

public class NumeroPositivoNegativo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Solicitar un número
        System.out.print("Introduce un número: ");
        int numero = sc.nextInt();
        
        // Evaluar la condición
        if (numero > 0) {
            System.out.println("El número es positivo.");
        } else if (numero < 0) {
            System.out.println("El número es negativo.");
        } else {
            System.out.println("El número es cero.");
        }
        
        sc.close();
    }
}
```
