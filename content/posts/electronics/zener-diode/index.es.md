+++
title="Diodo Zener"
description=""
summary=""
date="2026-10-06T18:17:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

Sabemos que un diodo rectificador permite la circulacion de corriente en
polarizacion inversa, no permite el paso de la corriente independientemente del
valor de tension aplicado (en realidad permite un paso de corriente minima
despreciable que se conoce como corriente de fuga).

Existen diodos que en polarizacion inversa permiten la circulacion de corriente
a partir de un determinado valor de tension diferencial. Este tipo de diodos se
conoce como diodos Zener. La tension a partir de la cual el diodo Zener se
dispara y permite la circulacion de corriente en sentido inverso se conoce como
"tension de ruptura" o "tension Zener".

El simbolo grafico de un diodo Zener es un triangulo apuntando a una linea con
extremidades donde se parece una S, el anodo es la base del triangulo y el
catodo la S.

## Curva caracteristica de un diodo semiconductor

En un diodo en la que se distingue claramente las polarizaciones directa (Vꜰ) e
inversa (Vʀ). Se puede observar una region de polarizacion directa, una region
de polarizacion inversa y una Region de ruptura en su curva grafica. A esta
curva se denomina una curva caracteristica I-V del diodo.

En la zona de polarizacion directa (parte superior del grafico con la intensidad
indicada en mA), la conduccion de corriente es nula hasta que se alcanza la
tension de transicion (Vᴛ) necesaria para contrarrestar la barrera de potencial
(zona neutra de la union N-P). La conduccion comienza discretamente al
aproximarse al valor de tension Vᴛ (entre 0,3 y 0,7V dependiendo del
semiconductor), valor a partir del cual la intensidad aumenta rapidamente. La
diferencia de tension entre los extremos del diodo permanece, muy proxima a Vᴛ
para cualquier valor de la intensidad.

respecto a la zona de polarizacion inversa (parte inferior de la grafica con la
intensidad indicada en μA), sabemos que en condiciones normales la intensidad
que circula es minima (corriente de fuga).

Cuando la tension diferencial inversa aplicada al diodo alcanza el valor Vᴢ,
conocido como tension de Zener o de ruptura, se produce un incremento brusco de
la intensidad de corriente (pasando de corriente de fuga a corriente Zener). En
estado de conduccion inversa la diferencia de tension entre los extremos del
diodo Zener se mantiene en valor Vᴢ constante. Este comportamiento
caracteristico constituye la mayor utilidad de estos diodos, que se utilizan
como reguladores o limitadores de tension principalmente.

## Aplicaciones del diodo Zener en el automovil

El comportamiento caracteristico de este tipo de diodos permite utilizarlos
como:
- Regulador o estabilizador de tension: Supongamos puntos 1 y 2 que corresponden
a los ramales de alimentacion positiva y negativa respectivamente de un circuito
electronico alimentado por una tension variable de valor ligeramente superior a
la que necesitamos estabilizar para el correcto funcionamiento de varios
elementos consumidores.
Para estabilizar la tension del circuito y mantener el valor de alimentacion
deseado instalamos entre las lineas positiva y negativa del mismo un diodo Zener
conectado en polarizacion inversa. Cuando la diferencia de tension entre las
lineas de alimentacion supera la tension zener (Vᴢ) el diodo permite el paso de
la corriente manteniendo entre sus extremos la diferencia de tension Vᴢ. La
conexion del anodo del diodo al valor constante del negativo mantiene el catodo
y con el toda la linea positiva en valor Vᴢ impidiendo que la tension
suministrada a los componentes del circuito pueda danarlos. En estado de
conduccion la resistencia en serie con el diodo Zener (resistencia de drenaje)
limita la intensidad de la corriente para impedir la destruccion del diodo Zener
por exceso de temperatura.
El simil hidraulico para esta funcion de los diodos Zener serian los reguladores
de presion de combustible de los sistemas de inyeccion, que mantienen la presion
en la rampa en un valor constante independiente del caudal suministrado por la
electrobomba derivando al retorno el combustible excedente.
- Proteccion de consumidores: Supongamos que queremos proteger a un consumidor C
de las subidas de tension intermintentes que provoca el funcionamiento
intermitente de un componente electromagnetico que produce fuertes picos de
tension.
Colocando un diodo Zener en paralelo y polarizacion inversa protegemos al
consumidor C permitiendo la descarga de la tension excesiva por el circuito
paralelo. En el momento en que la diferencia de tension que recibe C supera la
tension Zener del diodo el mismo trabaja como puente limitando el valor maximo
de la tension aplicada. La resistencia de drenaje R limita la intensidad de la
corriente derivada para evitar el calentamiento del diodo.
En automocion existe un simil neumatico de funcionamiento similar. Las valvulas
Blow-Off utilizadas en los vehiculos turbo descargan los picos de presion que se
producen en el sistema de admision para proteger la integridad de los
turbocompresores.
