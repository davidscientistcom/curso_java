```Java
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Random;

public class Ahorcado {
    public static void main(String[] args) {
        // Lista de palabras disponibles
        ArrayList<String> palabras = new ArrayList<String>();
        palabras.add("java");
        palabras.add("programacion");
        palabras.add("ahorcado");
        palabras.add("ejemplo");
        palabras.add("computadora");

        // Selecciona una palabra al azar de la lista
        Random random = new Random();
        String palabra = palabras.get(random.nextInt(palabras.size()));

        // Array para guardar el estado actual de la palabra (guiones bajos inicialmente)
        char[] estado = new char[palabra.length()];
        for (int i = 0; i < estado.length; i++) {
            estado[i] = '_';
        }

        // ArrayList para almacenar las letras ya introducidas por el usuario
        ArrayList<Character> letrasUsadas = new ArrayList<Character>();

        // Número de intentos permitidos
        int intentos = 6;
        Scanner scanner = new Scanner(System.in);

        // Bucle principal del juego
        while (intentos > 0) {
            System.out.println("\nPalabra: " + mostrarEstado(estado));
            System.out.println("Intentos restantes: " + intentos);
            System.out.println("Letras usadas: " + letrasUsadas);
            System.out.print("Introduce una letra: ");
            
            String entrada = scanner.nextLine();
            // Validar que se introduzca exactamente una letra
            if (entrada.length() != 1) {
                System.out.println("Por favor, introduce solo una letra.");
                continue;
            }
            char letra = entrada.charAt(0);

            // Si la letra ya fue usada, se notifica y se pide otra
            if (letrasUsadas.contains(letra)) {
                System.out.println("Ya has usado esa letra. Intenta con otra.");
                continue;
            }
            // Añadir la letra a la lista de usadas
            letrasUsadas.add(letra);

            // Variable para determinar si se ha acertado la letra en la palabra
            boolean acierto = false;
            for (int i = 0; i < palabra.length(); i++) {
                if (palabra.charAt(i) == letra) {
                    estado[i] = letra;
                    acierto = true;
                }
            }
            if (!acierto) {
                intentos--;
                System.out.println("La letra '" + letra + "' no está en la palabra.");
            }

            // Comprobar si la palabra ha sido adivinada por completo
            if (!new String(estado).contains("_")) {
                System.out.println("\n¡Felicidades! Has adivinado la palabra: " + palabra);
                break;
            }
        }
        
        // Si se han agotado los intentos, se muestra la palabra correcta
        if (intentos == 0) {
            System.out.println("\nSe te han acabado los intentos. La palabra era: " + palabra);
        }
        
        scanner.close();
    }
    
    // Método auxiliar para mostrar el estado actual de la palabra con espacios
    public static String mostrarEstado(char[] estado) {
        StringBuilder sb = new StringBuilder();
        for (char c : estado) {
            sb.append(c).append(" ");
        }
        return sb.toString();
    }
}
```
