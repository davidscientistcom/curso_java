A continuación tienes una **implementación simplificada** de **Hundir la Flota (Battleship)** en Java, **sin** crear clases adicionales. Todo está contenido en una sola clase, utilizando **métodos estáticos** para organizar el código y mantenerlo más legible. Es un juego de **un solo tablero** en el que el programa coloca automáticamente unos barcos en la matriz, y el usuario intenta encontrarlos haciendo disparos por coordenadas (fila y columna). Cuando el usuario acierte todas las posiciones de los barcos, habrá ganado.

> **Nota:** Esta es una versión **simplificada** del juego. Solo tiene un tablero, el programa coloca los barcos, y el usuario dispara hasta hundirlos o agotar un número de disparos, etc. Se pueden hacer muchas extensiones (modo jugador vs. jugador, barcos de distinto tamaño, controles de validación, etc.), pero la siguiente es la base para un “mini-Hundir la Flota” funcional.



# Código Completo

```java
import java.util.Random;
import java.util.Scanner;

public class HundirLaFlotaSimple {
    
    // Parámetros del tablero
    private static final int TAMANIO = 5;     // Ej: 5x5
    private static final int NUM_BARCOS = 3;  // Cuántos barcos colocamos (un barco = una sola celda para simplificar)
    
    // Representaciones en el tablero
    private static final char AGUA = '.';     // No visitado, no disparado
    private static final char BARCO = 'B';    // Celda con barco (oculto al jugador normalmente)
    private static final char TOCADO = 'X';   // El usuario ha disparado aquí y había barco
    private static final char FALLO = 'O';    // El usuario ha disparado aquí y no había barco

    // Tablero donde se almacenan barcos y disparos
    //    - El usuario no ve directamente dónde están los barcos, pero
    //      nosotros lo usaremos internamente para saber si acierta.
    private static char[][] tablero = new char[TAMANIO][TAMANIO];

    // Scanner para leer entrada del usuario
    private static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        System.out.println("=== HUNDIR LA FLOTA (VERSION SIMPLE) ===\n");
        
        // 1. Inicializar tablero con agua
        inicializarTablero();

        // 2. Colocar los barcos en posiciones aleatorias
        colocarBarcosAleatoriamente();

        // 3. Bucle principal del juego
        juego();

        // Cerrar Scanner
        sc.close();
    }

    /**
     * Inicializa el tablero con agua ('.') en todas las posiciones.
     */
    private static void inicializarTablero() {
        for (int i = 0; i < TAMANIO; i++) {
            for (int j = 0; j < TAMANIO; j++) {
                tablero[i][j] = AGUA;
            }
        }
    }

    /**
     * Coloca NUM_BARCOS "barcos" (1 celda) de manera aleatoria en el tablero.
     * Marcamos esas celdas con 'B'.
     */
    private static void colocarBarcosAleatoriamente() {
        Random rand = new Random();
        int colocados = 0;

        while (colocados < NUM_BARCOS) {
            int fila = rand.nextInt(TAMANIO);
            int columna = rand.nextInt(TAMANIO);

            if (tablero[fila][columna] == AGUA) {
                tablero[fila][columna] = BARCO;
                colocados++;
            }
        }
    }

    /**
     * Lógica principal del juego: el usuario dispara hasta hundir todos los barcos
     * o hasta que decida salir o (opcionalmente) limitamos intentos.
     */
    private static void juego() {
        // (Opcional) Podríamos establecer un número máximo de disparos, si se desea
        int intentosMax = 15;  // si quieres probar un límite en los disparos
        int disparosRealizados = 0;

        while (true) {
            // 1. Mostramos el tablero para el usuario (sin barcos ocultos)
            mostrarTableroParaUsuario();

            // 2. Comprobamos si se han hundido todos los barcos
            if (todosLosBarcosHundidos()) {
                System.out.println("\n¡FELICIDADES! Has hundido todos los barcos.");
                break;
            }

            // 3. Comprobamos si llegamos al límite de disparos (opcional)
            disparosRealizados++;
            if (disparosRealizados > intentosMax) {
                System.out.println("\nHas excedido el número de disparos permitido. ¡GAME OVER!");
                break;
            }

            // 4. Leemos la coordenada de disparo del usuario
            System.out.println("\nDISPARO #" + disparosRealizados + " (máx " + intentosMax + ")");
            System.out.print("Introduce la fila (0-" + (TAMANIO-1) + "): ");
            int fila = leerEntero();
            System.out.print("Introduce la columna (0-" + (TAMANIO-1) + "): ");
            int col = leerEntero();

            // 5. Validamos la coordenada y resolvemos el disparo
            if (!coordenadaValida(fila, col)) {
                System.out.println("Coordenadas inválidas. Inténtalo de nuevo.");
                continue;
            }
            resolverDisparo(fila, col);
        }
    }

    /**
     * Muestra el tablero al usuario, pero sin revelar dónde están los barcos (B).
     * - Agua sin disparar: '.'
     * - Disparo fallido: 'O'
     * - Disparo acertado: 'X'
     */
    private static void mostrarTableroParaUsuario() {
        System.out.println("\n   TABLERO ACTUAL");
        // Encabezado de columnas
        System.out.print("    ");
        for (int c = 0; c < TAMANIO; c++) {
            System.out.print(c + " ");
        }
        System.out.println();

        // Filas
        for (int i = 0; i < TAMANIO; i++) {
            System.out.print(i + " | ");  // número de fila
            for (int j = 0; j < TAMANIO; j++) {
                // Si en el tablero hay 'B', para el usuario debe verse como agua '.', 
                // a menos que haya sido descubierto (X).
                // Pero nuestra lógica es simple: 
                // - si es BARCO ('B'), se muestra como '.'
                // - si es TOCADO ('X'), se muestra 'X'
                // - si es FALLO ('O'), se muestra 'O'
                // - si es AGUA ('.'), se muestra '.'
                if (tablero[i][j] == BARCO) {
                    System.out.print(AGUA + " ");
                } else {
                    System.out.print(tablero[i][j] + " ");
                }
            }
            System.out.println();
        }
    }

    /**
     * Comprueba si en el tablero ya no quedan barcos sin tocar (es decir, si
     * todas las celdas 'B' han sido convertidas en 'X').
     */
    private static boolean todosLosBarcosHundidos() {
        for (int i = 0; i < TAMANIO; i++) {
            for (int j = 0; j < TAMANIO; j++) {
                if (tablero[i][j] == BARCO) {
                    return false; // Aún queda al menos un barco sin hundir
                }
            }
        }
        return true;
    }

    /**
     * Resuelve el disparo del usuario en la posición (fila, col).
     * - Si ya estaba tocado/fallado, avisamos
     * - Si hay un barco ('B'), lo cambiamos a 'X' (tocado)
     * - Si es agua, lo cambiamos a 'O' (fallo)
     */
    private static void resolverDisparo(int fila, int col) {
        char estado = tablero[fila][col];
        if (estado == TOCADO || estado == FALLO) {
            System.out.println("Ya has disparado aquí antes. ¡No pasa nada!");
        } else if (estado == BARCO) {
            // ¡Acertó!
            tablero[fila][col] = TOCADO;
            System.out.println("¡TOCADO!");
        } else if (estado == AGUA) {
            // Fallaste
            tablero[fila][col] = FALLO;
            System.out.println("AGUA... fallaste.");
        }
    }

    /**
     * Lee un entero de consola. Si hay error de formato, se vuelve a pedir.
     */
    private static int leerEntero() {
        while (true) {
            try {
                int numero = Integer.parseInt(sc.nextLine());
                return numero;
            } catch (NumberFormatException e) {
                System.out.print("Valor inválido. Introduce un número entero: ");
            }
        }
    }

    /**
     * Verifica si la coordenada (fila, col) está dentro del tablero.
     */
    private static boolean coordenadaValida(int fila, int col) {
        return (fila >= 0 && fila < TAMANIO && col >= 0 && col < TAMANIO);
    }
}
```



