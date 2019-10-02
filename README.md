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


 import numpy as np
from scipy.optimize import linprog
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
sns.set()

venta=np.array([1.1,1.1,1.1,1.2,1.2,1.2])
costo=np.array([.3,.4,.48,.3,.4,.48])
ganancia=-(venta-costo) # Se pone signo menos porque se quiere maximizar

A=[[-1,-1,-1,0,0,0], # Requerimientos de producción, signo negativo porque la condición debe ser <=
  [0,0,0,-1,-1,-1], # Requerimientos de producción, signo negativo porque la condición debe ser <=
  [1,0,0,1,0,0], # Restricciones de disponibilidad
  [0,1,0,0,1,0], # Restricciones de disponibilidad
  [0,0,1,0,0,1], # Restricciones de disponibilidad
  [-.7,.3,.3,0,0,0], #Restricciones de composición mezcla 1
  [-.5,.5,-.5,0,0,0], #Restricciones de composición mezcla 1
  [.3,.3,-.7,0,0,0], #Restricciones de composición mezcla 1
  [0,0,0,.6,-.4,-.4], #Restricciones de composición mezcla 2
  [0,0,0,.35,-.65,.35],#Restricciones de composición mezcla 2
  [0,0,0,-.4,-.4,.6]] #Restricciones de composición mezcla 2

b=[-10000,-10000,6000,10000,12000,0,0,0,0,0,0] #vector de restricciones

nombres=["A en mezcla 1","B en mezcla 1","C en mezcla 1","A en mezcla 2","B en mezcla 2","C en mezcla 2","Utilidad"]

res = linprog(c=ganancia,A_ub=A,b_ub=b,method="interior-point")
print(res)



