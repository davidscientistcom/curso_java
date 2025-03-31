```java
public class Main_bak {

    public static void dibujaDeposito(int[][] matriz){
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j]+" ");
            }
            System.out.println();
        }
    }

    public static int[][] crearDeposito(int altura, int anchura){
        return new int[altura][anchura];
    }
    private static int calcularLineasLlenar(int altura, int porcentaje) {
        return (int) Math.ceil((porcentaje / 100.0) * altura);
    }
    private static int[][] llenarLineas(int altura, int anchura, int lineas, int[][] deposito) {
        for (int i = altura-1; i>=altura - lineas; i--) {
            for (int j=0; j<anchura; j++) {
                deposito[i][j] = 1;
            }
        }
        return deposito;
    }

    private static int[][] llenarDeposito(int altura,int anchura, int porcentaje, int[][] deposito) {
        if (porcentaje>=0 && porcentaje<=100) {
            int lineas = calcularLineasLlenar(altura,porcentaje);
            deposito = llenarLineas(altura,anchura,lineas,deposito);
        }
        else{
            System.out.println("Porcentaje inválido");
        }

        return deposito;

    }




    public static void main(String[] args) {
        int anchura = 3;
        int altura = 8;
        int porcentaje = 50;
        int [][] deposito = crearDeposito(altura, anchura);
        deposito = llenarDeposito(altura,anchura,porcentaje,deposito);
        dibujaDeposito(deposito);
    }


}

```