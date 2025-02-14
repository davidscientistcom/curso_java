```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Introduce el primer número: ");
        int numero1 = sc.nextInt();

        System.out.print("Introduce el segundo número: ");
        int numero2 = sc.nextInt();

        if (numero1 > numero2) {
            System.out.println("El mayor es el primer número que es : " + numero1);
        } else if (numero2 > numero1) {
            System.out.println("El mayor es el segundo número que es : " + numero2);
        }
        else {
            System.out.println("Los dos números introducidos son iguales");
        }
        sc.close();

    }
}

```