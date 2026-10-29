+++
title="El fusible"
description=""
summary=""
date="2026-10-29T19:30:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

Si en un punto concreto de una instalacion electrica se produce un
cortocircuito, la corriente pasara directamente desde el borne positivo al
negativo de la bateria sin que se produzca ninguna diferencia de potencial (pues
no hay elementos resistivos por medio), lo que provocara que circule una
intensidad de corriente tan elevada que terminara provocando un
sobrecalentamiento tan intenso en el cable, que acabara quemandose.

Para evitar estas situaciones se utilizan fusibles. Son elementos de proteccion
en circuitos electricos y electronicos del automovil constituidos por un hilo de
aleacion de plomo y estano calibrado para fundirse al ser atravesado por un
determinado valor de corriente.

Los fusibles se conectan en serie con el circuito electrico que protegen. Al
producirse un corto, la elevada intensidad de corriente que circula por el
provoca un fuerte incremento de la temperatura en el tramo del circuito
afectado, que ocasiona que el fusible se funda. De este modo deja de circular
corriente por el circuito y el sistema queda fuera de todo riesgo.

Hay fusibles abiertos, cerrados y de clavija en automocion, el mas comun es el
de clavija hoy en dia.

Los fusibles se agrupan en cajas de fusibles que pueden contener tambien otros
elementos de control tales como reles y que por norma general suelen estar
situados en el compartimento motor (cerca de la bateria) y en el habitaculo de
pasajeros (en la parte baja del salpicadero).

## Fusibles de clavija

Este tipo de fusibles se fabrican de plastico transparente para facilitar su
comprobacion visual, y sus diferentes colores nos indican la intensidad maxima
para la que estan calibrados, suelen tener grabada dicha intensidad en su canto
superior.

> Al sustituir un fusible fundido es muy importante hacerlo por otro del mismo
> valor, para evitar problemas en caso de sobreintensidades.

Esos fusibles disponen de dos puntos de control que permiten comprobar el estado
del fusible sin tener que extraerlo de su alojamiento en la caja de fusibles.
Los procedimientos para comprobar el estado de un fusible son los que se
describen:

### Procedimiento 1

- Cerramos el interruptor que alimenta el fusible a comprobar.
- Haciendo uso de un voltimetro comprobamos que exite tension en los dos puntos
de control. Si es asi, entonces esta en buen estado.

### Procedimiento 2

- Abrimos el interruptor que alimenta el fusible a comprobar.
- Haciendo uso de un ohmetro comprobamos la continuidad entre los dos puntos de
control. Si el ohmetro marca 0Ω entonces el fusible esta en buen estado.

> Dado que el numero de circuitos a proteger es elevado y el tamano de la caja
> de fusibles esta condicionado por multiples factores, en muchas ocasiones un
> mismo fusible protege a mas de un circuito. Cuando es asi y al mismo tiempo
> dejan de funcionar dos de los circuitos que comparten un mismo fusible, es
> probable que el fusible compartido este fundido.

## Como elegir el fusible mas apropiado para un circuito concreto

A partir de la formula de la potencia y sabiendo la tension a la que esta
sometido un circuito (en automoviles suele ser 12V) se puede establecer
facilmente cual es la intensidad de corriente que circula por el mismo, con lo
cual tendremos definido el parametro que nos proporciona el valor del fusible
a elegir.

P = V*I

Despejando la intensidad de corriente (I) de la formula anterior obtenemos la
formula que nos permite calcular la intensidad que recorre un circuito y a
partir de ella poder determinar el fusible mas adecuado a la instalacion sobre
la que estemos trabajando.

I = P/V

> Disponemos de un circuito que desarolla una potencia de 50 W con una tension
> aplicada de 12 V. Cual es el fusible que debemos montar en la instalacion?
>
> I = P/V = 50/12 = 4,167A
>
> Existen fusibles de `5A`, `7,5A`, `10A`, `15A`, `20A`, etc. y por norma
> elegimos el imediatamente superior para no quedarnos cortos, asi que se
> incorporaria el de 5A (naranja).
