```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        int fin = 5;
        int inicio = 0;

        while(inicio!=fin) {
            System.out.println(inicio);
            inicio++; // inicio = inicio+1
        }

    }
}
```

```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        int fin = 5;
        int inicio = 0;

        while(inicio!=fin) {
            inicio++; // inicio = inicio+1
            System.out.println(inicio);

        }

    }
}
```
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        int fin = 5;
        int inicio = 1;

        while(inicio!=(fin+1)) {
            System.out.println(inicio);
            inicio++; // inicio = inicio+1
        }

    }
}
```
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