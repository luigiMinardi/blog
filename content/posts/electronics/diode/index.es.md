+++
title="Diodo"
description=""
summary=""
date="2026-10-06T17:23:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

## Semiconductores

La conductividad/resistividad de los materiales depende de los electrones de
valencia y de la ocupacion de esta ultima capa. Un numero de electrones bajo,
inferior a la mitad de la capacidad del ultimo nivel orbital, determina que el
material sea conductor, por contra, el numero de lectrones elevado o proximo al
maximo eleva la resistencia electrica y la capacidad aislante.

Existen ciertas sustancias con un numero de electrones en su capa de valencia
"intermedio" denominadas semiconductores. Es el caso de materiales lates como
el silicio y el germanio, cuya estructura molecular en estado puro los
"convierte" en aislantes aunque la ocupacion de la capa de valencia no es
elevada.

El numero de electrones de valencia del silicio es de cuatro lo que hace que
al combinarse con otros atomos de silicio forme estructuras cristalinas muy
estables que no liberan electrones, comportandose por tanto como un material
aislante. Cada atomo comparte sus 4 electrones de valencia con los atomos
colindantes "recibiendo" 4 mas, que incrementan la estabilidad de su estructura
convirtiendolo en un elemento claramente aislante.

La estabilidad de esta estructura cristalina tiene un punto debil que es la
temperatura. Conforme esta aumenta la agitacion de los electrones tambien lo
hace, lo que provoca que algunos electrones perifericos salten de su orbita
regular rompiendo el enlace. A mayor temperatura hay mayor numero de enlaces
rotos y electrones libres. En estas circunstancias la conductividad del silicio
aumenta y disminuye su resistencia.

Este comportamiento resulta poco practico y de escasa utilidad en circuitos
electricos. La resistencia intrinseca del material implica que la corriente que
lo atraviesa genere gran cantidad de calor. Si no se disipa correctamente esta
energia termica, el recalentamiento del material reduce su resistencia,
permitiendo mayor intensidad de corriente, calor y recalentamiento,
produciendose una reaccion en cadena que conducira a la destruccion del
componente.

## Cristal tipo N

Si al silicio o al germanio los "dopamos" con materiales que tengan cinco
electrones en su capa de valencia, como puede ser el arsenico, el antimonio o el
fosforo, la estructura molecular de la sustancia resultante mantiene la
configuracion molecular original de la sustancia en mayor proporcion, dejando
cierto numero de electrones "libres". Estos electrones no se integran
suficientemente en la estructura de un atomo concreto, facilitando la
circulacion de corriente en cuanto el cristal sea sometido a una diferencia de
potencial electrico.

Cuando debido a la impureza anadida, se obtiene una estructura con un electron
libre se dice que se trata de un cristal tipo N.

## Cristal tipo P

Si al silicio o al germanio les anadimos en pequena proporcion materiales
metalicos con tres atomos de valencia, como pueden ser aluminio, boro, galio o
indio, la estructura molecular del cristal resultante adopta la forma del
elemento mayoritario dejando "huecos" libres. La existencia de estos huecos
facilita la conduccion de la corriente electrica, dando cabida a electrones que
no se integran suficientemente en la estructura atomica del material
semiconductor.

Cuando se obtiene una estructura cristalina con huecos (en realidad se trata de
falta de electrones para completar los enlaces de la estructura molecular) se
dice que se trata de un cristal tipo P.

## Union del semiconductor N con el P

Sabemos que un semiconductor tipo P dispone de "huecos" libres, aunque su carga
neta es neutra. Por contra, el semiconductor tipo N dispone de electrones
libres, pero su carga neta es neutra tambien.

Si procedemos a unir ambos cristales podremos ver que se producen
comportamientos electronicos peculiares que ofrecen varias posibilidades de
aplicacion.

Al unir fisicamente un cristal P y un cristal N los electrones libres del area
de contacto del semiconductor N tienden a expendirse por la estructura molecular
desplazandose hasta el semiconductor P. Se considera que los "huecos" del
cristal P realizan la misma accion desplazandose por tanto hacia el cristal N.

