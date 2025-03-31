```java

/*
            DISEÑAR UN JUEGO EN EL QUE SE GENERE UN NÚMERO ALEATORIO ENTRE 1 Y 100
            NOS PEDIRÁ UN NÚMERO
            EL PROGRAMA NOS DIRÁ SI EL NÚMERO SECRETO ES MENOR O MAYOR
            Y YO VOLVERÉ A PONER NÚMERO
            - HABRÁ DOS POSIBLES SOLUCIONES.
                - ENCUENTRO EL NÚMERO Y GANO Y ME TIENE QUE DECIR FELICITACIONES!
                - GASTO LOS INTENTOS Y ME DICE, LO SIENTO, OTRA VEZ SERÁ.
            - EL LÍMITE DE INTENTOS DEBERÁ DE SER DEFINIDO POR VARIABLE ASÍ COMO LOS LÍMITES DEL ALEATORIO

*/

import java.util.Scanner;
import java.util.Random;

        public class Main {
            public static void main(String[] args) {

                int limiteInferior = 1;
                int limiteSuperior = 100;
                int intentosMaximos = 7;


                Random rand = new Random();
                int numeroSecreto = rand.nextInt(limiteSuperior - limiteInferior + 1) + limiteInferior;


                Scanner scanner = new Scanner(System.in);
                int intentoUsuario;
                int intentosRealizados = 0;
                boolean acertado = false;

                System.out.println("Intenta averiguar el número que hay entre " + limiteInferior + " y " + limiteSuperior + ".");
                System.out.println("Tienes " + intentosMaximos + " intentos para adivinarlo.");


                 do{
                    System.out.print("Introduce tu número: ");
                    intentoUsuario = scanner.nextInt();
                    intentosRealizados++;

                    if (intentoUsuario == numeroSecreto) {
                        acertado = true;
                        System.out.println("¡Felicidades! Has acertado el número en " + intentosRealizados + " intentos).");
                    } else if (intentoUsuario < numeroSecreto) {
                        System.out.println("El número secreto es MAYOR.");
                    } else {
                        System.out.println("El número secreto es MENOR.");
                    }
                }while ((intentosRealizados < intentosMaximos) && !acertado);

                if (!acertado) {
                    System.out.println(" Lo siento, te has quedado sin intentos. El número era: " + numeroSecreto);
                }


                scanner.close();

            }

        }






```