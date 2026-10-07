+++
title="Transistor"
description=""
summary=""
date="2026-10-07T19:34:00+02:00"
tags=["atomos", "corriente", "to-review"]
categories=["todo", "electronica", "fundamentos de la electronica"]
+++

La combinacion en un mismo componente de tres cristales semiconductores recibe
el nombre de transistor.

A nivel fisico se puede considerar la union de dos diodos dispuestos en sentido
opuesto que "comparten" el material semiconductor que los une fisicamente aunque
electricamente los separa, puesto que en ambas uniones entre los semiconductores
de diferente naturaleza se forman las zonas de agotamiento electrico o barreras
de difusion caracteristicas de los diodos.

Esta condicion de materiales alternos en numero impar permite dos combinaciones
fisicas diferentes que de por si en ningun caso conduciran la corriente entre
sus extremos, puesto que la polarizacion en sentido directo de uno de los diodos
(conduccion) resulta siempre en polarizacion inversa del otro (bloqueo). Sin
embargo, la existencia de tres semiconductores permite la incorporacion de un
tercer terminal de conexion, cuya diferencia de potencial electrico con respecto
a los dos restantes determina el particular comportamiento electrico del
transistor.

Hay dos tipos de transistores existentes en funcion del tipo de union que
realicemos con los cristales semiconductores NPN y PNP y su representacion 
grafica es un circulo con un T dentro donde un emisor o colector entran al
circulo conectandose a la "ala" superior izquierda del T y un emisor o colector
sale de la "ala" superior derecha de la T, en el NPN tienes una flecha saliendo
del emisor por la derecha y en el PNP tienes una flecha entrando del emisor por
la izquierda.

La figura del transistor indica siempre mediante la flecha correspondiente a la
union PN la orientacion del diodo de control (Emisor-Base), que debe ser
polarizado en sentido directo para lograr la conduccion entre los extremos
(Emisor-Colector). La indicacion de esta union P-N permite reconocer si el
transistor es del tipo PNP o NPN, puesto que la punta de la flecha siempre
apunta al semiconductor N, que quedara dentro o fuera de la base representada
por el trazo plano en el centro del componente.

> La denominacion del emisor y el colector se debe precisamente a la funcion de
> "emision" de portadores de carga electrica (huecos o electrones) que realiza
> el primero que son utilizados o captados en su mayoria por el segundo, que
> realiza por tanto la funcion de colector.
>
> El numero de portadores de carga "recolectados" determina la cantidad de
> cargas electricas que circulan entre el emisor y el colector o lo que es lo
> mismo, la intensidad de la corriente.

A nivel funcional, la diferencia de tension entre el emisor y la base polariza
el transistor y determina la corriente de base, factores que regulan la
conductividad entre el emisor y el colector para una misma diferencia de tension
entre ambos. Esta particularidad permite gobernar corrientes emisor-colector de
valor elevado modulando la tension aplicada a la base del transistor, trabajando
con corrientes de control realmente reducidas.

Al igual que los diodos y las resistencias, el tamano y construccion de los
transistores debe ser acorde a la potencia electrica de trabajo, que en este
caso es variable. Para evitar la destruccion del material semiconductor y lograr
un comportamiento correcto muchos transistores se fabrican con disipadores
termicos integrados o con base metalica para su montaje sobre elementos de
refrigeracion.

En algunos transistores de alta potencia el soporte de montaje y disipacion
termica puede realizar tambien la funcion de terminal de conexion.

El funcionamiento de un transistor se asemeja al de un rele electromagnetico,
pues con una pequena corriente de excitacion controlamos un segundo circuito de
gran consumo (la corriente entre Emisor y Colector puede ser del orden de 50 a
200 veces superior a la de excitacion entre Emisor y Base). La ventaja de los
transistores respecto a los reles es que carecen de contactor que puedan
quemarse o deteriorarse, no tienen desgaste, puesto que no son mecanismos
mecanicos, y que ofrecen uan respuesta de regulacion proporcional.

La principal aplicacion de los transistores en automocion es la amplificacion de
senales y el control de la potencia electrica suministrada a los actuadores para
lograr un trabajo variable de los mismos, pudiendo trabajar en modulacion
(corriente continua variable) o saturacion (corriente continua intermitente).
Ambas explotan la ventaja electrica fundamental de los transistores, comonmente
conocida como ganancia de corriente, que se debe principalmente a loa diferente
capacidad para conducir las cargas electricas de los 3 semiconductores que los
forman.

