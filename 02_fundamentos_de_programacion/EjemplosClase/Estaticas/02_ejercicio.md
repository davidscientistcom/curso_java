```java
public class Main_bak {

    public static void muestraMatriz(int[][] matriz){
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j]+" ");
            }
            System.out.println();
        }
    }

    /* Quiero crear la siguiente Matriz */
    /*
        {1, 0, 1},
        {0, 0, 0},
        {1, 0, 1}
     */

    public static void main(String[] args) {
        int[][] matriz = new int[5][5]; // Matriz de 3x3

        for (int i = 0; i < matriz.length; i++) { // Recorre las filas
            for (int j = 0; j < matriz[i].length; j++) { // Recorre las columnas
                if (i ==0 && j ==0 ) {
                    matriz[i][j] = 1;
                }
                if (i==0 && j == matriz.length-1 ) {
                    matriz[i][j] = 1;
                }
                if (j == 0 && i == matriz.length-1 ) {
                    matriz[i][j] = 1;
                }
                if (j == matriz.length-1 && i == matriz.length-1 ) {
                    matriz[i][j] = 1;
                }
            }
        }
        muestraMatriz(matriz);

    }
}

// 1.- De la matriz que nos han dado, necesitamos eliminar los pares, para ello los pondremos a 0. Respectando la diagonal principal.
// 2.- Haced un programa que en base a los datos que os han quedado en la matriz, calculeis la media de los valores que están por debajo de la diagonal

```