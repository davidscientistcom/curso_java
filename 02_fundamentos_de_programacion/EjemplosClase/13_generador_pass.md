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

### EJERCICIO RESUELTO
```java

import java.util.Random;
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
           String resultado = "Baja";
           if (numeroElementos > 8 && complejidad == 2) {
               resultado = "Media";
           }
           else if (numeroElementos > 8 && complejidad == 3) {
               resultado = "Alta";
           }
           return resultado;
    }

    // Esta función generará el password, en base a los criterios del usuario
    private static String generarPassword(int numeroElementos, int complejidad) {
            StringBuilder password =new StringBuilder();

            String conjuntoSimbolos = crearConjuntoSimbolos(complejidad);
            for (int i = 0; i < numeroElementos; i++) {
                password.append( seleccionarAleatorio(conjuntoSimbolos));
            }

            return password.toString();
    }

    private static char seleccionarAleatorio(String conjuntoSimbolos) {
            Random random = new Random();
            int indice = random.nextInt(conjuntoSimbolos.length());
            return conjuntoSimbolos.charAt(indice);
    }

    private static String crearConjuntoSimbolos(int complejidad) {
        String mayusculas = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        String minusculas = "abcdefghijklmnopqrstuvwxyz";
        String numeros     = "0123456789";
        String simbolos    = "!@#$%&*+=?";

        String conjunto = "";

        switch (complejidad) {
            case 1:
                conjunto = numeros;
                break;
            case 2:
                conjunto = numeros+mayusculas+minusculas;
                break;
            case 3:
                conjunto = numeros+mayusculas+minusculas+simbolos;
                break;
            default:
                System.out.println("Error no controlado");
                break;
        }

        return conjunto;



    }

    // Mostrar el menu de complejidad y el usuario introducirá 1,2 o 3
    private static int seleccionarComplejidad(Scanner scanner) {
        System.out.println("1.- Si quieres sólo dígitos");
        System.out.println("2.- Si quieres sólo dígitos y letras");
        System.out.println("3.- Si quieres dígitos, letras y símbolos");

        int complejidadSeleccionada = 0;
        do{
            System.out.println("\n. Introduce opcion [1,2 ó 3]");
            complejidadSeleccionada = scanner.nextInt();
        }while(complejidadSeleccionada < 1 || complejidadSeleccionada > 3);

        return complejidadSeleccionada;

    }


}







```



