## Modificar el ejercicio que hemos hecho antes (código que tenéis abajo), para que solicite los valores correctos de inicio y fin (inicio debe de ser menor que fin)

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

## Este ejercicio hace uso del While

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int inicio = 0;
        int fin = 0;

        while (inicio >= fin)
        {
            System.out.println("Introduce el valor de inicio: ");
            inicio = scanner.nextInt();

            System.out.println("Introduce el valor de fin: ");
            fin = scanner.nextInt();

            if (inicio>=fin){
                System.out.println("El valor de fin debe de ser siempre mayor!!!");
            }
        }


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

### Nos tenemos que fijar que en este ejemplo hemos cambiado la estructura de while... por la do... while, ya que tiene más sentido que pidamos los parámetros y por tanto, el código se debe de ejecutar **al menos una vez** para poder introducir los valores del usuario.
```java

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int inicio = 8;
        int fin = 1;

        do{
            System.out.println("Introduce el valor de inicio: ");
            inicio = scanner.nextInt();

            System.out.println("Introduce el valor de fin: ");
            fin = scanner.nextInt();

            if (inicio>=fin){
                System.out.println("El valor de fin debe de ser siempre mayor!!!");
            }
        } while (inicio >= fin);




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