## Ejemplo 1: Mostrar la Fecha y la Fecha y Hora Actual

**Descripción:**  
Se muestra cómo obtener la fecha actual y la fecha y hora actual utilizando `LocalDate.now()` y `LocalDateTime.now()`.

```java
import java.time.LocalDate;
import java.time.LocalDateTime;

public class EjemploFechaActual {
    public static void main(String[] args) {
        // Obtener la fecha actual (sin hora)
        LocalDate fechaActual = LocalDate.now();
        // Obtener la fecha y hora actual
        LocalDateTime fechaHoraActual = LocalDateTime.now();
        
        System.out.println("Fecha actual: " + fechaActual);
        System.out.println("Fecha y hora actual: " + fechaHoraActual);
    }
}
```



## Ejemplo 2: Crear una Fecha Específica

**Descripción:**  
Se crea una fecha fija utilizando `LocalDate.of()`.  
*Ejemplo:* Fecha de nacimiento: 15 de marzo de 1990.

```java
import java.time.LocalDate;

public class EjemploFechaEspecifica {
    public static void main(String[] args) {
        // Crear una fecha específica (año, mes, día)
        LocalDate fechaNacimiento = LocalDate.of(1990, 3, 15);
        System.out.println("Fecha de nacimiento: " + fechaNacimiento);
    }
}
```



## Ejemplo 3: Operaciones Aritméticas con Fechas

**Descripción:**  
Se muestran operaciones básicas con fechas: sumar días y restar meses a la fecha actual.

```java
import java.time.LocalDate;

public class EjemploOperacionesFechas {
    public static void main(String[] args) {
        LocalDate fechaActual = LocalDate.now();
        
        // Sumar 10 días a la fecha actual
        LocalDate fechaMasDiezDias = fechaActual.plusDays(10);
        // Restar 2 meses a la fecha actual
        LocalDate fechaMenosDosMeses = fechaActual.minusMonths(2);
        
        System.out.println("Fecha actual: " + fechaActual);
        System.out.println("Fecha tras sumar 10 días: " + fechaMasDiezDias);
        System.out.println("Fecha tras restar 2 meses: " + fechaMenosDosMeses);
    }
}
```



## Ejemplo 4: Comparación de Fechas

**Descripción:**  
Se comparan dos fechas utilizando los métodos `isBefore()`, `isAfter()` e `isEqual()`.

```java
import java.time.LocalDate;

public class EjemploCompararFechas {
    public static void main(String[] args) {
        LocalDate fecha1 = LocalDate.of(2025, 2, 10);
        LocalDate fecha2 = LocalDate.of(2025, 12, 25);
        
        if (fecha1.isBefore(fecha2)) {
            System.out.println(fecha1 + " es anterior a " + fecha2);
        } else if (fecha1.isAfter(fecha2)) {
            System.out.println(fecha1 + " es posterior a " + fecha2);
        } else {
            System.out.println(fecha1 + " y " + fecha2 + " son iguales.");
        }
    }
}
```



## Ejemplo 5: Formatear una Fecha

**Descripción:**  
Se utiliza `DateTimeFormatter` para mostrar la fecha actual en un formato personalizado ("dd/MM/yyyy").

```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class EjemploFormatearFecha {
    public static void main(String[] args) {
        LocalDate fechaActual = LocalDate.now();
        // Definir el patrón de formato
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        // Formatear la fecha actual
        String fechaFormateada = fechaActual.format(formato);
        System.out.println("Fecha actual formateada: " + fechaFormateada);
    }
}
```



## Ejemplo 6: Parsear una Cadena a Fecha

**Descripción:**  
Se convierte una cadena con una fecha en formato "dd/MM/yyyy" a un objeto `LocalDate`.

```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class EjemploParsearFecha {
    public static void main(String[] args) {
        // Cadena con fecha en formato "dd/MM/yyyy"
        String fechaString = "25/12/2025";
        // Definir el formateador con el mismo patrón
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        // Convertir la cadena a LocalDate
        LocalDate fechaParseada = LocalDate.parse(fechaString, formato);
        System.out.println("Fecha parseada: " + fechaParseada);
    }
}
```



## Ejemplo 7: Ejemplo Combinado con Entrada de Usuario

**Descripción:**  
Se pide al usuario que introduzca la fecha de un evento en formato "dd/MM/yyyy". Se parsea la cadena, se calcula la fecha 30 días antes del evento y se compara la fecha del evento con la fecha actual.

```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.util.Scanner;

public class EjemploFechaEvento {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Pedir al usuario la fecha del evento en formato "dd/MM/yyyy"
        System.out.print("Introduce la fecha del evento (dd/MM/yyyy): ");
        String fechaEventoStr = sc.nextLine();
        
        // Definir el formateador
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        // Parsear la cadena a LocalDate
        LocalDate fechaEvento = LocalDate.parse(fechaEventoStr, formato);
        System.out.println("Fecha del evento: " + fechaEvento);
        
        // Calcular la fecha 30 días antes del evento
        LocalDate fechaRecordatorio = fechaEvento.minusDays(30);
        System.out.println("Recordatorio (30 días antes): " + fechaRecordatorio.format(formato));
        
        // Comparar la fecha del evento con la fecha actual
        LocalDate hoy = LocalDate.now();
        if (fechaEvento.isAfter(hoy)) {
            System.out.println("El evento aún no ha ocurrido.");
        } else if (fechaEvento.isBefore(hoy)) {
            System.out.println("El evento ya ocurrió.");
        } else {
            System.out.println("El evento es hoy.");
        }
        
        sc.close();
    }
}
```



## Ejemplo 8: Mostrar Fecha y Hora Actual Formateada

**Descripción:**  
Se utiliza `LocalDateTime` junto con `DateTimeFormatter` para mostrar la fecha y hora actuales en un formato personalizado ("dd/MM/yyyy HH:mm:ss").

```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class EjemploFechaHora {
    public static void main(String[] args) {
        // Obtener la fecha y hora actual
        LocalDateTime ahora = LocalDateTime.now();
        // Definir un formateador para fecha y hora
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");
        // Formatear la fecha y hora
        String fechaHoraFormateada = ahora.format(formato);
        System.out.println("Fecha y hora actual formateada: " + fechaHoraFormateada);
    }
}
```