El desplazamiento a traves de la estructura motlecular de electrones de N hacia
P y el de los huecos desde P hacia N hace que en la zona de union entre ambos se
produzca la neutralizacion del material semiconductor. Cuando el electron libre
encuentra un hueco pasa a formar parte del enlace atomico integrandose en la
estructura cristalina. En estas circunstancias, la zona de union de los
cristales se convierte en una estructura equilibrada y estable que resulta
menos conductora que los cristales N y P originaes, por lo tanto aislante.

Como consecuencia de la reestructuracion molecular, el semiconductor N que
inicialmente era electricamente neutro, pierde electrones y pasa a ser positivo,
mientras que el del tipo P al perder "huecos", se va haciendo cada vez mas
negativo. Este fenomeno provoca que entre los semiconductores N y P (separados
por la zona neutra) aparezca una diferencia de potencial que se conoce como
"barrera de potencial" que en semiconductores a base de germanio es de unos 0,3V
y en el caso de cristales de silicio de 0,7V.

Podemos diferenciar en este momento tres naturalezas electricas diferentes en
una misma estructura cristalina. Esta particular configuracion cambia cuando
aplicamos una diferencia de potencial electrico en los extremos del
semiconductor.

Si conectamos los polos de una fuente de alimentacion, con el polo positivo de
la fuente al cristal N y el negativo al cristal P (lo que se conoce como
polarizacion inversa) la corriente no circulara pues se producira por atraccion
la acumulacion de huecos junto al terminal del cristal P y la concentracion de
electrones en el extremo del cristal N. Esta combinacion expande la zona neutra,
incrementando la resistencia electrica de la union de semiconductores.

En esta situacion el conjunto adquiere un comportamiento claramente resistivo o
aislante, aunque dependinedo de la diferencia de potencial aplicada se puede
establecer una pequena circulacion de corriente (lo que se conoce como corriente
de fuga) de valor tan pequeno, que resulta despreciable.

Sucede exactamente lo contrario si conectamos la fuente de alimentacion con su
borne positivo en el cristal P y el negativo en el cristal N. La tension
aplicada repele las cargas negativas y los huecos reduciendo la zona neutra a su
minima expresion cuando la diferencia de potencial electrico supera el valor de
barrera de potencial del diodo. La naturaleza de ambos cristales permite a
partir de ese momento la circulacion de la corriente sin ocasionar resistencia a
la intensidad de la misma. La tension de loa corriente conducida se reduce por
la diferencia de tension necesaria para contrarestar la tension de la barrera de
potencial.

Por tanto podemos deducir de la union de los semiconductores P y N lo sigiente:
- Que este tipo de uniones se puede comportar tanto como un buen conductor como
todo lo contrario, ofreciendo tal resistencia al paso de la corriente que se
puedenconsiderar materia no conductora o aislante.
- Que el comportamiento de la union depende de la polarizacion aplicada, es
decir del potencial electrico al que conectamos cada cristal.

A este tipo de union se le conoce con el nombre de diodo.

## El diodo

El diodo puede ser definido como una **valvula electrica unidireccional**, que
permite el paso de corriente en un sentido y lo impide en el sentido contrario.
Podemos compararlo con una valvula hidraulica antiretorno. En sentido de
izquierda a derecha el liquido circula a partir del momento en que la presion
vence la resistencia del muelle y separa la bola de su asiento. De derecha a
izquierda no se producira circulacion de fluido pues el cierre es hermetico, sea
cual sea la presion.

El simbolo con el que se representa el diodo es un triangulo apuntando a una
linea, la base del triangulo es el Anodo (+) la linea es el Catodo (-).

Las dos posibilidades de polarizacion de un diodo se conoce con los nombres de:
- Polarizacion directa: Cuando se conecta el potencial positivo al anodo
(cristal P) y el potencial negativo al catodo (cristal N). El resultado es la
conduccion de corriente cuando la diferencia de potencial electrico o voltaje
aplicado supera la tension de barrera necesaria para la ordenacion de las cargas
en la zona neutra o barrera (tension de barrera).
- Polarizacion inversa: Cuando se conecta el potencial positivo de alimentacion
al catodo (cristal N) y el potencial negativo al anodo (cristal P). El resultado
es el bloqueo del diodo.

El diodo y sus derivados son los elementos fundamentales para el desarollo de la
electronica. Entre sus aplicaciones en el sector del automovil, cabe destacar
por ser la mas entigua los diodos del alternador, utilizados para rectificar la
corriente alterna que este genera para hacerla continua.

