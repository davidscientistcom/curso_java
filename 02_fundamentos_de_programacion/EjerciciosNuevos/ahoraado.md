```JAVA

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Random;
import java.util.Scanner;

public class AhorcadoConMatriz {
    
    // MATRIZ (array bidimensional de String) que representa las etapas del Ahorcado
    // Cada fila de HANGMAN_PICS es un array de líneas que componen el dibujo.
    private static final String[][] HANGMAN_PICS = {
        {   // Etapa 0: Sin fallos
            "  +---+",
            "  |   |",
            "      |",
            "      |",
            "      |",
            "      |",
            "========="
        },
        {   // Etapa 1: 1 fallo
            "  +---+",
            "  |   |",
            "  O   |",
            "      |",
            "      |",
            "      |",
            "========="
        },
        {   // Etapa 2: 2 fallos
            "  +---+",
            "  |   |",
            "  O   |",
            "  |   |",
            "      |",
            "      |",
            "========="
        },
        {   // Etapa 3: 3 fallos
            "  +---+",
            "  |   |",
            "  O   |",
            " /|   |",
            "      |",
            "      |",
            "========="
        },
        {   // Etapa 4: 4 fallos
            "  +---+",
            "  |   |",
            "  O   |",
            " /|\\  |",
            "      |",
            "      |",
            "========="
        },
        {   // Etapa 5: 5 fallos
            "  +---+",
            "  |   |",
            "  O   |",
            " /|\\  |",
            " /    |",
            "      |",
            "========="
        },
        {   // Etapa 6: 6 fallos (último, ahorcado completo)
            "  +---+",
            "  |   |",
            "  O   |",
            " /|\\  |",
            " / \\  |",
            "      |",
            "========="
        }
    };

    // Número máximo de fallos permitidos (coincide con la longitud de HANGMAN_PICS - 1)
    private static final int MAX_FALLAS = HANGMAN_PICS.length - 1; 
    
    // Scanner global para leer de consola
    private static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        // Ejemplo: lista de palabras para adivinar (podrías mejorarlo pidiendo al usuario)
        List<String> listaPalabras = Arrays.asList("PROGRAMACION", "JAVA", "AHORCADO", "MATRIZ", "HANGMAN");
        
        System.out.println("=== JUEGO DEL AHORCADO ===");
        System.out.println("Intenta adivinar la palabra antes de que sea demasiado tarde.\n");

        // Elegimos una palabra al azar
        String palabraSecreta = elegirPalabraAleatoria(listaPalabras);
        
        // Lógica principal del juego
        jugarAhorcado(palabraSecreta);

        sc.close();
    }

    /**
     * Método principal que gestiona el juego del Ahorcado:
     * - Lleva la cuenta de las fallas.
     * - Muestra el estado del ahorcado y las letras adivinadas.
     */
    private static void jugarAhorcado(String palabraSecreta) {
        // Pasamos la palabra a mayúsculas (ya está en mayúsculas en la lista, pero por si acaso)
        palabraSecreta = palabraSecreta.toUpperCase();

        // Arreglo de chars para representar qué letras se han descubierto
        // Se inicializa con '_' en cada posición
        char[] progreso = new char[palabraSecreta.length()];
        Arrays.fill(progreso, '_');
        
        // Llevamos la cuenta de fallos
        int fallos = 0;
        
        // Guardaremos aquí las letras ya intentadas, para no repetir
        ArrayList<Character> letrasIntentadas = new ArrayList<>();
        
        // Bucle principal (mientras no se complete la palabra y no se excedan los fallos)
        while (true) {
            // Mostramos el estado actual
            mostrarEstadoAhorcado(fallos);
            mostrarProgresoPalabra(progreso);
            mostrarLetrasIntentadas(letrasIntentadas);

            // Verificamos si el jugador ya adivinó la palabra completa
            if (Arrays.equals(progreso, palabraSecreta.toCharArray())) {
                System.out.println("¡Felicidades! Has adivinado la palabra: " + palabraSecreta);
                break;
            }

            // Si excedimos el número de fallos permitidos, termina el juego
            if (fallos >= MAX_FALLAS) {
                System.out.println("¡Has perdido! La palabra secreta era: " + palabraSecreta);
                break;
            }

            // Pedimos al usuario que ingrese una letra
            char letra = pedirLetra();

            // Comprobamos si ya fue intentada
            if (letrasIntentadas.contains(letra)) {
                System.out.println("Ya has intentado la letra '" + letra + "'. ¡Prueba con otra!");
                continue; // Volvemos al siguiente intento sin penalizar
            } 
            // Añadimos la letra a la lista de intentadas
            letrasIntentadas.add(letra);

            // Revisamos si la letra está en la palabra
            boolean acierto = false;
            for (int i = 0; i < palabraSecreta.length(); i++) {
                if (palabraSecreta.charAt(i) == letra) {
                    progreso[i] = letra; // Revelamos la letra en el progreso
                    acierto = true;
                }
            }

            // Si no hubo ningún acierto, incrementamos los fallos
            if (!acierto) {
                fallos++;
                System.out.println("Letra incorrecta. ¡Cuidado!");
            }
        }
    }

    /**
     * Muestra en consola el dibujo ASCII del Ahorcado, según el número de fallos.
     */
    private static void mostrarEstadoAhorcado(int fallos) {
        // "fallos" determina qué fila (o sub-array) de HANGMAN_PICS usar
        String[] dibujo = HANGMAN_PICS[fallos];
        for (String linea : dibujo) {
            System.out.println(linea);
        }
    }

    /**
     * Imprime el progreso de la palabra, sustituyendo las letras desconocidas por '_'.
     * Ejemplo: P _ O _ _ A _ I _ N
     */
    private static void mostrarProgresoPalabra(char[] progreso) {
        System.out.println("\nPalabra: ");
        for (char c : progreso) {
            System.out.print(c + " ");
        }
        System.out.println("\n");
    }

    /**
     * Muestra las letras que el usuario ya ha intentado (acertadas o falladas).
     */
    private static void mostrarLetrasIntentadas(ArrayList<Character> letrasIntentadas) {
        System.out.println("Letras intentadas: " + letrasIntentadas);
    }

    /**
     * Solicita una letra al usuario y la devuelve en mayúscula.
     * Si el usuario introduce más de un caracter, se toma solo el primero.
     */
    private static char pedirLetra() {
        System.out.print("Introduce una letra: ");
        String entrada = sc.nextLine().toUpperCase().trim(); // mayúsculas, quitamos espacios
        if (entrada.isEmpty()) {
            return pedirLetra(); // Si está vacío, volvemos a pedir
        }
        // Tomamos solo el primer caracter válido
        return entrada.charAt(0);
    }

    /**
     * Devuelve una palabra aleatoria de una lista dada.
     */
    private static String elegirPalabraAleatoria(List<String> listaPalabras) {
        Random random = new Random();
        int index = random.nextInt(listaPalabras.size());
        return listaPalabras.get(index);
    }
}
```