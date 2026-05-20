# Balance energético y dimensionamiento preliminar del banco de baterías

## Criterio de diseño

El dimensionamiento energético del SFA de 400 Wp se realiza considerando el mes crítico de menor recurso solar. Para esta etapa se adopta una HSP de diseño de 1.44 h, valor previamente identificado para el escenario más desfavorable.

Los valores de 5 a 6 HSP observables en temporada de verano se consideran únicamente para evaluar excedentes de generación. Estos valores no deben usarse para definir la autonomía mínima del sistema, ya que podrían sobredimensionar la expectativa de generación disponible durante invierno.

## Enfoque de carga variable

El SFA no se asigna a una carga fija única. Su función prevista es alimentar proyectos del Tech Lab según disponibilidad energética, siempre dentro de los límites eléctricos y energéticos del sistema.

Por ello, cada proyecto que se conecte deberá estimar como mínimo:

- potencia de operación;
- tiempo diario de uso;
- energía diaria requerida;
- tipo de alimentación requerida: DC o AC mediante inversor;
- condición de uso: continua, intermitente o temporal.

La conexión de cargas deberá evaluarse en función de la energía disponible del sistema, el estado del banco de baterías y la temporada de operación. En invierno se deberá usar como referencia el escenario de diseño con HSP crítica; en verano podrá existir mayor disponibilidad energética.

## Generación estimada en mes crítico

La energía bruta diaria del arreglo fotovoltaico se calcula como:

E_FV,bruta = P_FV × HSP

Para el arreglo de 400 Wp:

E_FV,bruta = 400 Wp × 1.44 h = 576 Wh/día

La energía útil disponible para cargas no se fija como un valor absoluto, sino que se expresa en función de una eficiencia global preliminar η. Esta eficiencia representa pérdidas por controlador, batería, cableado, temperatura, suciedad y conversión DC/DC o DC/AC.

E_útil = E_FV,bruta × η

E_útil = 576 × η

| η global asumida | Energía útil estimada |
|---:|---:|
| 0.60 | 345.6 Wh/día |
| 0.70 | 403.2 Wh/día |
| 0.80 | 460.8 Wh/día |

Para cálculos preliminares se puede usar η = 0.70 como caso base, lo que entrega aproximadamente 403 Wh/día útiles en el mes crítico. Este valor no debe entenderse como un límite fijo, sino como una referencia de diseño dependiente de la eficiencia real del sistema.

## Banco de baterías seleccionado

El banco previsto se compone de dos baterías Tensite GEL 12-100 conectadas en serie.

| Parámetro | Valor |
|---|---:|
| Tipo de batería | GEL VRLA ciclo profundo |
| Cantidad de baterías | 2 |
| Tensión nominal por batería | 12 V |
| Capacidad nominal por batería | 100 Ah a C100 |
| Capacidad por batería a 10 h | 91 Ah |
| Configuración | Serie |
| Tensión nominal del banco | 24 V |
| Capacidad nominal del banco | 100 Ah |
| Energía nominal del banco | 24 V × 100 Ah = 2400 Wh |
| Energía útil aproximada al 50 % DoD | 1200 Wh |

En una conexión en serie se suma el voltaje, pero la capacidad en Ah se mantiene. Por ello, dos baterías de 12 V y 100 Ah en serie forman un banco de 24 V y 100 Ah, no un banco de 200 Ah.

## Autonomía objetivo

Para el banco de baterías se adopta como criterio preliminar una autonomía de 1.5 días. Este valor permite cubrir periodos cortos de baja generación sin sobredimensionar excesivamente el almacenamiento.

| Parámetro | Valor preliminar |
|---|---:|
| Tensión nominal del banco | 24 V |
| Autonomía objetivo | 1.5 días |
| Profundidad máxima de descarga considerada | 50 % |
| Eficiencia de batería considerada | 85 % |

La tensión nominal del banco se define en 24 V debido a la compatibilidad requerida con el inversor Victron Phoenix 24/375 disponible en laboratorio.

## Fórmula de capacidad del banco

La capacidad mínima del banco de baterías se estima mediante:

