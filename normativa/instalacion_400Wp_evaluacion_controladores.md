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

## Arreglo propuesto

La futura instalación considera dos paneles de 200 W:

\[
P_{FV}=2 \times 200W = 400Wp
\]

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

## Controladores PWM revisados

Los controladores PWM disponibles presentan limitaciones para usar los dos paneles de 200 W en un único sistema, debido a límites de corriente, potencia y tensión de entrada FV.

## Controlador MPPT solicitado

Se indicó que se solicitó un controlador Victron BlueSolar MPPT 100/30.

Este controlador resulta viable para dos paneles en serie y banco de 24 V. Sin embargo, el margen de tensión frente al límite de 100 V debe revisarse considerando la tolerancia del módulo y el incremento de Voc por baja temperatura.

## Observación técnica

Para mayor margen de seguridad, un controlador MPPT de 150 V sería más robusto. Sin embargo, el MPPT 100/30 puede considerarse compatible si no se agregan más módulos en serie y se valida el voltaje máximo del arreglo.
