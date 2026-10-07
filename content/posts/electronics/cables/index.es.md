+++
title="Cableado"
description=""
summary=""
date="2026-10-07T23:23:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

Los cables son hilos de cobre protegidos por un recubrimiento aislante de
diferentes colores para hacerlos mas facilmente identificables. Son los
encargados de realizar la union electrica entre los diferentes elementos del
circuito.

En el vehiculo, los cables se agrupan en mazos que se fijan a la carroceria a
traves de grapas y atraviesan paneles metalicos o puertas protegidos mediante
arandelas o fuelles de goma.

Al realizar instalaciones electricas sobre el vehiculo hemos de tener en cuenta
una serie de consideraciones.

El valor maximo de la corriente que puede transportar un cable depende de la
seccion y longitud de este. Si a la hora de montar una instalacion elegimos un
cable demasiado fino este tendra una resistencia alta provocando en el circuito
una caida de tension excesiva que restara eficacia al mismo, ademas de
sobrecalentarlo, con el consiguiente riesgo de incendio. Asimismo, un cable con
una longitud mayor de la estrictamente necesaria producira una caida de tension
que restara eficacia al circuito.

Para calcular la seccion de calbe que hemos de montar en una instalacion
electrica concreta lo haremos utilizando la siguiente formula:

Sᴍɪɴɪᴍᴀ = ρ(L/Rᴄᴀʙʟᴇ)
Sᴍɪɴɪᴍᴀ = Seccion minima del cable
ρ = Resistividad del cable
L = Longitud del cable
Rᴄᴀʙʟᴇ = Resistencia del cable

Las secciones de cables normalizados mas empleados en electricidad del automovil
son, segun Norma UNE: `0,5`, `0,75`, `1`, `1,5`, `2,5`, `4`, `6`, `10`, `16`,
`25`, `35` mm^2 de seccion. 

Si sustituimos el valor de la resistencia Rᴄᴀʙʟᴇ obtendremos una formula muy
util para el calculo de las secciones minimas en funcion de la intensidad de
corriente (I), la longitud del cable (L), la caida de tension maxima admisible
(ΔV) (que para estos casos es siempre del 2,5% que equivale a 0,3V) y el
coeficiente de resistividad (ρ).

Sᴍɪɴɪᴍᴀ = ρ\*(L/ΔV)\*I
ΔV = Caida de tension maxima admisible
I = Intensidad de corriente 

> Que seccion de cable deberemos comprar si queremos realizar la instalacion de
> unos faros antiniebla que consumen 18A, si sabemos que el total de cable a
> utilizar es de 3,5m?
>
> Sᴍɪɴɪᴍᴀ = ρ\*(L/ΔV)\*I
> Sᴍɪɴɪᴍᴀ = ρ\*L\*I/ΔV
> Sᴍɪɴɪᴍᴀ = 0,017\*3,5\*18/0,3
> Sᴍɪɴɪᴍᴀ = 3,57mm^2
> Por lo tanto debemos comprar cable cuya seccion sea de 4mm^2.
