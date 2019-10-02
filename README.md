# proyecto_modulo1
proyecto de simulación matemática 
# Problemas de mezclas
$x_1$ = Cantidad de A usado en la mezcla 1

$x_2$ = Cantidad de B usado en la mezcla 1

$x_3$ = Cantidad de C usado en la mezcla 1

$x_4$ = Cantidad de A usado en la mezcla 2

$x_5$ = Cantidad de B usado en la mezcla 2

$x_6$ = Cantidad de C usado en la mezcla 2
**Función a optimizar Ganancia con el producto (Precio de venta - precio de producción):**

Precio de Venta:
$$ 1.1(x_1+x_2+x_3)+1.2(x_4+x_5+x_6)$$

Costo de produccion:
$$ .3(x_1+x_4)+.4(x_2+x_5)+.48(x_3+x_6)$$

**Requerimientos de produccion**

$$ x_1+x_2+x_3 >= 10000$$
$$ x_4+x_5+x_6 >= 10000$$
Se necesitará que se cambien a menor o igual que

**Restricciones de disponibilidad**

$$ x_1+x_4 <= 6000$$
$$ x_2+x_5<=10000$$
$$ x_3+x_6<=12000$$

**Restricciones de composicion**

$$x_1/(x_1+x_2+x_3) >= .3 $$
$$x_2/(x_1+x_2+x_3) <= .5 $$
$$x_3/(x_1+x_2+x_3) >= .3 $$

$$x_4/(x_4+x_5+x_6) <= .4 $$
$$x_5/(x_4+x_5+x_6) >= .35 $$
$$x_5/(x_4+x_5+x_6) <= .4 $$

**Estas restricciones se transforman a: 
 $$-.7x_1+.3x_2+.3x_3<=0$$
 $$ -.5x_1+.5x_2-.5x_3 <= 0$$
 $$ .3x_1+.3x_2-.7x_3<=0 $$
 
 $$ .6x_4-.4x_5-.4x_6<=0$$
 $$ .35x_4-.65x_5+.35x_6<=0$$
 $$ -.4x_4+.6x_5-.4x_6<=0$$
