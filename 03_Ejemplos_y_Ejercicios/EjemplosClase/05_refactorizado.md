# Ejercicio: 
Refactorización de un Analizador de Texto

## Objetivo
Aprender a identificar código repetitivo y refactorizarlo usando funciones simples. Este ejercicio utiliza solo arrays básicos y lógica sencilla.

## Versión Inicial (Código sin refactorizar)

```java
import java.util.Scanner;

public class AnalizadorTextoSimple {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("=== ANALIZADOR DE TEXTOS BÁSICO ===");
        System.out.print("Introduce un texto: ");
        String texto = scanner.nextLine();
        
        // Análisis 1: Contar vocales
        int contadorVocales = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = Character.toLowerCase(texto.charAt(i));
            if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                contadorVocales++;
            }
        }
        System.out.println("Número de vocales: " + contadorVocales);
        
        // Análisis 2: Contar consonantes
        int contadorConsonantes = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = Character.toLowerCase(texto.charAt(i));
            if ((c >= 'a' && c <= 'z') && !(c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u')) {
                contadorConsonantes++;
            }
        }
        System.out.println("Número de consonantes: " + contadorConsonantes);
        
        // Análisis 3: Contar palabras
        String[] palabras = texto.trim().split("\\s+");
        int contadorPalabras = texto.trim().isEmpty() ? 0 : palabras.length;
        System.out.println("Número de palabras: " + contadorPalabras);
        
        // Análisis 4: Contar letras mayúsculas
        int contadorMayusculas = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = texto.charAt(i);
            if (c >= 'A' && c <= 'Z') {
                contadorMayusculas++;
            }
        }
        System.out.println("Número de letras mayúsculas: " + contadorMayusculas);
        
        // Análisis 5: Calcular longitud promedio de palabras
        if (contadorPalabras > 0) {
            int totalCaracteres = 0;
            for (String palabra : palabras) {
                totalCaracteres += palabra.length();
            }
            double promedio = (double) totalCaracteres / contadorPalabras;
            System.out.printf("Longitud promedio de palabras: %.2f caracteres\n", promedio);
        } else {
            System.out.println("No hay palabras para calcular el promedio");
        }
        
        scanner.close();
    }
}
```

## Versión Refactorizada (Con funciones simples)

```java
import java.util.Scanner;

public class AnalizadorTextoRefactorizado {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("=== ANALIZADOR DE TEXTOS BÁSICO ===");
        System.out.print("Introduce un texto: ");
        String texto = scanner.nextLine();
        
        // Llamadas a funciones para cada análisis
        int vocales = contarVocales(texto);
        int consonantes = contarConsonantes(texto);
        String[] palabras = obtenerPalabras(texto);
        int totalPalabras = palabras.length;
        int mayusculas = contarMayusculas(texto);
        double promedioPalabras = calcularPromedioPalabras(palabras);
        
        // Mostrar resultados
        mostrarResultados(vocales, consonantes, totalPalabras, mayusculas, promedioPalabras);
        
        scanner.close();
    }
    
    /**
     * Cuenta el número de vocales en un texto
     */
    public static int contarVocales(String texto) {
        int contador = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = Character.toLowerCase(texto.charAt(i));
            if (esVocal(c)) {
                contador++;
            }
        }
        return contador;
    }
    
    /**
     * Determina si un carácter es una vocal
     */
    public static boolean esVocal(char c) {
        c = Character.toLowerCase(c);
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
    
    /**
     * Cuenta el número de consonantes en un texto
     */
    public static int contarConsonantes(String texto) {
        int contador = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = Character.toLowerCase(texto.charAt(i));
            if ((c >= 'a' && c <= 'z') && !esVocal(c)) {
                contador++;
            }
        }
        return contador;
    }
    
    /**
     * Divide un texto en palabras y retorna un array
     */
    public static String[] obtenerPalabras(String texto) {
        if (texto.trim().isEmpty()) {
            return new String[0];
        }
        return texto.trim().split("\\s+");
    }
    
    /**
     * Cuenta el número de letras mayúsculas en un texto
     */
    public static int contarMayusculas(String texto) {
        int contador = 0;
        for (int i = 0; i < texto.length(); i++) {
            char c = texto.charAt(i);
            if (c >= 'A' && c <= 'Z') {
                contador++;
            }
        }
        return contador;
    }
    
    /**
     * Calcula la longitud promedio de las palabras
     */
    public static double calcularPromedioPalabras(String[] palabras) {
        if (palabras.length == 0) {
            return 0;
        }
        
        int totalCaracteres = 0;
        for (String palabra : palabras) {
            totalCaracteres += palabra.length();
        }
        
        return (double) totalCaracteres / palabras.length;
    }
    
    /**
     * Muestra los resultados de todos los análisis
     */
    public static void mostrarResultados(int vocales, int consonantes, int palabras, 
                                      int mayusculas, double promedioPalabras) {
        System.out.println("Número de vocales: " + vocales);
        System.out.println("Número de consonantes: " + consonantes);
        System.out.println("Número de palabras: " + palabras);
        System.out.println("Número de letras mayúsculas: " + mayusculas);
        
        if (palabras > 0) {
            System.out.printf("Longitud promedio de palabras: %.2f caracteres\n", promedioPalabras);
        } else {
            System.out.println("No hay palabras para calcular el promedio");
        }
    }
}
```
