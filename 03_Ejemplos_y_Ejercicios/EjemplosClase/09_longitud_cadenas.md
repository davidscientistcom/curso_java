```JAVA
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Introduce la primera cadena: ");
        String cadena1 = sc.nextLine();

        System.out.print("Introduce la segunda cadena: ");
        String cadena2 = sc.nextLine();

        if (cadena1.length() < cadena2.length()) {
            System.out.println(cadena1.toUpperCase());
        }
        else{
            System.out.println(cadena2.toUpperCase());
        }

    }

}
```