## Explicación Paso a Paso

1. **Constantes y Variables Globales**  
   - `TAMANIO = 5`: El tablero es 5x5.  
   - `NUM_BARCOS = 3`: Se colocan 3 “mini-barcos” (una sola celda cada uno) de forma aleatoria.  
   - `AGUA = '.'`, `BARCO = 'B'`, `TOCADO = 'X'`, `FALLO = 'O'`: símbolos para representar estados de las celdas.  
   - `tablero[][]`: matriz `char` de 5x5 donde se coloca la información.

2. **Método `main`**  
   - Imprime un mensaje inicial.  
   - Llama a `inicializarTablero()` (para que todo empiece con `'.'`).  
   - Llama a `colocarBarcosAleatoriamente()` (para poner 3 barcos en celdas aleatorias).  
   - Llama a `juego()` para iniciar el bucle principal.  
   - Finalmente, cierra el `Scanner`.

3. **`inicializarTablero()`**  
   - Recorre la matriz y pone `AGUA (.)` en todas las posiciones.  
   - Con esto, el tablero empieza “vacío” desde el punto de vista del usuario.

4. **`colocarBarcosAleatoriamente()`**  
   - Usamos `Random` para obtener coordenadas aleatorias (fila, columna).  
   - Si la posición está en `AGUA`, la cambiamos a `BARCO (B)`.  
   - Repetimos hasta colocar los 3 barcos (`NUM_BARCOS`).

