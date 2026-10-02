+++
title="Resistividad"
description=""
summary=""
date="2026-10-01T22:48:00+02:00"
tags=["atomos", "corriente"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

La **resistividad**  indica la resistencia intrinseca de los materiales.

> La **resistividad** o **resistencia especifica** de un material es la
resistencia caracteristica que presenta un conductor de 1mm^2 de seccion y 1
metro de longitud a una temperatura de 20 ºC fabricado con este material.
>
> Se representa por la letra griega ``ρ`` (Rho)

La resistividad del cobre es 0,01786 Ω.

La expresion matematica para calcular la resistencia de un conductor es:

R= ρ\*L/S
ρ= (Ω*mm^2)/m (coeficiente de resistividad)
L= m (longitud del conductor)
S= mm^2 (seccion del conductor)
R= Ω (resistencia del conductor)


> Un cable de cobre de 15 metros de longitud y una seccion de 1mm tendra cual
> resistencia?
>
> R= 0,0178\*15/1 = 0,267Ω

> Cual es la resistencia de una varilla de hierro de 2mm de seccion y longitud
> de 4m?
>
> Le resistividad del hierro (ρ) es 0,13 (Ω\*mm^2/m)
> La longitud (L) es 4m
> La seccion (S) es 2mm^2
>
> R= 0,13\*(4/2) = 0,26Ω
>
> Con eso se puede observar que 15 metros de cable de cobre con 1mm de seccion
> tiene practicametne la misma resistencia que una varilla de hierro de 4
> metros con 2mm de seccion.

> Cual es la longitud de una bobina de cobre de 2mm de seccion si su
> resistencia total es de 3Ω?
> 
> La resistividad del cobre (ρ) es 0,0178 Ω\*mm^2/m
> La resistencia (R) es 3Ω
> La seccion (S) es 2mm^2
>
> R= ρ\*L/S
> R= (ρ\*L)/S
> R\*S= ρ\*L
> (R\*S)/ρ = L
> L= R\*(S/P)
>
> L= 3\*2/0,0178 = 337,08m

## Influencia de la temperatura en la resistividad

La resistencia de la mayoria de materiales varia con la temperatura. La
magnitud de esta variacion depende de la naturaleza propia del material y en
unos lo hace incrementando la resistencia al aumentar la temperatura y en otros
lo hace a la inversa, reduciendo la resistencia. Por norma general los metales
incrementan su resistencia con la temperatura.

La expresion para calcular el valor de resistencia de un conductor cuando se
modifica la temperatura de este es

Rₜº = R₀\*(1+ α\*Δtº)
Rₜº = Resistencia en caliente
R₀ = Resistencia a temperatura inicial
α = Coeficiente de temperatura
Δtº = Variacion de temperatura en ºC

El coeficiente de variacion de temperatura (α) es una propriedad intrinseca de
cada material que establece la relacion entre la variacion de la resistencia y
el cambio de temperatura.

Signos positivos del coeficiente te temperatura indican que ante un incremento
en la temperatura del material este experimenta un incremento de resistencia.
Un valor negativo del coeficiente de temperatura indica que, ante un incremento
de temperatura del material este experimenta una reduccion en el valor de su
resistencia electrica.

Los materiales aislantes por norma general tienen coeficiente de temperatura
negativo.

Si se le recude mucho la temperatura de un material conductor (hasta alcanzar
valores proximos a -273ºC, 0 Kelvin (K) o cero absoluto) se puede llegar a
alcanzar la superconductividad, la ausencia absoluta de resistencia electrica.

> Una bobina de cobre cuya resistencia a 0ºC es de 6,5Ω. Cual es su resistencia
> cuando alcance los 90ºC?
>
> La resistencia a temperatura inicial (R₀) es 6,5Ω
> La temperatura inicial es 0ºC y la final 90ºC, la variacion de temperatura
> (Δtº) es 90ºC
> El coeficiente de temperatura del cobre (α) es 0,0039
>
> Rₜº = R₀\*(1+α\*Δtº)
> Rₜº = 6,5\*(1+0,0039\*90º)
> Rₜº = 6,5\*(1+0,351)
> Rₜº = 6,5\*1,351
> Rₜº = 8,7815Ω
>
> Un incremento de 90ºC en la temperatura de la bobina provoca un incremento de
> resistencia de 2,2815Ω (8,7815Ω-6,5Ω).

> Que incremento de temperatura habra tenido que experimentar una bobina de
> cobre si a 15ºC tenia una resistencia de 3,5Ω si su resistencia a pasado a ser
> de 7,5Ω?
>
> La resistencia a temperatura inicial (R₀) es 3,5Ω
> La resistencia a temperatura final (Rₜº) es 7,5Ω
> El coeficiente de temperatura del cobre (α) es 0,0039
> 
> Si despejamos Δtº de la forumula inicial tenemos
> Δtº= ((Rₜº/R₀)-1)/α
> Δtº= ((7,5/3,5)-1)/0,0039
> Δtº= 293ºC
>
> La temperatura final de la bobina seria 308ºC (293 de incremento + 15
> iniciales)

