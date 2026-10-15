+++
title="Encendido y sensores del motor — Apuntes de estudio"
description=""
showDate = false
showAuthor = false
showEdit = false
showReadingTime = false
showWordCount = false
sharingLinks = false
showComments = false
[build]
    list="never"
+++

## 1. Circuito de encendido
El encendido convierte los 12 V de la batería en 15–40 kV para que salte la chispa en la bujía justo antes del PMS, con el avance adecuado a rpm y carga. Valores típicos aproximados: comprueba siempre los datos del fabricante.  

**Principio de la bobina.** La corriente por el primario crea un campo magnético. Al cortarla, el campo colapsa e induce alta tensión en el secundario.  
| Devanado | Espiras | Hilo | Resistencia típica |
| --------------- | --------------- | --------------- | --------------- |
| Primario | 100–300 | Grueso | 0,5–4 Ω |
| Secundario | 15.000–30.000 | Fino | 5–15 kΩ |

### 1.1 Encendido convencional (platinos / ruptor)
Circuito primario (baja tensión):  
1. Batería (+)
2. Llave de contacto
3. Resistencia previa (si la lleva) y primario de la bobina (borne 15 → borne 1)
4. Platinos (ruptor) → masa
5. Condensador en paralelo con los platinos

Circuito secundario (alta tensión):  
1. Secundario de la bobina (borne 4)
2. Cable central → rotor (dedo) del distribuidor
3. Tapa del distribuidor → cables de bujía
4. Bujía → masa (salta la chispa)  

Elementos clave:

• **Leva:** abre los platinos; tiene tantos lóbulos como cilindros.  
• **Condensador:** evita el arco en los platinos y acelera el corte, así la chispa es más fuerte.  
• **Ángulo de cierre (Dwell):** grados de leva con platinos cerrados; en 4 cilindros, unos 50–55° (≈ 60 %).  
• **Avance centrífugo:** contrapesos que adelantan la chispa al subir las rpm.  
• **Avance por vacío:** cápsula de depresión conectada al colector que adelanta la chispa a carga parcial.  

Inconvenientes: desgaste de platinos y leva, reglajes periódicos, corriente primaria limitada (3–4 A) y chispa débil a altas rpm porque la bobina no tiene tiempo de cargarse.
### 1.2 Encendido electrónico
Un transistor (módulo o ECU) corta la corriente del primario en lugar de los platinos. Evolución:  
| Tipo | Quién da la señal | Avance | Reparto de la chispa |
| --------------- | --------------- | --------------- | --------------- |
| Transistorizado con contactos | Platinos (solo señal, poca corriente) | Mecánico | Distribuidor |
| Sin contactos (inductivo o Hall) | Generador de impulsos en el distribuidor | Mecánico | Distribuidor |
| Integral / cartografiado | Sensor de cigüeñal (CKP) | Mapa en ECU | Distribuidor |
| DIS (chispa perdida) | CKP | Mapa en ECU | Bobina doble, sin distribuidor |
| COP (bobina por bujía) | CKP + árbol de levas (CMP) | Mapa en ECU | Una bobina sobre cada bujía |

• **Generador inductivo:** imán + bobina + rueda reluctora; señal alterna, 2 cables.  
• **Generador Hall:** 3 cables (alimentación, masa, señal); señal cuadrada.  
• **DIS:** cada bobina dispara dos cilindros gemelos (1-4 y 2-3); uno está en compresión y el otro en escape (chispa perdida).  
• **Dwell electrónico:** la ECU regula el tiempo de carga para tener corriente constante (6–8 A) a cualquier rpm.  

Ventajas frente al convencional: sin desgaste ni reglajes, chispa más energética, avance exacto (rpm, carga, temperatura y picado) y menos emisiones.
## 2. Sensores: ideas generales
La ECU recibe señales de los sensores, calcula inyección y avance, y manda a los actuadores. Casi todos los sensores trabajan con 5 V de referencia y una masa propia de sensor que da la ECU.  

| Tipo de sensor | Cómo funciona | Cables típicos | Ejemplos |
| --------------- | --------------- | --------------- | --------------- |
| Resistivo NTC | La resistencia baja al subir la temperatura | 2 | Temperatura de agua y de aire |
| Potenciómetro | Divisor de tensión 0–5 V según posición | 3 | Mariposa, pedal, EGR |
| Inductivo | Genera tensión alterna propia, sin alimentación | 2 (+ malla) | Cigüeñal (CKP) |
| Hall | Señal cuadrada digital | 3 | Cigüeñal, árbol de levas, pedal |
| Piezoeléctrico | Genera tensión al deformarse o vibrar | 1–2 (+ malla) | Picado |
| Piezorresistivo | Membrana que cambia de resistencia con la presión | 3 | MAP |
| Galvánico | Genera tensión por diferencia de oxígeno | 1–6 | Lambda |


