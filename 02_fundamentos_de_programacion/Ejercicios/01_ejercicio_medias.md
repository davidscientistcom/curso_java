## Dadas las notas de un alumno, quiero que me digáis cual es la nota media de dicho alumno.

Esta sería una primera versión con un for **normal**

```java

import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {    

        List<Double> notas = new ArrayList<>();

        notas.add(8.4);        
        notas.add(6.1);
        notas.add(3.1);
        notas.add(5.1);
        notas.add(8.0);

        Double total = 0.0;

        for (int i = 0; i < notas.size(); i++) {
            total += notas.get(i);
        }

        Double media = total / notas.size();

        System.out.println(media);

}
}
```

En este ejemplo podemos observar como usamos la estructura for-each, en lugar del for normal, porque no necesito para nada su i, sino que tengo que recorrer todos los valores de la colección.

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {

        List<Double> notas = new ArrayList<>();

        notas.add(8.4);
        notas.add(9.2);
        notas.add(6.1);
        notas.add(3.1);
        notas.add(5.1);
        notas.add(8.0);

        Double total = 0.0;

        for (Double nota : notas) {
            total+=nota;
        }

        Double media = total / notas.size();

        System.out.println(media);




}
}



```
