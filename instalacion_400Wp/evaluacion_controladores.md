# Evaluación preliminar de controladores para SFA de 400 Wp

## Panel fotovoltaico disponible

Modelo: Tensite EM200-PH

| Parámetro | Valor |
|---|---:|
| Pmax | 200 W |
| Voc | 45.4 V |
| Isc | 5.80 A |
| Vmp | 36.7 V |
| Imp | 5.65 A |
| Tolerancia de Voc | ±4 % |

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

## Corrección preliminar de Voc por baja temperatura

El voltaje de circuito abierto del panel aumenta cuando la temperatura de celda disminuye. Para una verificación conservadora del controlador MPPT 100/30, se evaluó un escenario frío de 10 °C, tomando como referencia STC a 25 °C.

Como no se cuenta aún con el coeficiente térmico exacto del datasheet completo del panel, se asumió un valor típico para módulos cristalinos:

Coeficiente térmico aproximado de Voc = -0.30 %/°C

Diferencia de temperatura considerada:

ΔT = 25 °C - 10 °C = 15 °C

Incremento aproximado de Voc:

15 × 0.30 % = 4.5 %

### Caso sin tolerancia de placa

| Cálculo | Resultado |
|---|---:|
| Voc de un panel a 10 °C | 45.4 V × 1.045 = 47.44 V |
| Voc de dos paneles en serie a 10 °C | 2 × 47.44 V = 94.88 V |

### Caso con tolerancia positiva de placa

La placa del panel indica una tolerancia de Voc de ±4 %. Considerando el caso más exigente:

| Cálculo | Resultado |
|---|---:|
| Voc máximo de un panel por tolerancia | 45.4 V × 1.04 = 47.22 V |
| Voc máximo de un panel a 10 °C | 47.22 V × 1.045 = 49.35 V |
| Voc máximo de dos paneles en serie a 10 °C | 2 × 49.35 V = 98.70 V |

## Controladores PWM revisados

Los controladores PWM disponibles presentan limitaciones para usar los dos paneles de 200 W en un único sistema, debido a límites de corriente, potencia y tensión de entrada FV.

## Controlador MPPT solicitado

Se indicó que se solicitó un controlador Victron BlueSolar MPPT 100/30.

Este controlador resulta viable para dos paneles en serie y banco de 24 V. Sin embargo, el margen de tensión frente al límite de 100 V debe revisarse considerando la tolerancia del módulo y el incremento de Voc por baja temperatura.

Con el escenario asumido de 10 °C, dos paneles en serie podrían alcanzar aproximadamente 94.88 V sin tolerancia de placa, o 98.70 V considerando tolerancia positiva. Por tanto, el controlador de 100 V cumple de forma preliminar, pero queda con margen reducido.

## Observación técnica

Para mayor margen de seguridad, un controlador MPPT de 150 V sería más robusto. Sin embargo, el MPPT 100/30 puede considerarse compatible si no se agregan más módulos en serie, se trabaja con banco de 24 V y se valida el voltaje máximo del arreglo con el datasheet completo del panel.