> Ganancia de corriente o parametro β de un transistor
> La ganancia de corriente de un transistor es la relacion que existe entre la
> variacion o incremento de la corriente de Colector y la variacion de la
> corriente Base. Se trata de un parametro que indica el numero de veces que es
> incrementada la corriente principal E-C respecto a la de excitacion B-E. Su
> formula es la siguiente:
> β = ΔIᴄ/ΔIʙ
> β = Ganancia de corriente
> ΔIᴄ = Variacion de la corriente de coelctor
> ΔIʙ = Variacion de la corriente de base
> Si por ejemplo, tenemos un transistor con una variacion de corriente de 
> colector de 8mA y una variacion de la corriente de base de 0,08 mA, la
> ganancia sera:
> β = ΔIᴄ/ΔIʙ
> β = 8/0,08
> β = 100
> La ganancia de corriente de los transistores comerciales varia bastante de
> unos a otros. Podemos encontrar transistores de potencia que poseen una β de
> tan solo 20 hasta transistores amplificadores de senal que pueden llegar a
> tener una β de 400. Por todo ello, se pueden considerar que los valores
> normales de este parametro se encuentran entre 50 y 300.

## Funcionamiento del transistor

La particular respuesta de conduccion electrica variable y diferencial de los
transistores se debe a la combinacion de dos factores fisico-constructivos
principalmente:
- La disposicion de las uniones P-N es opuesta.
- El material semiconductor Emisor esta mas dopado que el del Colector y el del
Colector esta mas dopado que la Base. Asi, el Emisor puede conducir mas
corriente que el Colector y que la Base, que es la que menor capacidad de
conduccion tiene de los tres. Popularmente se dice que la base es "estrecha".

Teniendo en cuenta estas dos caracteristicas, para conseguir el paso de la
corriente entre el Emisor y el Colector o viceversa deben cumplirse dos
condiciones.

1. Debe existir una diferencia de potencial electrico suficiente entre ambos y
siempre mayor que entre el Emisor y la Base. Factor externo que puede ser fijo o
variable.
2. Tanto el Emisor como el Colector deben dejar de estar aislados electricamente
por las barreras de difusion que se forman en su union con la base. Como hemos
visto anteriormente, tras la union molecular entre dos semiconductores de
polaridad contraria se forma una zona de agotamiento electrico (neutra) que
resulta no conductora (barrera de difusion). Aunque se trata de un factor
obviamente interno puede ser modificado aplicando la tension adecuada a la base.

Para lograr la continuidad de la red de portadores de carga electrica en el
material semiconductor (electrones o huecos dependiendo de si se trata de un
cristal N o P), la union emisor-base debe ser alimentada en sentido directo
(polaridad igual a la del semiconductor) con una diferencia de tension
suficiente para "polarizar temporalmente" la barrera de difusion igual que en un
diodo. Para ello, el voltaje aplicado a la base del transistor debe ser positivo
o negativo con respecto al del emisor dependiendo de si se trata de un
transistor de tipo NPN o PNP con un valor diferencial superior a 0,3 a 0,7V en
funcion de si el material de base empleado es Germanio o Silicio.

Si esta condicion inicial se cumple, la union Emisor-Base se vuelve conductora,
permitiendo la circulacion de corriente en el sentido que la diferencia de
potencial entre ambos terminales produce. En este momento el Emisor, por su
mayor dopaje, emite mas portadores de carga que los que la Base, poco dopada y
estrecha "utiliza". Como es de esperar las cargas emitidas en "exceso" (huecos o
electrones) se pueden desplazar libremente por la estructura cristalina formada
por el Emisor y la Base, que ademas de materialmente continua resulta en este
momento electricamente conductora. Las cargas emitidas no pueden avanzar por la
zona de agotamiento existente entre la Base y el Colector, puesto que la
naturaleza electrica del colector es de su misma polaridad y las repele.

Aplicando a la union Base-Colector una tension de polaridad contraria a su
propia naturaleza, se drena el colector y se invierte su polaridad, la base
mantiene su naturaleza gracias a los portadores de carga emitidos por el Emisor
que no puede utilizar. Desaparece en el mismo instante la repulsion que matenia
el aislamiento electrico entre la Base y el Colector.

La base podria conducir corriente en este momento tanto con el Emisor como con
el Colector, puesto que ya no se encuentra aislada por las barreras de difusion
y existe diferencia de tension suficiente con ambos. Dos factores impiden la
corriente entre la Base y el Colector:
1. La diferencia de tension entre el Emisor y el Colector es siempre mayor que
la de la Base con cualquiera de los anteriores, favoreciendo el flujo de cargas
electricas entre el Emisor y el Colector por existir entre ellos la mayor
diferencia de potencial electrico.
2. Las diferencias de dopaje entre los semiconductores garantizan que los
portadores emitidos sean "recolectados" por el Colector y que la Base conduzca
de forma prioritaria con el Emisor.

De este modo la corriente entre el Emisor y el Colector es mayor que la
corriente entre la Base y el Emisor, definiendo la ganancia del transistor.

