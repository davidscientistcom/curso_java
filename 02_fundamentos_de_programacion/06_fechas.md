# Trabajando con Fechas en Java

En cualquier aplicación es muy común necesitar trabajar con fechas y horas: por ejemplo, para registrar la fecha de nacimiento de un usuario, programar eventos o calcular plazos. Desde Java 8 se introdujo el paquete **java.time**, que proporciona una API más robusta, intuitiva y segura para manipular fechas y tiempos.

## 1. La Nueva API de Fechas: java.time

La nueva API se basa en clases inmutables y orientadas a objetos, lo que facilita su uso y evita problemas de concurrencia. Algunas de las clases más importantes son:

- **LocalDate:** Representa una fecha sin hora ni zona horaria (por ejemplo, 10/02/2025).  
- **LocalTime:** Representa una hora sin fecha (por ejemplo, 14:30:00).  
- **LocalDateTime:** Combina fecha y hora, sin información de zona horaria.  
- **ZonedDateTime:** Incluye fecha, hora y zona horaria.  
- **Instant:** Representa un instante específico en el tiempo (medido en nanosegundos desde la época: 1970-01-01T00:00:00Z).

Además, para trabajar con formatos y conversiones se utiliza la clase **DateTimeFormatter**.



## 2. Creación de Fechas

### 2.1 Obtener la Fecha y Hora Actual

- **LocalDate.now():**  
  Obtiene la fecha actual del sistema.

  ```java
  LocalDate fechaActual = LocalDate.now();
  System.out.println("Fecha actual: " + fechaActual);
  ```

- **LocalDateTime.now():**  
  Obtiene la fecha y la hora actual.

  ```java
  LocalDateTime ahora = LocalDateTime.now();
  System.out.println("Fecha y hora actual: " + ahora);
  ```

- **ZonedDateTime.now():**  
  Obtiene la fecha y hora actual con la zona horaria del sistema.

  ```java
  ZonedDateTime zonedDateTime = ZonedDateTime.now();
  System.out.println("Fecha y hora con zona: " + zonedDateTime);
  ```

### 2.2 Crear una Fecha Específica

Para crear una fecha con valores específicos se utiliza el método **of()**:

```java
LocalDate fechaNacimiento = LocalDate.of(1990, 3, 15);
System.out.println("Fecha de nacimiento: " + fechaNacimiento);
```



## 3. Operaciones con Fechas

Una de las grandes ventajas de la API java.time es la posibilidad de realizar operaciones aritméticas con fechas de forma sencilla y sin modificar el objeto original (ya que son inmutables).

### 3.1 Sumar o Restar Días, Meses o Años

```java
// Sumar 10 días a la fecha actual
LocalDate fechaFutura = LocalDate.now().plusDays(10);
System.out.println("Fecha dentro de 10 días: " + fechaFutura);

// Restar 2 meses a una fecha
LocalDate fechaMenosMeses = LocalDate.now().minusMonths(2);
System.out.println("Fecha hace 2 meses: " + fechaMenosMeses);
```

### 3.2 Comparar Fechas

Se pueden comparar fechas utilizando métodos como **isBefore()**, **isAfter()** o **isEqual()**:

```java
LocalDate fecha1 = LocalDate.of(2025, 2, 10);
LocalDate fecha2 = LocalDate.of(2025, 12, 25);

if (fecha1.isBefore(fecha2)) {
    System.out.println(fecha1 + " es anterior a " + fecha2);
} else if (fecha1.isAfter(fecha2)) {
    System.out.println(fecha1 + " es posterior a " + fecha2);
} else {
    System.out.println("Ambas fechas son iguales.");
}
```



## 4. Formateo y Parseo de Fechas

Para mostrar una fecha en un formato específico o convertir una cadena a una fecha, se utiliza la clase **DateTimeFormatter**.

