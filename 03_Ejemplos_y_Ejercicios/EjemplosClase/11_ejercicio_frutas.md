```Java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
       /*
       QUIERO HACER UNA LISTA DE LA COMPRA EN LA QUE VAMOS A IR INTRODUCIENDO FRUTAS
       PERO NO PUEDO INTRODUCIR FRUTAS SI YA EXISTE
       USAR UN SCANNER.
       PARA PARAR DE PONER FRUTAS, PONED FIN
        */

        List<String> palabras = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        boolean terminado = false;
        while (!terminado){
            System.out.println("Escribe uma palabra: ");
            String palabra = scanner.nextLine();
            palabra = palabra.toLowerCase();
            if (!palabra.equals("fin"))
            {
                if (!palabras.contains(palabra)) {
                    palabras.add(palabra);
                }
                else{
                    System.out.println("Esa palabra ya está registrada");
                }
            }
            else{
                terminado =true;

            }
        }
        System.out.println("Las palabras introducidas son:");
        for (String p : palabras) {
            System.out.println(p);
        }

        scanner.close();


    }

}
```