Para diagnosticar: multímetro (alimentación, masa, resistencia), osciloscopio (forma de la señal) y máquina de diagnosis (valores reales y códigos de avería). Si un sensor falla, la ECU suele usar un valor sustituto y entra en modo emergencia.  
## 3. Sensores uno a uno
### 3.1 RPM y posición (CKP y CMP)
• **Qué mide:** el CKP (cigüeñal) da régimen y posición del PMS; el CMP (árbol de levas) da la fase, es decir, qué cilindro está en compresión.  
• **Principio:** rueda fónica, normalmente 60-2 dientes; el hueco de dos dientes marca la referencia del PMS.  
• **Inductivo:** 2 cables + malla, señal alterna cuya amplitud y frecuencia suben con las rpm. Resistencia típica 200–1.000 Ω.  
• **Hall:** 3 cables, señal cuadrada de amplitud fija (0–5 V o 0–12 V), funciona incluso a muy bajas rpm.  
• **Uso en la ECU:** momento de chispa e inyección, cuentarrevoluciones. El CMP permite inyección secuencial y encendido COP.  
• **Fallo:** CKP averiado = el motor no arranca o se cala. CMP averiado = arranque largo y modo emergencia.  
### 3.2 MAF (caudalímetro de masa de aire)
• **Qué mide:** la masa de aire que entra al motor (kg/h).  
• **Principio:** hilo o película caliente. La electrónica mantiene el elemento a una temperatura fija sobre la del aire; cuanto más aire pasa, más corriente necesita, y esa corriente es la medida.  
• **Señal:** analógica 0–5 V (≈ 1 V al ralentí, hasta ≈ 4,5 V a plena carga) o en frecuencia en los modernos. Suele integrar el sensor de temperatura de aire.  
• **Uso en la ECU:** calcular la carga del motor y la cantidad de combustible. En diésel, también controlar la EGR.  
• **Fallo:** falta de potencia, tirones, ralentí inestable, humo negro en diésel. Precursor: caudalímetro de aleta (volumétrico, con potenciómetro).  
### 3.3 MAP (presión absoluta del colector)
• **Qué mide:** la presión absoluta en el colector de admisión, que indica la carga del motor.  
• **Principio:** piezorresistivo; membrana de silicio en puente de Wheatstone. 3 cables: 5 V, masa y señal.  
• **Señal:** sube con la presión. Al ralentí (≈ 0,3–0,4 bar abs.) ≈ 1 V; con contacto y motor parado mide la presión atmosférica (≈ 1 bar). En turbo llega a 2–2,5 bar.  
• **Uso en la ECU:** sistemas "speed-density": la masa de aire se calcula con MAP + rpm + temperatura de aire. En turbo, controla la presión de soplado.  
• **Fallo:** consumo alto, ralentí irregular, falta de potencia. Revisar primero el tubo de depresión.  
### 3.4 Picado (sensor de detonación)
• **Qué mide:** las vibraciones del bloque que produce la detonación (picado), típicamente entre 5 y 15 kHz.  
• **Principio:** piezoeléctrico atornillado al bloque; genera tensión al vibrar. 2 cables + malla.  
• **Montaje:** el par de apriete es crítico (≈ 20 N·m); sin arandelas ni pasta que amortigüe.  
• **Uso en la ECU:** si detecta picado en un cilindro, retrasa el avance de ese cilindro y luego lo vuelve a adelantar poco a poco.  
• **Fallo:** la ECU retrasa el avance por seguridad = pérdida de potencia y más consumo.  
### 3.5 Carga: mariposa (TPS) y pedal de acelerador (APP)
• **TPS:** potenciómetro en el eje de la mariposa, 3 cables. ≈ 0,5 V cerrada y ≈ 4,5 V abierta. Los antiguos solo tenían interruptores de ralentí y plena carga.  
• **Pedal (APP):** en acelerador electrónico (sin cable), el pedal lleva 2 pistas redundantes, potenciométricas o Hall. Una pista suele dar la mitad de tensión que la otra, o la inversa.  
• **Plausibilidad:** la ECU compara las dos pistas del pedal y las de la mariposa motorizada; si no cuadran, entra en emergencia.  
• **Uso en la ECU:** deseo del conductor, aceleración/deceleración, corte en retención, ralentí.  
• **Fallo:** tirones, zonas muertas al pisar, modo emergencia (≈ 1.200 rpm fijas o sin respuesta al pedal). Comprobar con barrido lento en osciloscopio.  
### 3.6 Temperatura de aire (IAT)
• **Qué mide:** la temperatura del aire de admisión, para saber su densidad.  
• **Principio:** NTC, 2 cables. Aproximado: ≈ 2,5 kΩ a 20 °C y ≈ 300 Ω a 80 °C.  
• **Uso en la ECU:** corregir inyección y avance (aire frío = más denso = más combustible).  
• **Fallo:** mezcla algo incorrecta. Una lectura de −40 °C indica circuito abierto; una muy alta, cortocircuito a masa.  
### 3.7 Temperatura de agua (ECT)
• **Qué mide:** la temperatura del refrigerante, que indica la temperatura del motor.  
• **Principio:** NTC, igual que el de aire. Aproximado: ≈ 2,5 kΩ a 20 °C y ≈ 200–300 Ω a 90 °C. Puede haber otro sensor aparte para el cuadro.  
• **Uso en la ECU:** enriquecimiento en frío, ralentí acelerado, avance, electroventilador y testigo de temperatura.  
• **Fallo:** arranque difícil en frío, consumo alto, humo negro, ventilador funcionando siempre.  
### 3.8 EGR (recirculación de gases de escape)
• **Función del sistema:** reintroduce parte de los gases de escape en la admisión para bajar la temperatura de combustión y reducir los NOx.  
• **Sensor:** posición de la válvula (potenciómetro o Hall) que confirma cuánto abre. Algunos sistemas añaden temperatura o presión diferencial.  
• **Cuándo actúa:** ralentí y cargas parciales con motor caliente; se cierra a plena carga y en frío.  
• **Uso en la ECU:** regular la apertura en lazo cerrado; en diésel se verifica con el MAF (si la EGR abre, entra menos aire fresco).  
• **Fallo:** carbonilla. Agarrotada abierta = humo negro, falta de potencia, ralentí inestable. Agarrotada cerrada = NOx altos y posible picado.  
### 3.9 Sonda lambda (oxígeno)
• **Qué mide:** el oxígeno residual en el escape, para saber si la mezcla es rica o pobre. λ = 1 equivale a 14,7:1 en gasolina.  
• **Zirconio (de salto):** genera 0,1 V con mezcla pobre y 0,9 V con mezcla rica; conmuta alrededor de 0,45 V varias veces por segundo.  
• **Titanio:** cambia de resistencia en vez de generar tensión; necesita alimentación de la ECU.  
• **Banda ancha (5–6 cables):** mide el valor λ exacto mediante una corriente de bombeo; se usa en diésel y gasolina modernos.  
• **Calefactor:** solo funciona por encima de unos 300–350 °C, por eso las calefactadas llevan una resistencia (cables: 1 sin calefactor; 3–4 con calefactor).  
• **Posición:** la anterior al catalizador regula la mezcla; la posterior vigila el catalizador (señal estable ≈ 0,6–0,7 V si el catalizador está bien).  
• **Fallo:** consumo alto, emisiones fuera de norma, catalizador dañado a largo plazo.  
## 4. Resumen y repaso
| Sensor | Mide | Tipo | Cables | Señal típica | Síntoma de fallo |
| --------------- | --------------- | --------------- | --------------- | --------------- | --------------- |
| CKP | RPM y PMS | Inductivo o Hall | 2+malla / 3 | Alterna / cuadrada | No arranca, se cala |
| CMP | Fase (cilindro 1) | Hall | 3 | Cuadrada | Arranque largo |
| MAF | Masa de aire | Película caliente | 3–5 | 1–4,5 V o frecuencia | Falta potencia, humo |
| MAP | Presión colector | Piezorresistivo | 3 | ≈ 1 V ralentí | Consumo, ralentí irregular |
| Picado | Detonación | Piezoeléctrico | 2+malla | Picos 5–15 kHz | Avance retrasado, menos potencia |
| TPS / APP | Posición mariposa / pedal | Potenciómetro o Hall | 3 / 6 | 0,5–4,5 V | Tirones, emergencia |
| IAT | Temperatura aire | NTC | 2 | 2,5 kΩ a 20 °C | Mezcla incorrecta |
| ECT | Temperatura agua | NTC | 2 | 2,5 kΩ a 20 °C | Arranque en frío, consumo |
| EGR | Posición válvula | Potenciómetro o Hall | 3–5 | 0,5–4,5 V | Humo negro, NOx |
| Lambda | Oxígeno en escape | Zirconio / titanio / banda ancha | 1–6 | 0,1–0,9 V | Consumo, emisiones |

## Preguntas para autoevaluarte
1. ¿Por qué se induce alta tensión en el secundario al abrir los platinos y no al cerrarlos?  
2. ¿Qué función tiene el condensador y qué pasa si falla?  
3. ¿Qué diferencia hay entre el avance centrífugo y el de vacío?  
4. ¿Qué es la chispa perdida en un DIS?  
5. ¿Cómo distingues un CKP inductivo de uno Hall por los cables y la señal?  
6. ¿Qué diferencia hay entre medir masa de aire (MAF) y presión (MAP)?  
7. ¿Qué hace la ECU cuando el sensor de picado detecta detonación?  
8. ¿Por qué el pedal electrónico lleva dos pistas?  
9. Un NTC marca −40 °C en diagnosis: ¿qué avería buscas?  
10. ¿Para qué sirve la sonda lambda posterior al catalizador?  

# Texto Original

https://claude.ai/artifact/7rey8ihC5GjufA9RYehZNm?sk=SCWnDpCVZOnNiGtBlOqqNQ#9b882542-5ea2.mkyhwc0bw1s.62
