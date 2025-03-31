<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

- Espacios (`" "`)
- Tabulaciones (`\t`)
- Saltos de línea (`\n`)
- Retornos de carro (`\r`)

La doble barra invertida (`\\s`) es necesaria porque en Java las barras invertidas dentro de una cadena deben escaparse (`\` se escribe como `\\`). 


| **Expresión** | **Significado** | **Ejemplo** |
|--------------|---------------|------------|
| `\s` | Cualquier espacio en blanco | `"Hola  mundo".replaceAll("\\s", "")` → `"Holamundo"` |
| `\d` | Cualquier dígito (`0-9`) | `"Casa 123".replaceAll("\\d", "")` → `"Casa "` |
| `\w` | Cualquier carácter de palabra (`a-z`, `A-Z`, `0-9`, `_`) | `"Hola_mundo!".replaceAll("\\w", "")` → `"!"` |
| `\W` | Cualquier carácter que **no** sea una palabra | `"Hola, mundo!".replaceAll("\\W", "")` → `"Holamundo"` |
| `\D` | Cualquier carácter que **no** sea un dígito | `"Casa 123".replaceAll("\\D", "")` → `"123"` |
| `.` | Cualquier carácter excepto nueva línea | `"Hola.".replaceAll(".", "-")` → `"----"` |
| `^` | Coincide con el inicio de la cadena | `"Hola mundo".replaceAll("^Hola", "Hey")` → `"Hey mundo"` |
| `$` | Coincide con el final de la cadena | `"Hola mundo".replaceAll("mundo$", "amigo")` → `"Hola amigo"` |

### **Ejemplo avanzado:**
Si queremos eliminar todos los números y caracteres especiales excepto los espacios en una cadena:

```java
public class LimpiarTexto {
    public static void main(String[] args) {
        String texto = "Hola123, ¿cómo estás? #Java 2025";
        String limpio = texto.replaceAll("[^a-zA-Z\\s]", "");
        System.out.println(limpio); // "Hola cómo estás Java"
    }
}
```

Aquí usamos `[^a-zA-Z\\s]` para eliminar todo lo que **no** sea una letra o espacio.
