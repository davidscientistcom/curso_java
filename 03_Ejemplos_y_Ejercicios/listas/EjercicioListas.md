- El siguiente ejemplo ha sido desarrollado para tener en cuenta distintos usos de las colecciones.
- Fijaos en 
  - Listas para almacenar información común que puede repetirse
  - Usos de diccionarios para acceder por ID
  - Uso de conjuntos para eliminar duplicados.


```Java

import java.util.*;

public class GestionNotas {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Map<String, List<Double>> notasEstudiantes = new HashMap<>();
        notasEstudiantes.put("2023001", Arrays.asList(4.5, 6.0, 5.5));
        notasEstudiantes.put("2023002", Arrays.asList(8.0, 7.5, 9.0));
        notasEstudiantes.put("2023003", Arrays.asList(3.0, 4.0, 2.5));
        notasEstudiantes.put("2023004", Arrays.asList(6.0, 5.5, 6.5));
        notasEstudiantes.put("2023005", Arrays.asList(2.0, 3.5, 4.0));

        int opcion;
        do {
            opcion = mostrarMenu(sc);
            switch (opcion) {
                case 1:
                    mostrarNotaMedia(sc, notasEstudiantes);
                    break;
                case 2:
                    mostrarAprobados(notasEstudiantes);
                    break;
                case 3:
                    mostrarSuspensos(notasEstudiantes);
                    break;
                case 4:
                    mostrarEstadisticas(notasEstudiantes);
                    break;
                case 5:
                    System.out.println("Saliendo del sistema...");
                    break;
                default:
                    System.out.println("Opción no válida.");
            }
        } while (opcion != 5);
    }

    public static int mostrarMenu(Scanner sc) {
        System.out.println("\n=== MENÚ ===");
        System.out.println("1. Ver nota media de un estudiante");
        System.out.println("2. Ver lista de aprobados");
        System.out.println("3. Ver lista de suspensos");
        System.out.println("4. Ver porcentaje de aprobados y suspensos");
        System.out.println("5. Salir");
        System.out.print("Selecciona una opción: ");
        return sc.nextInt();
    }

    public static void mostrarNotaMedia(Scanner sc, Map<String, List<Double>> notasEstudiantes) {
        sc.nextLine();
        System.out.print("Introduce el código del estudiante: ");
        String codigo = sc.nextLine();
        if (notasEstudiantes.containsKey(codigo)) {
            List<Double> notas = notasEstudiantes.get(codigo);
            double media = calcularMedia(notas);
            System.out.println("Nota media del estudiante " + codigo + ": " + media);
        } else {
            System.out.println("Estudiante no encontrado.");
        }
    }

    public static void mostrarAprobados(Map<String, List<Double>> notasEstudiantes) {
        System.out.println("Estudiantes aprobados:");
        for (Map.Entry<String, List<Double>> entry : notasEstudiantes.entrySet()) {
            double media = calcularMedia(entry.getValue());
            if (media >= 5.0) {
                System.out.println("Código: " + entry.getKey() + " | Media: " + media);
            }
        }
    }

    public static void mostrarSuspensos(Map<String, List<Double>> notasEstudiantes) {
        System.out.println("Estudiantes suspensos:");
        for (Map.Entry<String, List<Double>> entry : notasEstudiantes.entrySet()) {
            double media = calcularMedia(entry.getValue());
            if (media < 5.0) {
                System.out.println("Código: " + entry.getKey() + " | Media: " + media);
            }
        }
    }

    public static void mostrarEstadisticas(Map<String, List<Double>> notasEstudiantes) {
        int total = notasEstudiantes.size();
        long aprobados = notasEstudiantes.values().stream()
                .filter(notas -> calcularMedia(notas) >= 5.0)
                .count();
        long suspensos = total - aprobados;
        double porcAprobados = (aprobados * 100.0) / total;
        double porcSuspensos = (suspensos * 100.0) / total;

        System.out.println("Aprobados: " + aprobados + " (" + porcAprobados + "%)");
        System.out.println("Suspensos: " + suspensos + " (" + porcSuspensos + "%)");
    }

    public static double calcularMedia(List<Double> notas) {
        return notas.stream().mapToDouble(Double::doubleValue).average().orElse(0.0);
    }
}
```