5. **`juego()`**  
   - Este método controla la **lógica principal** de los disparos.  
   - Un **bucle `while(true)`** se encarga de:  
     1. Mostrar el tablero al usuario (`mostrarTableroParaUsuario()`), ocultando las posiciones reales de los barcos.  
     2. Comprobar si ya hundimos todos los barcos (`todosLosBarcosHundidos()`). Si sí, se muestra “¡FELICIDADES!” y se rompe el bucle.  
     3. (Opcional) Controlar un número máximo de disparos (`intentosMax = 15`).  
     4. Pedir al usuario coordenadas (fila y columna) con `leerEntero()`.  
     5. Verificar si son válidas; si no, continuamos.  
     6. Llamar a `resolverDisparo(fila, col)` para ver si es TOCADO o FALLÓ.

6. **`mostrarTableroParaUsuario()`**  
   - Imprime la **matriz** para el usuario, pero si una celda tiene `BARCO (B)`, la mostramos como `AGUA (.)` para **ocultar** la ubicación del barco.  
   - Si la celda tiene `X` (tocado), `O` (fallo) o `.` (agua sin disparar), lo mostramos tal cual.

7. **`todosLosBarcosHundidos()`**  
   - Recorre el tablero buscando si existe alguna celda con `BARCO (B)`.  
   - Si no encuentra ninguna, devuelve `true`. Significa que todas fueron tocadas y se convirtieron en `X`.

8. **`resolverDisparo(fila, col)`**  
   - Mira el contenido de `tablero[fila][col]`.  
   - Si ya era `X` o `O`, avisamos de que ya se había disparado ahí.  
   - Si era `B`, cambiamos a `X` (tocado) y avisamos “¡TOCADO!”.  
   - Si era `'.'`, cambiamos a `O` (fallo) y avisamos “AGUA”.

9. **`leerEntero()`**  
   - Método de utilidad para leer un entero controlando la excepción `NumberFormatException`.  
   - Si se produce error, se pide de nuevo al usuario.

10. **`coordenadaValida(fila, col)`**  
   - Comprueba si `(fila, col)` está dentro del rango `[0, TAMANIO-1]`.



## Ejemplo de Ejecución (Flujo Simplificado)

1. El programa inicia, crea un tablero 5x5, coloca 3 barcos en posiciones aleatorias.
2. Muestra un tablero así (sin barcos a la vista, todos `.`):
   ```
   0 1 2 3 4
 0 . . . . .
 1 . . . . .
 2 . . . . .
 3 . . . . .
 4 . . . . .
   ```
3. El usuario elige disparar. Por ejemplo: fila=2, col=3
   - Si allí había un barco, se muestra “¡TOCADO!” y en el tablero saldrá `X` en esa posición.
   - Si no había, se muestra “AGUA” y aparecerá un `O`.
4. Cada turno se verifica si quedan barcos (`'B'`) sin tocar (`'X'`).
5. Cuando no queden barcos, el usuario gana. Si se exceden los disparos permitidos (15 en el ejemplo), “GAME OVER”.



## Posibles Extensiones

- **Barcos de varios tamaños** (por ejemplo, un barco de 3 celdas, otro de 2 celdas, etc.).  
- **Ordenador vs. Usuario**: Dos tableros, uno para el usuario y otro para el ordenador, y turnos alternos.  
- **Validaciones más estrictas**: No permitir que se coloquen barcos solapados (si tienen varias celdas).  
- **Interfaz gráfica**: Migrar todo a un `JFrame` con botones o similar.  
- **Puntajes** o **estadísticas** de partidas ganadas/perdidas.

Con esto tienes una **versión básica** de Hundir la Flota, que demuestra:
- Manejo de **matrices** (`char[][]`).  
- **Bucles** para colocar barcos y disparar.  
- **Métodos estáticos** para refactorizar la lógica.  
- **Lectura de consola** y **control** de datos introducidos por el usuario.  

¡Disfruta probando y ampliando este “mini-Hundir la Flota”!