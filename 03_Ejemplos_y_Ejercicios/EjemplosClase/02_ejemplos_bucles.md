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
```java

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Introduce el valor de inicio: ");
        int inicio = scanner.nextInt();

        System.out.print("Introduce el valor de fin: ");
        int fin = scanner.nextInt();

        for (int i = inicio; i <= fin; i++) {
            if (i % 2 == 0) {
                System.out.print(i+ " ");
            }
        }

        scanner.close();
    }

}
```
```Java

// Esto es un ejemplo de código
public class Main {

    public static void imprime(int[][] matriz){
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n_filas = 8;
        int n_columnas = 8;
        int[][] matriz = new int[n_filas][n_columnas];
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                if (i<=j)   {
                    matriz[i][j] = 0;
                }
                else{
                    matriz[i][j] = 1;
                }
            }
        }

        imprime(matriz);

    }
}
/*
TENGO QUE OBTENER:
    0,0  -- 0-2
    2,0  -- 2-2
        {1, 0, 0},
        {1, 1, 0},
        {1, 1, 1}

 */
```


```Java

// Esto es un ejemplo de código
public class Main {

    public static void imprime(int[][] matriz){
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n_filas = 4;
        int n_columnas = 4;
        int[][] matriz = new int[n_filas][n_columnas];
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                if ( i==0 || i ==matriz[i].length-1 || j==0 || j ==matriz[j].length-1)    {
                    matriz[i][j] = 0;
                }
                else{
                    matriz[i][j] = 1;
                }
            }
        }

        imprime(matriz);

    }
}
/*
TENGO QUE OBTENER:

        {0, 0, 0, 0},
        {0, 1, 1, 0},
        {0, 1, 1, 0},
        {0, 0, 0, 0},

        {0, 0, 0, 0, 0, 0, 0, 0},
        {0, 1, 1, 1, 1, 1, 1, 0},
        {0, 1, 0, 0, 0, 0, 1, 0},
        {0, 1, 0, 1, 1, 0, 1, 0},
        {0, 1, 0, 1, 1, 0, 1, 0},
        {0, 1, 0, 0, 0, 0, 1, 0},
        {0, 1, 1, 1, 1, 1, 1, 0},
        {0, 0, 0, 0, 0, 0, 0, 0},


 */
```