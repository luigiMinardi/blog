+++
title="Resistencias variables"
description=""
summary=""
date="2026-10-05T21:44:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

Son resistencias variables de tipo mecanico que modifican su valor ohmico
mediante un cursor que puede despazarse (segun casos) por un bobinado o sobre
una pista ceramica. Si disponen de dos terminales de conexion se trata de
reostatos, mientras que si disponen de tres se trata de potenciometros. Los
potenciometros pueden ser utilizados como reostatos utilizando unicamente dos de
sus bornes.

## Potenciometros de pelicula de carbon
Sobre un disco de fibra se deposita una pelicula resistiva de carbon sobre la
cual se desliza haciendo contacto el cursor movil. Son empleados en circuitos
donde las intensidades de corriente son pequenas para obtener una tension de
salida variable conectados como potenciometro, o una itensidad variable
conectados como reostato.

## Potenciometros bobinados

Se caracterizan por estar formados por un hilo o alambre de alta resistencia
bobinado alrededor de un soporte ceramico sobre el que desliza un cursor movil
unido a un eje rotativo. Se emplean para circuitos en los que las intensidades
de corriente de trabajo son elevadas para regular la potencia electrica
suministrada a determinados elementos.

Segun la posicion en la que se encuentren pueden provocar mayor o menor caida
de tension y de esa forma modificar las respuestas del circuito regulando la
intensidad de corriente que circulara por el.

Hay simbolos en esquemas electricos para Resistencias variables, reostatos y
potenciometros.

Los reostatos y potenciometros tienen multiples aplicaciones en automocion, por
ejemplo para controlar el volumen de la radio, modular la luminosidad del cuadro
de instrumentos, como sensores de desplazamiento para controlar la apertura de
la mariposa de admision o determinar la posicion del pedal del acelerador, etc.

A nivel teorico cualquier potenciometro se puede considerar la conexion en serie
de varias resistencias del mismo valor. Si calculamos la caida de tension que
provoca cada una de ellas y se la restamos a su valor de alimentacion
obtendremos los valores de tension intermedios del circuito. Para ello primero
debemos conocer la intensidad del circuito en funcion de la resistencia total.

El contacto electrico del cursor movil sobre los puntos de union entrega el
valor de tension especifico acorde a la posicion del mismo, obteniendo una
variacion de tension escalonada entre los valores maximos y minimo. La
multiplicacion del numero de resistencias o en su defecto la utilizacion de una
resistencia continua reduce los escalones o saltos de tension hasta proporcionar
una tension lineal de valor proporcional a una posicion precisa y concreta.

En los ejemplos siguientes supongas que se trata te un potenciometro de 2000Ω
(entre los extremos A y C, su resistencia es de 2KΩ) al que aplicamos una
tension de 10V.

> Posicion 1, cerca del A
> Tension entre A y C = 10V
> Resistencia entre A y C = 2000Ω
> Tension entre A y B = 2,5V
> Resistencia entre A y B = 500Ω
> Tension entre B y C = 7,5V
> Resistencia entre B y C = 1500Ω

> Posicion 2, en el medio
> Tension entre A y C = 10V
> Resistencia entre A y C = 2000Ω
> Tension entre A y B = 5V
> Resistencia entre A y B = 1000Ω
> Tension entre B y C = 5V
> Resistencia entre B y C = 1000Ω

> Posicion 3, cerca del C
> Tension entre A y C = 10V
> Resistencia entre A y C = 2000Ω
> Tension entre A y B = 7,5V
> Resistencia entre A y B = 1500Ω
> Tension entre B y C = 2,5V
> Resistencia entre B y C = 500Ω
