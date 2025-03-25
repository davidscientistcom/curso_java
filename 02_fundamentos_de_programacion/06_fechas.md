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



## Curiosidades sobre el tiempo y las fechas en informática

Al trabajar con fechas y horas en programación, especialmente en sistemas distribuidos o bases de datos, es importante conocer algunas anomalías y curiosidades históricas que pueden provocar errores sutiles si no se tienen en cuenta. A continuación, se recopilan algunos de los casos más relevantes.



1. Existen fechas que nunca han existido

Uno de los ejemplos más conocidos es el del cambio de calendario juliano al gregoriano. En muchos países europeos, al adoptar el calendario gregoriano en el siglo XVI, se eliminaron 10 días del calendario para corregir el desfase acumulado con respecto al año solar.
	•	En España, el cambio se hizo en 1582:
El día jueves 4 de octubre fue seguido directamente por el viernes 15 de octubre, lo que significa que los días del 5 al 14 de octubre de 1582 no existieron.

Este tipo de saltos puede causar errores en programas que intenten validar o calcular diferencias entre fechas históricas sin tener en cuenta este ajuste.



1. Hay instantes del tiempo que se repiten

Esto ocurre en los países que aplican el horario de verano (DST). Al final del horario de verano, se retrasa el reloj una hora, lo que provoca que una misma hora ocurra dos veces en el mismo día.
	•	Ejemplo típico en España:
	•	A las 03:00 del último domingo de octubre, el reloj se retrasa a las 02:00, por lo que el intervalo de las 02:00 a 03:00 ocurre dos veces.
	•	Esto genera ambigüedad horaria: una marca de tiempo como 2023-10-29 02:30 puede referirse a dos momentos distintos.

Este fenómeno puede causar problemas en bases de datos, logs, sistemas financieros y procesos automatizados si no se maneja correctamente la zona horaria con información de DST.



1. Hay instantes que no existen

También debido al horario de verano. Al principio del horario de verano, los relojes se adelantan una hora, lo que provoca que haya una hora que nunca llega a ocurrir.
	•	En España:
	•	A las 02:00 del último domingo de marzo, se adelanta a las 03:00.
	•	Por tanto, no existen las 02:00 a 02:59 de ese día.

Si se intenta registrar o procesar un evento en ese rango inexistente, puede haber errores o excepciones si no se manejan correctamente las zonas horarias.


1. El huso horario de España no coincide con su posición geográfica

Por meridiano, España debería estar en el UTC+0 (como Portugal o Reino Unido), ya que el meridiano de Greenwich pasa por Castellón y Aragón.

Sin embargo, en 1940, durante la dictadura franquista, se adelantó el reloj una hora para alinearse con la hora de Berlín (UTC+1), siguiendo el ejemplo de la Alemania nazi durante la Segunda Guerra Mundial.

Aunque el cambio debía ser provisional, nunca se volvió al horario original. Por tanto, España mantiene hasta hoy un horario que no corresponde con su ubicación geográfica, y durante el horario de verano se encuentra incluso en UTC+2.

Esto afecta especialmente a temas de productividad, sueño y sincronización con países vecinos, y también puede ser relevante en sistemas que asuman que España está en UTC+0 por su posición.



1. Las zonas horarias cambian a lo largo del tiempo

Las zonas horarias no son fijas. Pueden cambiar por decisión política o legal. Países o regiones cambian:
	•	Su uso o no del horario de verano.
	•	Su huso horario base.
	•	Sus reglas de transición entre invierno y verano.

Por ejemplo:
	•	Rusia eliminó el horario de verano en 2011 y lo reintrodujo parcialmente más tarde.
	•	Marruecos aplica el horario de verano todo el año salvo durante el Ramadán.

Por eso es fundamental usar bases de datos de zonas horarias actualizadas, como la IANA Time Zone Database (también conocida como tzdata), que los sistemas operativos y lenguajes como Java, Python o .NET utilizan internamente.