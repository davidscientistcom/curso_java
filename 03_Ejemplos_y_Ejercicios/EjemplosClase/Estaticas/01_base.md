```java
public class Main {
    public static void main(String[] args) {
        int[][] matriz = {
                {1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}
        };
        for (int i = 0; i < matriz.length; i++) { // Recorre las filas
            for (int j = 0; j < matriz[i].length; j++) { // Recorre las columnas
                System.out.print(matriz[i][j] + " ");
            }
            System.out.println();
        }
    }
}

```