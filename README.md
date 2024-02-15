<h1 align="center"> Xor </h1>

La compuerta lógica XOR, también conocida como exclusiva OR, es un componente fundamental en la lógica digital y se construye mediante la combinación de compuertas lógicas Not, And, y Or. La función XOR produce un resultado verdadero (1/High) solo cuando una y solo una de las entradas es verdadera.
<h4>Código:</h4>

```ruby
/**
 * Exclusive-or gate:
 * out = (not(a) and b) or (a and not(b))
 */
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Not(in=a, out=sal1);
    Not(in=b, out=sal2);
    And(a=sal1, b=b, out=sal3);
    And(a=a, b=sal2, out=sal4);
    Or(a=sal3, b=sal4, out=out);
}
```
<h4>Diagrama:</h4>

![Xor](https://github.com/Fernando2240/Grupo-Megahertz/assets/92164946/24804705-2da4-4bb4-bf67-3c26cca0383e)
<h1 align="center"> Mux </h1>
La compuerta lógica MUX (Multiplexor) es un dispositivo fundamental en la lógica digital que se utiliza para seleccionar una de las múltiples entradas y enrutarla hacia la salida. La operación de un MUX se controla mediante las entradas de selección, que determinan cuál de las entradas de datos se transmite a la salida.
<h4>Código:</h4>

```ruby
/** 
 * Multiplexor:
 * if (sel == 0) out = a, else out = b
 */
CHIP Mux {
    IN a, b, sel;
    OUT out;

    PARTS:
    Not(in=sel, out=sal1);
    And(a=a, b=sal1, out=sal2);
    And(a=b, b=sel, out=sal3);
    Or(a=sal2, b=sal3, out=out);
}
```
<h4>Diagrama:</h4>

![Mux](https://github.com/Fernando2240/Grupo-Megahertz/assets/92164946/ae2a8f41-4da2-4cde-8579-4ed71bdc61c4)
<h1 align="center"> DMux </h1>
El demultiplexor (DMux) es otro componente esencial en la lógica digital que realiza la función inversa del multiplexor (Mux). Un demultiplexor toma una única entrada y la enruta a una de las múltiples salidas según el estado de un selector de control.
<h4>Código:</h4>

```ruby
 /**
 * Demultiplexor:
 * [a, b] = [in, 0] if sel == 0
 *          [0, in] if sel == 1
 **/

CHIP DMux {
    IN in, sel;
    OUT a, b;

    PARTS:
    Not(in=sel, out=sal1);
    And(a=sal1, b=in, out=a);
    And(a=sel, b=in, out=b);
}
```
<h4>Diagrama:</h4>

  ![DMux](https://github.com/Fernando2240/Grupo-Megahertz/assets/92164946/4329fc92-2798-44cd-bebc-6c8f5b83a046)
<h1 align="center"> Not16 </h1>

La compuerta lógica Not16 es una compuerta Not que opera en un bus de 16 bits. Esto significa que tiene 16 entradas y 16 salidas, y realiza la operación lógica Not (inversión) en cada bit de entrada individualmente. Cada bit de la salida es la negación del bit correspondiente en la entrada de 16 bits.
<h4>Código:</h4>

```ruby
/**
 * 16-bit Not gate:
 * for i = 0, ..., 15:
 * out[i] = Not(a[i])
 */
CHIP Not16 {
    IN in[16];
    OUT out[16];

    PARTS:
        Not(in=in[0], out=out[0]);
        Not(in=in[1], out=out[1]);
        Not(in=in[2], out=out[2]);
        Not(in=in[3], out=out[3]);
        Not(in=in[4], out=out[4]);
        Not(in=in[5], out=out[5]);
        Not(in=in[6], out=out[6]);
        Not(in=in[7], out=out[7]);
        Not(in=in[8], out=out[8]);
        Not(in=in[9], out=out[9]);
        Not(in=in[10], out=out[10]);
        Not(in=in[11], out=out[11]);
        Not(in=in[12], out=out[12]);
        Not(in=in[13], out=out[13]);
        Not(in=in[14], out=out[14]);
        Not(in=in[15], out=out[15]);
}
```
<h4>Diagrama:</h4>

  ![Not16](https://github.com/Fernando2240/Grupo-Megahertz/assets/92164946/78af8d4f-cd3f-4582-8907-133ebbbc08f7)
