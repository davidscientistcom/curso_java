## Ejemplo de calculadora
```Java
import java.util.Scanner;

public class CalculadoraSimple {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Calculadora Simple");
        System.out.print("Introduce el primer número: ");
        double num1 = scanner.nextDouble();
        
        System.out.print("Introduce el segundo número: ");
        double num2 = scanner.nextDouble();
        
        System.out.println("Elige una operación:");
        System.out.println("1. Suma");
        System.out.println("2. Resta");
        System.out.println("3. Multiplicación");
        System.out.println("4. División");
        System.out.print("Tu elección (1-4): ");
        int opcion = scanner.nextInt();
        
        double resultado = 0;
        String operacion = "";
        
        switch (opcion) {
            case 1:
                resultado = num1 + num2;
                operacion = "suma";
                break;
            case 2:
                resultado = num1 - num2;
                operacion = "resta";
                break;
            case 3:
                resultado = num1 * num2;
                operacion = "multiplicación";
                break;
            case 4:
                if (num2 != 0) {
                    resultado = num1 / num2;
                    operacion = "división";
                } else {
                    System.out.println("Error: No se puede dividir por cero");
                    scanner.close();
                    return;
                }
                break;
            default:
                System.out.println("Opción no válida");
                scanner.close();
                return;
        }
        
        System.out.println("El resultado de la " + operacion + " es: " + resultado);
        scanner.close();
    }
}
```


## Ejemplo de adivinar el número
```Java
import java.util.Scanner;
import java.util.Random;

public class AdivinaNumero {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int numeroSecreto = random.nextInt(100) + 1; // Número entre 1 y 100
        int intentos = 0;
        int adivinanza;
        boolean adivinado = false;
        
        System.out.println("¡Bienvenido a Adivina el Número!");
        System.out.println("He pensado un número entre 1 y 100.");
        
        while (!adivinado && intentos < 10) {
            System.out.print("Intento " + (intentos + 1) + ": Introduce tu adivinanza: ");
            adivinanza = scanner.nextInt();
            intentos++;
            
            if (adivinanza == numeroSecreto) {
                adivinado = true;
                System.out.println("¡Felicidades! Has adivinado el número en " + intentos + " intentos.");
            } else if (adivinanza < numeroSecreto) {
                System.out.println("El número secreto es MAYOR.");
            } else {
                System.out.println("El número secreto es MENOR.");
            }
        }
        
        if (!adivinado) {
            System.out.println("Lo siento, has agotado tus 10 intentos. El número era: " + numeroSecreto);
        }
        
        scanner.close();
    }
}
```

## Ejemplo de conversor de temperatura

```Java
import java.util.Scanner;

public class ConversorTemperatura {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Conversor de Temperatura");
        System.out.println("1. Celsius a Fahrenheit");
        System.out.println("2. Celsius a Kelvin");
        System.out.println("3. Fahrenheit a Celsius");
        System.out.println("4. Fahrenheit a Kelvin");
        System.out.println("5. Kelvin a Celsius");
        System.out.println("6. Kelvin a Fahrenheit");
        System.out.print("Elige una opción (1-6): ");
        
        int opcion = scanner.nextInt();
        double temperatura, resultado;
        
        System.out.print("Introduce la temperatura: ");
        temperatura = scanner.nextDouble();
        
        switch (opcion) {
            case 1: // Celsius a Fahrenheit
                resultado = (temperatura * 9/5) + 32;
                System.out.println(temperatura + " °C = " + resultado + " °F");
                break;
            case 2: // Celsius a Kelvin
                resultado = temperatura + 273.15;
                System.out.println(temperatura + " °C = " + resultado + " K");
                break;
            case 3: // Fahrenheit a Celsius
                resultado = (temperatura - 32) * 5/9;
                System.out.println(temperatura + " °F = " + resultado + " °C");
                break;
            case 4: // Fahrenheit a Kelvin
                resultado = (temperatura - 32) * 5/9 + 273.15;
                System.out.println(temperatura + " °F = " + resultado + " K");
                break;
            case 5: // Kelvin a Celsius
                resultado = temperatura - 273.15;
                System.out.println(temperatura + " K = " + resultado + " °C");
                break;
            case 6: // Kelvin a Fahrenheit
                resultado = (temperatura - 273.15) * 9/5 + 32;
                System.out.println(temperatura + " K = " + resultado + " °F");
                break;
            default:
                System.out.println("Opción no válida");
        }
        
        scanner.close();
    }
}
```

## Ejemplo de gestor de tareas

```Java
import java.util.ArrayList;
import java.util.Scanner;

public class GestorTareas {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<String> tareas = new ArrayList<>();
        ArrayList<Boolean> completadas = new ArrayList<>();
        boolean salir = false;
        
        System.out.println("===== Gestor de Tareas Simple =====");
        
        while (!salir) {
            System.out.println("\nMenú:");
            System.out.println("1. Agregar tarea");
            System.out.println("2. Mostrar tareas");
            System.out.println("3. Marcar tarea como completada");
            System.out.println("4. Eliminar tarea");
            System.out.println("5. Salir");
            System.out.print("Seleccione una opción: ");
            
            int opcion = scanner.nextInt();
            scanner.nextLine(); // Consumir salto de línea
            
            switch (opcion) {
                case 1: // Agregar tarea
                    System.out.print("Introduce la nueva tarea: ");
                    String nuevaTarea = scanner.nextLine();
                    tareas.add(nuevaTarea);
                    completadas.add(false);
                    System.out.println("Tarea agregada correctamente.");
                    break;
                    
                case 2: // Mostrar tareas
                    if (tareas.isEmpty()) {
                        System.out.println("No hay tareas registradas.");
                    } else {
                        System.out.println("\n===== Lista de Tareas =====");
                        for (int i = 0; i < tareas.size(); i++) {
                            String estado = completadas.get(i) ? "[✓]" : "[ ]";
                            System.out.println((i + 1) + ". " + estado + " " + tareas.get(i));
                        }
                    }
                    break;
                    
                case 3: // Marcar como completada
                    if (tareas.isEmpty()) {
                        System.out.println("No hay tareas para marcar.");
                    } else {
                        System.out.print("Introduce el número de la tarea a marcar como completada: ");
                        int indice = scanner.nextInt() - 1;
                        if (indice >= 0 && indice < tareas.size()) {
                            completadas.set(indice, true);
                            System.out.println("Tarea marcada como completada.");
                        } else {
                            System.out.println("Número de tarea inválido.");
                        }
                    }
                    break;
                    
                case 4: // Eliminar tarea
                    if (tareas.isEmpty()) {
                        System.out.println("No hay tareas para eliminar.");
                    } else {
                        System.out.print("Introduce el número de la tarea a eliminar: ");
                        int indice = scanner.nextInt() - 1;
                        if (indice >= 0 && indice < tareas.size()) {
                            System.out.println("Tarea eliminada: " + tareas.get(indice));
                            tareas.remove(indice);
                            completadas.remove(indice);
                        } else {
                            System.out.println("Número de tarea inválido.");
                        }
                    }
                    break;
                    
                case 5: // Salir
                    salir = true;
                    System.out.println("¡Gracias por usar el Gestor de Tareas!");
                    break;
                    
                default:
                    System.out.println("Opción no válida. Intente de nuevo.");
            }
        }
        
        scanner.close();
    }
}
```