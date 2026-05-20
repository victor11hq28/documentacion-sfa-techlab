# Evaluación preliminar de controladores para SFA de 400 Wp

## Panel fotovoltaico disponible

Modelo: Tensite EM200-PH

| Parámetro | Sticker del módulo | Ficha técnica |
|---|---:|---:|
| Pmax | 200 W | 200 W |
| Voc | 45.4 V | 45.40 V |
| Isc | 5.80 A | 5.81 A |
| Vmp | 36.7 V | 36.70 V |
| Imp | 5.65 A | 5.45 A |
| Tolerancia de Voc | ±4 % | No especificada en tabla principal |
| Coeficiente térmico de Pmax | No indicado en sticker | -0.38001 %/°C |
| Coeficiente térmico de Voc | No indicado en sticker | -0.29506 %/°C |
| Coeficiente térmico de Isc | No indicado en sticker | +0.08558 %/°C |
| TONC / NMOT | 45 °C | 45 ± 2 °C |

**Nota:** Para los cálculos preliminares de tensión máxima se toma como referencia el Voc de placa y el coeficiente térmico de Voc de la ficha técnica. Las diferencias menores entre el sticker del módulo y la ficha técnica, especialmente en Isc e Imp, deberán verificarse mediante la medición de curva I-V.

## Arreglo propuesto

La futura instalación considera dos paneles de 200 W:

P_FV = 2 × 200 W = 400 Wp

## Conexión en serie

| Parámetro | Valor |
|---|---:|
| Voc total | 90.8 V |
| Vmp total | 73.4 V |
| Isc total | 5.80 A |
| Imp total | 5.65 A |

Ventaja principal: menor corriente en el lado fotovoltaico, lo que reduce pérdidas por caída de tensión y exigencias sobre el cableado.

Observación: se requiere un controlador MPPT con voltaje máximo de entrada FV superior al Voc corregido del arreglo.

## Conexión en paralelo

| Parámetro | Valor |
|---|---:|
| Voc total | 45.4 V |
| Vmp total | 36.7 V |
| Isc total | 11.60 A |
| Imp total | 11.30 A |

Ventaja principal: menor tensión de entrada FV.

Observación: aumenta la corriente, por lo que se requiere mayor cuidado en cableado, conectores y protecciones.

## Corrección de Voc por baja temperatura

El voltaje de circuito abierto del panel aumenta cuando la temperatura de celda disminuye. Para una verificación conservadora del controlador MPPT 100/30, se evaluó un escenario frío de 10 °C, tomando como referencia las condiciones STC a 25 °C.

Según la ficha técnica del módulo Tensite EM200-PH, el coeficiente térmico de Voc es:

Coeficiente térmico de Voc = -0.29506 %/°C

Diferencia de temperatura considerada:

ΔT = 25 °C - 10 °C = 15 °C

Incremento aproximado de Voc:

15 × 0.29506 % = 4.4259 %

Factor de corrección:

1 + 0.044259 = 1.044259

### Caso sin tolerancia de placa

| Cálculo | Resultado |
|---|---:|
| Voc de un panel a 10 °C | 45.4 V × 1.044259 = 47.41 V |
| Voc de dos paneles en serie a 10 °C | 2 × 47.41 V = 94.82 V |

### Caso con tolerancia positiva de placa

La placa del panel indica una tolerancia de Voc de ±4 %. Considerando el caso más exigente:

| Cálculo | Resultado |
|---|---:|
| Voc máximo de un panel por tolerancia | 45.4 V × 1.04 = 47.22 V |
| Voc máximo de un panel a 10 °C | 47.22 V × 1.044259 = 49.31 V |
| Voc máximo de dos paneles en serie a 10 °C | 2 × 49.31 V = 98.61 V |

Con el escenario considerado, dos paneles en serie podrían alcanzar aproximadamente 94.82 V sin tolerancia de placa, o 98.61 V considerando tolerancia positiva. Por tanto, el controlador MPPT 100/30 cumple para una temperatura de celda de 10 °C, condición conservadora para Lima, aunque queda con margen reducido frente al límite de 100 V.

## Controladores PWM revisados

Los controladores PWM disponibles presentan limitaciones para usar los dos paneles de 200 W en un único sistema, debido a límites de corriente, potencia y tensión de entrada FV.

## Controlador MPPT seleccionado

El controlador seleccionado para la instalación es el Victron SmartSolar MPPT 100/30.

| Parámetro | Valor según ficha técnica |
|---|---:|
| Tensión de batería | Selección automática 12/24 V |
| Corriente nominal de carga | 30 A |
| Potencia FV nominal a 12 V | 440 W |
| Potencia FV nominal a 24 V | 880 W |
| Tensión máxima de circuito abierto FV | 100 V |
| Corriente máxima de cortocircuito FV | 35 A |
| Eficiencia máxima | 98 % |
| Absorción predeterminada | 14.4 V / 28.8 V, ajustable |
| Flotación predeterminada | 13.8 V / 27.6 V, ajustable |

Para el banco de 24 V y un arreglo de 400 Wp, la potencia FV queda por debajo del límite nominal de 880 W indicado para operación a 24 V. La corriente de cortocircuito del arreglo en serie también queda por debajo del límite de 35 A.

La conexión de dos módulos en serie es compatible de forma preliminar con el SmartSolar MPPT 100/30, siempre que no se agreguen más módulos en serie. El punto a vigilar sigue siendo la tensión máxima de circuito abierto: con el escenario de 10 °C y coeficiente térmico real del módulo, el arreglo podría alcanzar aproximadamente 94.82 V sin tolerancia de placa o 98.61 V considerando tolerancia positiva.

## Configuración preliminar del controlador

El controlador debe configurarse para el banco de baterías GEL de 24 V. La ficha del controlador permite valores ajustables de absorción y flotación, por lo que la configuración debe hacerse según los parámetros de la batería seleccionada.

Para las baterías GEL Tensite 12 V 100 Ah conectadas en serie, se debe considerar:

| Parámetro | Valor para una batería 12 V | Valor para banco 24 V |
|---|---:|---:|
| Tensión de carga en ciclos / absorción | 14.30–14.60 V | 28.60–29.20 V |
| Tensión de flotación | 13.60–13.80 V | 27.20–27.60 V |
| Corriente máxima de carga | 18 A | 18 A |

Los valores predeterminados del SmartSolar para 24 V, 28.8 V en absorción y 27.6 V en flotación, se encuentran dentro de los rangos indicados por la ficha de la batería. Sin embargo, debe limitarse la corriente máxima de carga a 18 A para respetar la especificación del banco de baterías GEL. La ecualización debe mantenerse desactivada salvo indicación explícita del fabricante.

## Observación técnica

Para mayor margen de seguridad en tensión FV, un controlador MPPT de 150 V sería más robusto. Sin embargo, el SmartSolar MPPT 100/30 puede considerarse compatible para Lima si se conectan únicamente dos módulos en serie, se trabaja con banco de 24 V y se mantiene como supuesto de diseño una temperatura mínima de celda no menor a 10 °C. Si se desea evaluar escenarios más conservadores, debe recalcularse el Voc corregido.
