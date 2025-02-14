MODIFICAR EL EJERCICIO PARA QUE HASTA QUE NO PONGAS UN VALOR DE INICIO Y DE FIN CORRECTO TE DIGA, QUE VUELVAS A INTENTARLO

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Introduce el valor de inicio: ");
        int inicio = scanner.nextInt();

        System.out.print("Introduce el valor de fin: ");
        int fin = scanner.nextInt();

        // Validamos que fin sea mayor o igual que inicio
        if (fin < inicio || fin <0 || inicio < 0) {
            System.out.println("Tienes que poner valores correctos");
        } else {
            // Si los valores son correctos, imprimimos la secuencia
            while (inicio <= fin) {
                System.out.print(inicio+ " ");
                inicio++;
            }
        }

        scanner.close();
    }
}
```