[Formato de fechas:] (https://code2care.org/java/list-of-java-simple-date-formats/)

### 4.1 Formateo de Fechas

```java
import java.time.format.DateTimeFormatter;

LocalDate fechaActual = LocalDate.now();
DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String fechaFormateada = fechaActual.format(formato);
System.out.println("Fecha actual formateada: " + fechaFormateada);
```

### 4.2 Parseo de Cadenas a Fechas

```java
String fechaString = "25/12/2025";
LocalDate fechaParseada = LocalDate.parse(fechaString, formato);
System.out.println("Fecha parseada: " + fechaParseada);
```



## 5. Ejemplo Combinado de Fechas

El siguiente ejemplo integra la creación, formateo, operación y parseo de fechas:

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;

public class EjemploFechas {
    public static void main(String[] args) {
        // Obtener la fecha y hora actual
        LocalDate fechaActual = LocalDate.now();
        LocalDateTime ahora = LocalDateTime.now();
        ZonedDateTime zonedDateTime = ZonedDateTime.now();

        System.out.println("Fecha actual (LocalDate): " + fechaActual);
        System.out.println("Fecha y hora actual (LocalDateTime): " + ahora);
        System.out.println("Fecha y hora con zona (ZonedDateTime): " + zonedDateTime);

        // Crear una fecha específica
        LocalDate fechaNacimiento = LocalDate.of(1990, 3, 15);
        System.out.println("Fecha de nacimiento: " + fechaNacimiento);

        // Sumar 10 días a la fecha actual
        LocalDate fechaFutura = fechaActual.plusDays(10);
        System.out.println("Fecha dentro de 10 días: " + fechaFutura);

        // Formatear la fecha actual
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        String fechaFormateada = fechaActual.format(formato);
        System.out.println("Fecha actual formateada: " + fechaFormateada);

        // Parsear una cadena a fecha
        String fechaString = "25/12/2025";
        LocalDate fechaParseada = LocalDate.parse(fechaString, formato);
        System.out.println("Fecha parseada: " + fechaParseada);
    }
}
```

# Formateo de fechas en Java

Java ofrece varias formas de formatear fechas, principalmente a través de la clase `SimpleDateFormat` (Java legacy) y la moderna API de fecha y hora (`java.time` introducida en Java 8).

## SimpleDateFormat (Java legacy)

```java
import java.text.SimpleDateFormat;
import java.util.Date;

public class EjemploFormateoFechas {
    public static void main(String[] args) {
        Date fecha = new Date();
        SimpleDateFormat formato = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
        String fechaFormateada = formato.format(fecha);
        System.out.println(fechaFormateada);
    }
}
```

## Modern Java (java.time)

```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class EjemploFormateoModerno {
    public static void main(String[] args) {
        LocalDateTime ahora = LocalDateTime.now();
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");
        String fechaFormateada = ahora.format(formato);
        System.out.println(fechaFormateada);
    }
}
```

## Patrones de formato más comunes

| Símbolo | Significado | Ejemplo |
|---------|-------------|---------|
| `yyyy` | Año con 4 dígitos | 2025 |
| `yy` | Año con 2 dígitos | 25 |
| `MM` | Mes en número (01-12) | 02 |
| `MMM` | Mes abreviado | Feb |
| `MMMM` | Nombre completo del mes | Febrero |
| `dd` | Día del mes (01-31) | 20 |
| `E` | Día de la semana abreviado | Jue |
| `EEEE` | Nombre completo del día | Jueves |
| `HH` | Hora en formato 24h (00-23) | 13 |
| `hh` | Hora en formato 12h (01-12) | 01 |
| `mm` | Minutos (00-59) | 30 |
| `ss` | Segundos (00-59) | 45 |
| `a` | AM/PM | PM |
| `z` | Zona horaria | GMT |

## Ejemplos prácticos

```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class EjemplosFormato {
    public static void main(String[] args) {
        LocalDateTime fecha = LocalDateTime.now(); // 20/02/2025 14:30:25
        
        // Diferentes formatos con ejemplos
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("dd/MM/yyyy"))); 
        // 20/02/2025
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("yyyy-MM-dd"))); 
        // 2025-02-20
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("EEEE, dd 'de' MMMM 'de' yyyy"))); 
        // Jueves, 20 de febrero de 2025
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("hh:mm a"))); 
        // 02:30 PM
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("HH:mm:ss"))); 
        // 14:30:25
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("dd MMM yy"))); 
        // 20 Feb 25
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("HH:mm:ss.SSS"))); 
        // 14:30:25.123 (con milisegundos)
        
        System.out.println(fecha.format(DateTimeFormatter.ofPattern("EEEE 'en la semana' w 'del año'"))); 
        // Jueves en la semana 8 del año
    }
}
```
