# Balance energético y dimensionamiento preliminar del banco de baterías

## Criterio de diseño

El dimensionamiento energético del SFA de 400 Wp se realiza considerando el mes crítico de menor recurso solar. Para esta etapa se adopta una HSP de diseño de 1.44 h, valor previamente identificado para el escenario más desfavorable.

Los valores de 5 a 6 HSP observables en temporada de verano se consideran únicamente para evaluar excedentes de generación. Estos valores no deben usarse para definir la autonomía mínima del sistema, ya que podrían sobredimensionar la expectativa de generación disponible durante invierno.

## Generación estimada en mes crítico

| Parámetro | Valor |
|---|---:|
| Potencia FV instalada | 400 Wp |
| HSP de diseño | 1.44 h |
| Energía bruta diaria | 400 W × 1.44 h = 576 Wh/día |
| Eficiencia preliminar del sistema | 70 % |
| Energía útil estimada | 576 Wh/día × 0.70 = 403 Wh/día |

Con una HSP de diseño de 1.44 h, el sistema de 400 Wp podría entregar aproximadamente 403 Wh/día útiles en el mes crítico. Esto equivale a sostener una carga continua promedio cercana a 16.8 W durante 24 h.

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

Con los supuestos preliminares:

Capacidad [Ah] = E_carga × 1.5 ÷ (24 × 0.50 × 0.85)

Capacidad [Ah] = E_carga × 1.5 ÷ 10.2

## Estimación preliminar según carga continua

Como aún falta confirmar el consumo real de la carga crítica, se evalúan escenarios de potencia continua.

| Carga continua | Consumo diario | Capacidad mínima estimada |
|---:|---:|---:|
| 5 W | 120 Wh/día | 17.6 Ah @ 24 V |
| 10 W | 240 Wh/día | 35.3 Ah @ 24 V |
| 15 W | 360 Wh/día | 52.9 Ah @ 24 V |
| 20 W | 480 Wh/día | 70.6 Ah @ 24 V |

Para una carga crítica continua entre 10 W y 15 W, se recomienda evaluar un banco comercial de 24 V entre 40 Ah y 60 Ah. Si la carga se aproxima a 20 W continuos, conviene considerar un banco cercano a 24 V 80 Ah o superior.

## Configuración del banco de baterías

El banco debe configurarse a 24 V. Si se emplean baterías de 12 V, se requieren al menos dos unidades conectadas en serie:

12 V + 12 V = 24 V

En una conexión en serie se suma el voltaje, pero la capacidad en Ah se mantiene igual a la capacidad de cada batería. Por ejemplo, dos baterías de 12 V y 60 Ah conectadas en serie forman un banco de 24 V y 60 Ah.

Si se requiere mayor capacidad, se pueden conectar ramas serie idénticas en paralelo. No se recomienda mezclar baterías de diferente tecnología, capacidad, antigüedad o estado de salud, ya que esto puede producir desbalances de carga y descarga.

## Comportamiento ante batería cargada

Cuando el banco de baterías alcanza su estado de carga objetivo, el controlador reduce la corriente de carga y pasa a una etapa de absorción o flotación, según corresponda. En esta condición, aunque los módulos fotovoltaicos sigan recibiendo radiación, no se extrae necesariamente toda la potencia disponible del arreglo.

La energía excedente se recorta o no se aprovecha, lo cual es normal en sistemas fotovoltaicos autónomos. Este comportamiento no representa un problema para los módulos fotovoltaicos. La protección principal depende de que el controlador esté correctamente seleccionado y configurado según el tipo de batería, evitando sobrecarga, tensión de flotación incorrecta o etapas de ecualización no compatibles.

## Excedente energético en verano

El sistema se dimensiona para el mes crítico. En verano, con 5 a 6 HSP, la generación disponible será considerablemente mayor. Cuando el banco de baterías alcance su estado de carga objetivo, el controlador limitará la potencia tomada del arreglo FV.

Como mejora futura, se puede evaluar el uso de cargas secundarias no críticas, activadas únicamente cuando el banco de baterías se encuentre suficientemente cargado. Estas cargas no deben comprometer la autonomía de la carga principal.

## Pendientes

- Confirmar consumo diario de la carga crítica.
- Definir modelo final de baterías.
- Confirmar si se comprará un banco nuevo de baterías.
- Verificar estado de las baterías actualmente disponibles y descartar unidades obsoletas.
- Definir cantidad de baterías y configuración serie/paralelo.
- Verificar parámetros de carga recomendados por el fabricante: absorción, flotación, corriente máxima de carga y ecualización.
