# Ejercicio: Calculadora de Edad y Estadísticas

## Enunciado
Crea un programa que pida al usuario su fecha de nacimiento y calcule:
1. Su edad exacta en años, meses y días
2. Los días que faltan para su próximo cumpleaños
3. Un resumen estadístico con:
   - Número de días vividos
   - Porcentaje de años bisiestos vividos
   - Día de la semana en que nació

Además, el programa debe validar que los datos ingresados sean correctos (fechas válidas y números).

## Solución
```java
import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.Period;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;
import java.time.temporal.ChronoUnit;
import java.util.Scanner;

public class CalculadoraEdad {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        LocalDate fechaNacimiento = null;
        
        // Solicitar y validar la fecha de nacimiento
        while (fechaNacimiento == null) {
            System.out.println("Introduce tu fecha de nacimiento (formato DD/MM/AAAA): ");
            String fechaInput = scanner.nextLine();
            
            try {
                // Convertir la cadena a fecha
                DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
                fechaNacimiento = LocalDate.parse(fechaInput, formatter);
                
                // Validar que la fecha no sea en el futuro
                if (fechaNacimiento.isAfter(LocalDate.now())) {
                    System.out.println("Error: La fecha de nacimiento no puede estar en el futuro.");
                    fechaNacimiento = null;
                }
            } catch (DateTimeParseException e) {
                System.out.println("Error: Formato de fecha inválido. Usa el formato DD/MM/AAAA.");
            }
        }
        
        // Obtener la fecha actual
        LocalDate hoy = LocalDate.now();
        
        // 1. Calcular edad exacta
        Period edad = Period.between(fechaNacimiento, hoy);
        System.out.println("\n--- RESULTADOS ---");
        System.out.println("1. Tu edad exacta es: " + 
                          edad.getYears() + " años, " + 
                          edad.getMonths() + " meses y " + 
                          edad.getDays() + " días");
        
        // 2. Días para el próximo cumpleaños
        LocalDate proximoCumpleanos = fechaNacimiento.withYear(hoy.getYear());
        
        // Si el cumpleaños de este año ya pasó, calcular para el próximo año
        if (proximoCumpleanos.isBefore(hoy) || proximoCumpleanos.isEqual(hoy)) {
            proximoCumpleanos = proximoCumpleanos.plusYears(1);
        }
        
        long diasHastaCumpleanos = ChronoUnit.DAYS.between(hoy, proximoCumpleanos);
        System.out.println("2. Faltan " + diasHastaCumpleanos + " días para tu próximo cumpleaños");
        
        // 3. Estadísticas
        System.out.println("\n--- ESTADÍSTICAS ---");
        
        // Días vividos
        long diasVividos = ChronoUnit.DAYS.between(fechaNacimiento, hoy);
        System.out.println("• Has vivido " + diasVividos + " días en total");
        
        // Porcentaje años bisiestos
        int anoInicio = fechaNacimiento.getYear();
        int anoFin = hoy.getYear();
        int totalAnos = anoFin - anoInicio + 1;
        int anosBisiestos = 0;
        
        for (int ano = anoInicio; ano <= anoFin; ano++) {
            if (esAñoBisiesto(ano)) {
                anosBisiestos++;
            }
        }
        
        double porcentajeBisiestos = (double) anosBisiestos / totalAnos * 100;
        System.out.printf("• Porcentaje de años bisiestos vividos: %.2f%%\n", porcentajeBisiestos);
        
        // Día de la semana en que nació
        DayOfWeek diaSemana = fechaNacimiento.getDayOfWeek();
        String nombreDia = obtenerNombreDia(diaSemana);
        System.out.println("• Naciste un " + nombreDia);
        
        // Bonus: Convertir cadena a entero con validación
        System.out.println("\n--- BONUS: CONVERSIÓN DE CADENA A ENTERO ---");
        System.out.println("Introduce un número para convertirlo a entero: ");
        String numeroStr = scanner.nextLine();
        
        try {
            int numero = Integer.parseInt(numeroStr);
            System.out.println("Número convertido correctamente: " + numero);
            System.out.println("El doble de tu número es: " + (numero * 2));
        } catch (NumberFormatException e) {
            System.out.println("Error: No has introducido un número entero válido.");
        }
        
        scanner.close();
    }
    
    // Método para verificar si un año es bisiesto
    private static boolean esAñoBisiesto(int año) {
        return (año % 4 == 0 && año % 100 != 0) || (año % 400 == 0);
    }
    
    // Método para obtener el nombre del día en español
    private static String obtenerNombreDia(DayOfWeek dia) {
        switch (dia) {
            case MONDAY: return "lunes";
            case TUESDAY: return "martes";
            case WEDNESDAY: return "miércoles";
            case THURSDAY: return "jueves";
            case FRIDAY: return "viernes";
            case SATURDAY: return "sábado";
            case SUNDAY: return "domingo";
            default: return "desconocido";
        }
    }
}
```