Teniendo en cuenta que la ganancia es un factor constructivo teoricamente
invariable, podemos decir que para una misma diferencia de tension entre el
colector y el emisor, la tension de la base modifica la conductividad de la
union Emisor-Base y por consiguiente regula la intensidad de la corriente
Emisor-Colector.

Basandonos en lo anterior, podemos deducir las reglas de polarizacion de los
transistores, que son necesariamente diferentes en funcion de su naturaleza
electrica.

En los transistores NPN el Emisor debe ser negativo con respecto a la Base
(polarizacion directa) y la Base negativa con respecto al Colector. El mas
positivo de los tres es siempre el Colector y el Emisor emite electrones que
"invaden" la estructura de la Base.

Para transistores PNP el Emisor debe ser positivo con respecto a la Base
(polarizacion directa) y la Base positiva con respecto al Colector. El mas
positivo en este caso es el Emisor y emite huecos que avanzan en direccion
contraria a los electrones por la estructura molecular de la Base.

Para facilitar la comprension del funcionamento del transistor, demonstraremos
el comportamiento de un transistor NPN intercalando amperimetros en diferentes
puntos de un circuito de polarizacion.

La conexion de la alimentacion resulta contraria a la orientacion de la union
Emisor-Base. La tension positiva sobre el cristal N del Emisor atrea las cargas
negativas del mismo bloqueando el diodo de polarizacion, mientras la negativa
sobre el Colector, aunque repele las cargas del cristal N no tiene posibilidad
de continuidad por la presencia de la barrera base-colector. Resulta imposible
cualquier corriente efectiva entre el emisor y el colector.

El Emisor recibe la tension negativa y el Colector la positiva. No existe
circulacion de corriente entre ellos, puesto que no se ha polarizado la union
emisor-base. La base no recibe tension y se encuentra electricamente aislada,
con lo cual no recibe electrones que puedan rellenar sus huecos ni tension que
provoque el desplazamiento de los mismos. Se mantiene en estado inerte,
impidiendo la conduccion entre emisor y colector.

Con el emisor conectado a tension negativa, para lograr la polarizacion efectiva
de la union emisor-base aplicamos tension positiva a la base. La repulsion
electrica de las cargas y los huecos polariza la barrera de difusion permitiendo
la circulacion de una pequena corriente entre la Base y el Emisor (sentido
convencional). No obstante la Base y el Colector se encuentrar sometidos a la
misma tension positiva. La tension positiva sobre el Colector atrae y concentra
las cargas negativas del semiconductor N sobre su terminal ensanchando la
barrera de difusion entre P y N. La corriente entre el Emisor y el Coelctor es
por tanto nula.

Para provocar una diferencia de tension suficiente entra la Base y el Colector
intercalamos una resistencia en la linea de alimentacion de la Base. Siendo la
intensidad de esta linea diferente de 0, la caida de tension provocada por la
resistencia reduce la tension positiva aplicada a la Base. La Base resulta en
este momento mas negativa que el Colector, que recibe uan tension positiva
mayor. La alimentacion positiva mayor absorbe las cargas negativas del
semiconductor N permitiendo el avance de los huecos hasta la barrera de difusion
entre la Base y el Colector. Las cargas negativas emitidas por el Emisor pueden
ahora desplazarse por el semiconductor P de la Base y continuar hasta el
potencial positivo mayor, que en este caso es el del Colector. La corriente
fluye en este momento entre el Colector y el Emisor (sentido convencional) con
mayor intensidad que entre el Emisor y la Base por el mayor dopaje del Colector
y por la diferencia de tension mayor entre los mismos que entre cada uno de
ellos y la Base.

> **Importante**  
> Superados los valores estrictamentes necesarios para la polarizacion de la
> barrera de difusion, las diferencia de tension Emisor-Base-Colector
> determinan el funcionamiento del transistor, que puede ser en modulacion o en
> saturacion.
> 
> En modulacion la corriente Emisor-Colector mantiene la proporcion de ganancia
> con la corriente de Emisor-Colector. La diferencia de tension Emisor-Base
> modifica parcialmente la estructura del semiconductor Base. La parte
> modificada permite la conduccion entre el Emisor y el Colector.
> 
> La saturacion se produce cuando la relacion de ganancia no se cumple y la
> corriente Emisor-Colector depende directamente de la diferencia de tension
> entre los mismos (del circuito al que se encuentran conectados). Ocurre al
> incrementar la diferencia de tension entre el Emisor y la base cuando se
> supera cierta intensidad entre ambos (corriente de saturacion). Las cargas
> emitidas saturan la estructura molecular del semiconductor Base modificandola
> por completo. En este momento podemos considerar la Base "temporalmente" de la
> misma polaridad que el Emisor y el Colector.
> 
> En estas condiciones, el transistor se comporta como una estructura continua
> de naturaleza N o P (dependiendo del emisor) aunque mantiene su distribucion
> desigual de "portadores" de carga. La corriente de Base y la de Colector
> fluyen por el material dopado de forma no relacionada en este momento, como lo
> harian por un conductor de resistencia cero, y no guardan relacion alguna de
> proporcion o ganancia.

