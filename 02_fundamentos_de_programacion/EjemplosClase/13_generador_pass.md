```java 
import java.util.Scanner;


public class Main {

        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            // Seleccionamos el número de dígitos
            System.out.println("Introduce el número de dígitos");
            int numeroElementos = scanner.nextInt();

            // Seleccionamos el nivel de complejidad del pass
            int complejidad = seleccionarComplejidad(scanner);

            // Generar el password
            String passwordGenerado = generarPassword(numeroElementos,complejidad);

            String complejidadCalculada = calcularComplejidad(numeroElementos,complejidad);

            System.out.println("El password generado es :"+passwordGenerado+ " y su complejidad es :"+complejidadCalculada);

            scanner.close();

        }

    private static String calcularComplejidad(int numeroElementos, int complejidad) {
            return "";
    }

    // Esta función generará el password, en base a los criterios del usuario
    private static String generarPassword(int numeroElementos, int complejidad) {
            return "";
    }

    // Mostrar el menu de complejidad y el usuario introducirá 1,2 o 3
    private static int seleccionarComplejidad(Scanner scanner) {
        System.out.println("1.- Si quieres sólo dígitos");
        System.out.println("2.- Si quieres sólo dígitos y letras");
        System.out.println("3.- Si quieres dígitos, letras y símbolos");

        int numeroElementos = 0;
        do{
            System.out.println("\n. Introduce opcion [1,2 ó 3]");
            numeroElementos = scanner.nextInt();
        }while(numeroElementos < 1 || numeroElementos > 3);

        return numeroElementos;

    }


}

```



