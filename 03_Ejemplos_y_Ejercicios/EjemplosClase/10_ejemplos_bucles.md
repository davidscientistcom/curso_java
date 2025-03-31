### Ejemplo While

```Java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        boolean detectado = false;
        while(detectado == false) {
            System.out.println("Introduce un número ");
            int num = scanner.nextInt();
            if (num % 2 == 0) {
                System.out.println(num);
                detectado = true;
            }
        }
        scanner.close();

    }

}
```

```JAVA
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        int num_pares = 0;
        int suma=0;
        while(num_pares<2) {
            System.out.println("Introduce un número ");
            int num = scanner.nextInt();
            if (num % 2 == 0) {
                num_pares++;
                suma += num;
            }
        }
        System.out.println("La suma es: "+ suma);
        scanner.close();

    }

}
```