## Transistor Darlington

El transistor Darlignton consiste en un circuito formado por dos transistores y
alguna resistencia para el ajuste y proteccion del sistema. Tal y como puede
apreciarse en la figura siguiente, los curcuitos Emisor-Colector se conectan en
paralelo y los circuitos Emisor-Base en serie. Este tipo de montaje presenta una
arquitectura que equivale a la de un "nuevo" transistor con sus correspondientes
terminales Emisor, Base y Colector.

El transistor principal (T₁) necesita una corriente de excitacion Emisor-Base
(Iʙ₁) para que circule una corriente Emisor-Colector (Iᴄ₁). En circunstancias
normales la corriente de base (Iʙ₁) del transistor T1 acabaria perdiendose,
pero, en este tipo de montaje dicha corriente acaba siendo parte de la corriente
principal del transistor T2.

Analizando el circuito comprobamos que la corriente de base del transistor T1 es
amplificada por el transistor T2, de lo que resulta una ganancia de corriente
muy superior a la de un transistor normal, con la ventaja de que aprovecha mucho
mas la potencia y se asegura un menor calentamiento.

<!-- TODO: INSTERT IMAGE Asi es la arquitectura de un transistor Darlington
mediante combinacion de dos transistores PNP. -->

<!-- TODO: INSTERT IMAGE Asi es un transistor Darlington constituido por
transistores NPN -->

Para hacernos una clara idea del potencial que tiene este tipo de montaje,
supongamos que los dos transistores de un Darlington tienen una ganancia, cada
uno de ellos, de 150. El resultado es que al realizarse el montaje contamos con
una ganancia de 150\*150=22500. Con una corriente infinitamente pequena podemos
controlar otra relativamente grande.

En automocion, este tipo de montaje se suele utilizar como etapa final de
potencia en numerosas aplicaciones electronicas. Una de estas aplicaciones es
sobre los encendidos electronicos, donde con las pequenas corrientes
proporcionadas por generadores tipo inductivo o Hall, cotrolamos el circuito
primario de la bobina. O con la tension de informacion proporcionada por una NTC
podemos controlar el funcionamiento de los electroventiladores.

Este tipo de transistor tambien se aplica en los reguladores de tension de los
alternadores y permite al paso de corrientes muy intensas.

## Comprobaciones sobre el transistor

Para realizar las comprobaciones necesarias sobre un transistor, la primera cosa
que debemos hacer es identificar cada uno de sus terminales. Cual de ellos es la
Base, cual es el Emisor y cual el Colector. Por norma general el colector, por
su mayor superficie fisica conecta tambien con la carcasa metalica de montaje,
para garantizar una transmision de calor proporcional a la corriente que circula
por el transistor.

Si el transistor cuenta unicamente con 2 patillas, entonces el Colector es la
propia carcasa de este. Por contra, si cuenta con 3 patillas, entonces
procederemos a medir la continuidad entre cada una de ellas y el cuerpo metalico
del transistor. Aquella patilla que proporcione un valor de resistencia minimo
sera el terminal Colector. En la siguiente imagen se simula el proceso que
acabamos de describir y como puede observarse, el terminal Colector es el
central pues de las 3 pruebas es la B la que proporciona valor de resistencia
muy pequeno. Tanto la pureba A como la C dan valor de resistencia infinito.

En el caso de transistores en los que la carcasa no este accesible, el sistema
de identificacion de terminales debera ser otro, en cuyo caso deberemos
identificar tambien el tipo de transistor.

Mediante un sencillo metodo podemos determinar si un transistor es del tipo PNP
o NPN. Este metodo consiste en tomar varias medidas, con el multimetro en modo
ohmetro y seleccionando el rango de 100.

En primer lugar, determinaremos cual de los terminales del transistor
corresponde a la Base. Esto se consigue midiendo la resistencia en el ohmetro
entre los diferentes terminales. En un transistor en buen estado, la resistencia
entre el Colector y el Emisor es siempre muy alta, cualquiera que sea la
polaridad aplicada por el ohmetro, el otro terminal correspondera a la Base. Una
vez localizada la Base, conectamos la punta de prueba positiva en la misma y la
negativa en cualquiera de los otros dos terminales del transistor. Si la
resistencia obtenida es muy baja (se ha polarizado la union de uno de los diodos
por el efecto de tension positiva aplicada con el ohmetro a la base P) se trata
de un transistor NPN; si obtenemos una resistencia muy alta (no se ha polarizado
la union) se trata de un transistor PNP.

Hay distintas lecturas de resistencia que debemos obtener para un transistor
de tipo PNP que se encuentre en buen estado y otras para el NPN.

