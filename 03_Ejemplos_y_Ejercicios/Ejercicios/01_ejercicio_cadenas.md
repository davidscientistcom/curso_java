## Ejercicio de cadenas

Dado este ejercicio, el problema es: Dime el número de digitos que aparecen:

**PISTA** Se puede usar: replaceAll

public class Main {
    public static void main(String[] args) {
        String  texto = "Este es mi 11 4 texto de prueba";
        

    }


import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        String  texto = "Este es mi 11 4 texto 8855 8de prueba";
        String digitos = texto.replaceAll("\\D", "");
        System.out.println("Los dígitos encontrados son: "+ digitos +" que hace un total de "+digitos.length()+" digitos");


    }
}


