```JAVA
import java.util.ArrayList;
import java.util.Scanner;

public class GestorCumpleaniosRefactor {
    
    // Scanner global, para no crearlo y cerrarlo varias veces.
    private static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        // Listas en paralelo: mismo índice para nombre y fecha
        ArrayList<String> listaNombres = new ArrayList<>();
        ArrayList<String> listaFechas = new ArrayList<>();

        // Bucle principal del menú
        while (true) {
            mostrarMenu();
            int opcion = leerOpcion(); // lee la opción del usuario
            
            switch (opcion) {
                case 1:
                    // Agregar
                    agregarCumpleanios(listaNombres, listaFechas);
                    break;
                case 2:
                    // Buscar
                    buscarCumpleanios(listaNombres, listaFechas);
                    break;
                case 3:
                    // Eliminar
                    eliminarCumpleanios(listaNombres, listaFechas);
                    break;
                case 4:
                    // Listar
                    listarCumpleanios(listaNombres, listaFechas);
                    break;
                case 5:
                    // Salir
                    System.out.println("Saliendo del programa...");
                    sc.close(); // Cerramos el Scanner antes de salir
                    return;
                default:
                    System.out.println("Opción no válida, por favor selecciona entre 1 y 5.");
            }
        }
    }

    /**
     * Muestra las opciones del menú principal por consola.
     */
    private static void mostrarMenu() {
        System.out.println("\n===== GESTOR DE CUMPLEAÑOS =====");
        System.out.println("1. Agregar Cumpleaños");
        System.out.println("2. Buscar Cumpleaños");
        System.out.println("3. Eliminar Cumpleaños");
        System.out.println("4. Listar Cumpleaños");
        System.out.println("5. Salir");
        System.out.print("Elige una opción: ");
    }

    /**
     * Lee la opción del usuario como entero, gestionando posibles errores de formato.
     */
    private static int leerOpcion() {
        try {
            return Integer.parseInt(sc.nextLine());
        } catch (NumberFormatException e) {
            // Si no es un número válido, devolvemos un -1 para indicar error
            return -1;
        }
    }

    /**
     * Lee un String tras mostrar el mensaje indicado por parámetro.
     */
    private static String readString(String mensaje) {
        System.out.print(mensaje);
        return sc.nextLine();
    }

    /**
     * Agrega un nuevo cumpleaños (nombre y fecha) a las listas.
     */
    private static void agregarCumpleanios(ArrayList<String> listaNombres, ArrayList<String> listaFechas) {
        String nombre = readString("Introduce el nombre: ");
        String fecha = readString("Introduce la fecha de nacimiento (dd/mm/aaaa): ");

        listaNombres.add(nombre);
        listaFechas.add(fecha);

        System.out.println(">>> Cumpleaños añadido con éxito <<<");
    }

    /**
     * Busca y muestra la fecha de cumpleaños de un nombre dado.
     */
    private static void buscarCumpleanios(ArrayList<String> listaNombres, ArrayList<String> listaFechas) {
        String nombreBuscado = readString("Introduce el nombre a buscar: ");
        int indice = findIndexOfName(nombreBuscado, listaNombres);
        
        if (indice == -1) {
            System.out.println("No se ha encontrado un cumpleaños para la persona: " + nombreBuscado);
        } else {
            String fecha = listaFechas.get(indice);
            System.out.println("La fecha de nacimiento de " + nombreBuscado + " es: " + fecha);
        }
    }

    /**
     * Elimina el cumpleaños de un nombre dado, si existe.
     */
    private static void eliminarCumpleanios(ArrayList<String> listaNombres, ArrayList<String> listaFechas) {
        String nombreEliminar = readString("Introduce el nombre cuyo registro deseas eliminar: ");
        int indice = findIndexOfName(nombreEliminar, listaNombres);

        if (indice == -1) {
            System.out.println("No se encontró registro con ese nombre para eliminar.");
        } else {
            listaNombres.remove(indice);
            listaFechas.remove(indice);
            System.out.println(">>> Registro eliminado con éxito <<<");
        }
    }

    /**
     * Lista todos los cumpleaños almacenados.
     */
    private static void listarCumpleanios(ArrayList<String> listaNombres, ArrayList<String> listaFechas) {
        if (listaNombres.isEmpty()) {
            System.out.println("No hay registros de cumpleaños.");
        } else {
            System.out.println("Lista de Cumpleaños:");
            for (int i = 0; i < listaNombres.size(); i++) {
                System.out.println("- " + listaNombres.get(i)
                                   + " : " + listaFechas.get(i));
            }
        }
    }

    /**
     * Busca el índice del nombre en la lista (ignora mayúsculas/minúsculas).
     * Si no lo encuentra, retorna -1.
     */
    private static int findIndexOfName(String nombre, ArrayList<String> listaNombres) {
        for (int i = 0; i < listaNombres.size(); i++) {
            if (listaNombres.get(i).equalsIgnoreCase(nombre)) {
                return i;
            }
        }
        return -1; // No encontrado
    }
}
```