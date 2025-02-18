Lo que tenemos que hacer es :
    -aplicar un descuento a todos los clientes de tipo1, de 100€
    -aplicar un descuento a todos los clientes de tipo2, de 200€



import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> clientes = new ArrayList<>();
        List<String> idClientes = new ArrayList<>();
        List<Double> base = new ArrayList<>();

        clientes.add("David");
        idClientes.add("1_0001");
        base.add(500.25);
        
        clientes.add("Linda");
        idClientes.add("1_0002");
        base.add(700.0);
        
        clientes.add("Toky");
        idClientes.add("2_0001");
        base.add(1000.0);
    }
}
