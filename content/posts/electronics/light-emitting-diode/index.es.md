+++
title="Diodo LED"
description=""
summary=""
date="2026-10-06T20:37:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

El diodo LED (Light Emitter Diode o diodo emisor de luz) se caracteriza por
emitir luz cuando conduce la corriente electrica. En polarizacion inversa no
deja pasar la corriente ni emite luz. Es decir, se comporta (en cuanto a
cuestiones de polarizacion) como un diodo rectificador con la salvedad de que
emite luz.

La emision de luz se debe a un proceso fisico por el cual determinados
electrones tienen la particularidad de desprender fotones cuando ocupan un hueco
o retornan a su orbita de valencia, que logicamente solo se produce cuando
existe un flujo continuo de electrones que cambian de ubicacion, por lo tanto
una corriente electrica y polarizacion directa.

El simbolo con el que se representa este componente en los circuitos electricos
son dos flechas en diagonal y en paralelo una a otra donde apuntan para arriba a
la derecha, representando los rayos de luz saliendo del anodo, estan un poco
arriba de un triangulo que representa el anodo, ese que tiene una linea en una
de sus puntas representando el catodo.

Los LEDs tiene dos patillas de conexion, una larga y otra corta. La patilla
larga es el anodo y la corta el catodo, que al conectarse al positivo y negativo
respectivamente permiten el paso de la corriente electrica y la emision de luz.
El en encapsulado translucido la posicion del catodo se indica mediante un
biselado o rebaje plano que permite identificar la disposicion cuando el diodo
led se encuentra soldado al circuito y con sus patillas cortadas.

Dependiendo del material semiconductor empleado y la sustancia dopante, el diodo
LED emitira la luz de un color u otro. Si emite luz de color verde se trata de
un diodo tratado con imporezas de galio-fosforo. Si la luz emitida es de color
rojo las impurezas incorporadas al semiconductor habran sido a base de
galio-arsenico.

Actualmente existen diodos multicolores o RGB que son diodos que tienen 3
semiconductores, cada uno con un color diferente. Los colores de estos 3 diodos
son rojo, verde y azul. Controlando la mezcla de estos 3 colores primarios se
puede obtener una gama inmensa de colores utilizando estos LEDs. Para controlar
el color obtenido basta con hacer pasar mas o menos corriente por uno u otro
semiconductor. Por ejemplo si solo pasa corriente por el rojo y por el verde el
color que obtenemos sera el amarillo.

El consumo de estos diodos es muy bajo (tan solo unas pocas decenas de
miliamperios/hora) y su luz bastante intensa lo que los hace muy indicados para
multiples aplicaciones en automocion, tales como chivatos, testigos y luces de
control en general, asi como senalizacion e iluminacion.

Los LEDs tienen importantes ventajas respecto a las lamparas convencionales, una
de ellas es que consumen mucha menos energia. Como sabemos las bombillas
normales emiten luz pero tambien calor. En bombillas de filamento incandescente
tan solo se transforma un 20% de la energia electrica consumida en luz, de lo
cual se deduce que el 80% restante se transforma en calor. Para los LEDs estos
porcentajes se invierten, transformandose en luz el 80% de la energia consumida
y tan solo un 20% en calor. La reduccion del consumo electrico para obtener un
mismo rendimiento luminico y el ahoro energetico son evidentes.

Otra de las ventajas de los LEDs es que su vida util es mucho mayor que la de
una bombilla incandescente o un tubo de descarga de gas. Si una bombilla normal
tiene una vida util de unas 5000 horas, la vida util de un LED es superior a las
100000 horas de luz, o lo que es lo mismo mas de 11 anos de funcionamiento
ininterrumpido y una duracion 20 veces mayor.

Un diodo LED se comprueba exactamente igual que un diodo rectificador.

El 20% de energia que emiten en forma de calor conlleva la principal limitacion
de los diodos LEDs, que deben trabajar con tensiones de 2V para limitar la
intensidad de la corriente conducida y el recalentamiento. Si queremos
conectarlos a un valor de tension superior (por ejemplo 12V) debemos conectar
una resistencia en serie con diodo formando un divisor de tension. La caida de
tension provocada por la resistencia debe reducir el potencial aplicado al diodo
hasta los 2V.

> Supongamos que queremos montar un circuito y los datos que conocemos son los
> siguientes:
> Tension de la fuente de alimentacion (V): 14V
> Tension en bornes del diodo LED (Vʟᴇᴅ): 2V
> Intensidad del circuito (consumo del LED) (Iᴛ) 20mA
>
> Sabemos que en un circuito en serie la tension total (V) del circuito es
> igual a la suma de las caidas de tension que se producen a lo largo de este.
> En este caso la del LED debe ser 2V, por tanto:
> V = Vʟᴇᴅ + Vʀ
> Vʀ = V - Vʟᴇᴅ
> Vʀ = 14 - 2
> Vʀ = 12V
> Con este dato ya podemos aplicar directamente la ley de Ohm para obtener el
> valor de resistencia (R) a incorporar:
> R = Vʀ/Iᴛ
> R = 12/0,02
> R = 600Ω
