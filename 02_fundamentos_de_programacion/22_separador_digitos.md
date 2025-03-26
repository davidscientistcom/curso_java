## ¿Qué significa `100_000`?

Es exactamente igual que escribir `100000`.

La **barra baja `_`** se usa solo para **mejorar la legibilidad** de los números largos, como harías visualmente con los miles.

```java
int n1 = 100000;
int n2 = 100_000;  // Exactamente lo mismo

System.out.println(n1 == n2);  // true
```

## ¿Dónde se puede usar?

- En **enteros**: `int`, `long`
- En **reales**: `double`, `float`
- También en **valores binarios, hexadecimales y octales**

### Ejemplos válidos:
```java
int millones = 1_000_000;
long tarjetaCredito = 1234_5678_9012_3456L;
float pi = 3.14_15F;
int binario = 0b1010_1100;
```

##  Ejemplos inválidos:

No se puede:
- Empezar o acabar un número con `_`
- Ponerla justo antes o después del punto decimal

```java
// int error = _1000;       // inválido
// float error2 = 3._14F;   // inválido
```