Capacidad del banco [Ah] = Energía diaria de la carga [Wh/día] × días de autonomía ÷ (Voltaje del banco × profundidad de descarga × eficiencia de batería)

Si se toma como energía diaria de referencia la energía útil del mes crítico:

E_carga,diseño = 576 × η

Entonces:

Capacidad [Ah] = (576 × η × 1.5) ÷ (24 × 0.50 × 0.85)

Capacidad [Ah] = (576 × η × 1.5) ÷ 10.2

Capacidad [Ah] ≈ 84.7 × η

| η global asumida | Capacidad mínima estimada para 1.5 días |
|---:|---:|
| 0.60 | 50.8 Ah @ 24 V |
| 0.70 | 59.3 Ah @ 24 V |
| 0.80 | 67.8 Ah @ 24 V |

Con η = 0.70 como caso base, la capacidad mínima estimada es aproximadamente 59.3 Ah a 24 V. El banco seleccionado de 24 V y 100 Ah supera este mínimo preliminar y proporciona mayor margen para cargas variables de proyectos Tech Lab.

## Parámetros de carga de las baterías

Según la ficha técnica de la batería GEL Tensite 12-100, los parámetros principales por unidad de 12 V son:

| Parámetro | Valor por batería 12 V | Valor para banco 24 V |
|---|---:|---:|
| Tensión de carga en ciclos / absorción | 14.30–14.60 V | 28.60–29.20 V |
| Tensión de flotación | 13.60–13.80 V | 27.20–27.60 V |
| Corriente máxima de carga | 18 A | 18 A |
| Corriente máxima de descarga | 900 A durante 5 s | 900 A durante 5 s |
| Peso aproximado por batería | 26.2 kg ± 3 % | 52.4 kg ± 3 % total |

La corriente máxima de carga del banco no se duplica al conectar las baterías en serie. Por ello, aunque el controlador Victron SmartSolar MPPT 100/30 pueda entregar hasta 30 A, debe configurarse una corriente máxima de carga de 18 A para respetar la especificación de las baterías GEL.

## Configuración del banco de baterías

El banco debe configurarse a 24 V. La conexión prevista es:

12 V + 12 V = 24 V

No se recomienda mezclar estas baterías nuevas con baterías antiguas u obsoletas, ni con baterías de diferente tecnología, capacidad o estado de salud. En caso de ampliación futura, las ramas en paralelo deberán estar formadas por baterías equivalentes y en condiciones similares.

## Comportamiento ante batería cargada

Cuando el banco de baterías alcanza su estado de carga objetivo, el controlador reduce la corriente de carga y pasa a una etapa de absorción o flotación, según corresponda. En esta condición, aunque los módulos fotovoltaicos sigan recibiendo radiación, no se extrae necesariamente toda la potencia disponible del arreglo.

La energía excedente se recorta o no se aprovecha, lo cual es normal en sistemas fotovoltaicos autónomos. Este comportamiento no representa un problema para los módulos fotovoltaicos. La protección principal depende de que el controlador esté correctamente seleccionado y configurado según el tipo de batería, evitando sobrecarga, tensión de flotación incorrecta o etapas de ecualización no compatibles.

## Excedente energético en verano

El sistema se dimensiona para el mes crítico. En verano, con 5 a 6 HSP, la generación disponible será considerablemente mayor. Cuando el banco de baterías alcance su estado de carga objetivo, el controlador limitará la potencia tomada del arreglo FV.

Como mejora futura, se puede evaluar el uso de cargas secundarias no críticas, activadas únicamente cuando el banco de baterías se encuentre suficientemente cargado. Estas cargas no deben comprometer la autonomía de la carga principal ni superar los límites eléctricos del controlador, baterías, inversor o protecciones.

## Pendientes

- Configurar en el controlador el tipo de batería GEL o los parámetros manuales equivalentes.
- Configurar corriente máxima de carga en 18 A.
- Verificar si el perfil GEL del controlador coincide con los valores de la ficha Tensite.
- Estimar potencia, tiempo de uso y energía diaria de cada proyecto que se conecte al SFA.
- Verificar que cada carga conectada se mantenga dentro de la energía disponible y de los límites eléctricos del sistema.