> Popularmente, los diodos "convencionales" o que no ofrecen ninguna
> caracteristica funcional adicional a la conduccion de la corriente en un
> sentido y el bloqueo en el contrario reciben el nombre de diodos
> rectificadores.
>
> Esto es debido a que su utilizacion casi exclusiva en una primera epoca de la
> electrotecnia fue la rectificacion de corriente alterna para obtener corriente
> continua.

## Como comprobar un diodo rectificador

Los fallos mas comunes en los diodos son, los diodos abiertos y los diodos
cruzados. El primer caso provoca la interrupcion permanente del circuito (el
diodo abierto no conduce en polarizacion directa) y el segundo el cortocircuito
del mismo (el diodo cruzado no bloquea en polarizacion inversa). Cuando se
sospecha que un diodo puede estar danado debe procederse a su comprobacion.

Comprobar el correcto funcionamiento de un diodo es muy sencillo, basta con
verificar que permite el paso de corriente en un sentido y lo impide en el otro.
Para ello utilizaremos un multimetro en su funcion de ohmetro o preferiblemente
en funcion especifica de comprobacion de diodos.

## Verificacion mediante ohmetro

En primer lugar conectamos el diodo en sentido directo. Para ello colocamos el
cable rojo sobre el anodo del diodo (el lado del diodo sin marcar) y el cable
negro sobre el catodo (el lado que tiene la franja trazada). Previamente
habremos seleccionado la funcion ohmetro (Ω) en el multimetro.

En estas condiciones el tester suministra una pequena corriente continua para
medir la respuesta del diodo. Las lecturas de resistencia que nos puede
proporcionar el multimetro son dos:
- Si la resistencia que se lee es baja indica que el diodo no esta abierto y en
principio, a falta de comprobar la polarizacion inversa, parece funcionar
correctamente.
- Si esta resistencia es muy alta, nos indica que el diodo esta "abierto" y debe
ser reemplazado.

En segundo lugar polarizamos el diodo en inverso, para ello colocamos el cable
de color rojo en el catodo (el lado con la marca) y el cable negro en el anodo
del diodo.

El proposito de este caso es tambien tratar de hacer circular corriente a traves
del diodo, pero ahora en sentido opuesto al de conduccion. Las lecturas de
resistencia que nos puede proporcionar el multimetro son tambien dos:
- Si la resistencia leida es muy alta, esto nos indica que el diodo se comporta
como se esperaba, pues un diodo polarizado en inverso casi no conduce corriente
y resulta muy resistivo.
- Si la resistencia es muy baja nos indica que el diodo esta cortocircuitado y
debe ser reemplazado.

## Verificacion mediante comprobador de diodos

En primer lugar polarizamos el diodo en corriente directa, colocando el cable
rojo sobre el anodo del diodo (el lado sin franja distintiva) y el cable negro
sobre el catodo (el que tiene la franja). El multimetro debe de estar en
posicion de comprobador de diodos.

En estas condiciones el tester suministra una pequena corriente continua a
traves de la cual puede medir la respuesta del diodo. Las lecturas de tension
que nos puede proporcionar el multimetro son:
- Si la tension que indica el tester es de 0,6 a 0,7V (diodos de silicio) o 0,2
a 0,3V (diodos de germanio) indica que el diodo conduce y parece funcionar
correctamente. El valor de tension indicado corresponde a la tension de barrera.
- Si la tension que indica es infinita, nos inidica que el diodo esta "abierto"
y debe ser reemplazado.
- Si la tension que proporciona es 0V indica que el diodo esta cruzado y debe
ser sustituido.

En segundo lugar polarizamos el diodo en inverso, para ello colocamos el cable
de color rojo en el catodo y el negro en el anodo del diodo.

Se pretende hacer circular corriente a traves del diodo, pero ahora en sentido
opuesto o inverso. Las lecturas de tension que nos puede proporcionar el
multimetro son:
- Si la tenison proporcionada es infinita, esto nos indica que el diodo se
comporta como se esperaba, pues un diodo polarizado en inverso casi no conduce
corriente.
- Si el diodo esta cruzado el multimetro indicara 0V.


