# Checklist técnico según NTP 399.403

## Estado general

Checklist preliminar para verificar componentes del SFA de 400 Wp. La revisión inicial de módulos fotovoltaicos ya fue realizada en laboratorio mediante registro de placa del panel Tensite EM200-PH. La verificación del sistema se orienta ahora a la instalación con dos módulos de 200 W, controlador MPPT, banco de baterías de 24 V e inversor Victron 24/375.

## Módulos fotovoltaicos

- [x] Verificar marca y modelo: Tensite EM200-PH.
- [x] Registrar potencia máxima, Pmax: 200 W por módulo.
- [x] Registrar voltaje de circuito abierto, Voc: 45.4 V.
- [x] Registrar corriente de cortocircuito, Isc: 5.80 A según sticker del módulo / 5.81 A según ficha técnica.
- [x] Registrar voltaje de máxima potencia, Vmp: 36.7 V.
- [x] Registrar corriente de máxima potencia, Imp: 5.65 A según sticker del módulo / 5.45 A según ficha técnica.
- [x] Registrar coeficiente térmico de Voc: -0.29506 %/°C.
- [x] Registrar coeficiente térmico de Pmax: -0.38001 %/°C.
- [x] Registrar coeficiente térmico de Isc: +0.08558 %/°C.
- [ ] Registrar número de serie del panel 1.
- [ ] Registrar número de serie del panel 2.
- [x] Revisar estado físico del módulo: paneles nuevos, sin daños visibles reportados.
- [x] Revisar características de conexión: caja de conexiones y conectores tipo MC4.
- [ ] Realizar curva I-V del panel 1.
- [ ] Realizar curva I-V del panel 2.
- [ ] Comparar valores medidos de Voc, Isc, Vmp e Imp con los datos de placa y ficha técnica.

## Controlador de carga

- [x] Confirmar modelo de controlador seleccionado: Victron SmartSolar MPPT 100/30.
- [x] Registrar tensión nominal de batería admitida: selección automática 12/24 V.
- [x] Registrar corriente nominal de carga: 30 A.
- [x] Registrar potencia FV nominal admisible a 24 V: 880 W.
- [x] Registrar voltaje máximo de circuito abierto FV: 100 V.
- [x] Registrar corriente máxima de cortocircuito FV: 35 A.
- [x] Validar compatibilidad preliminar con dos módulos de 200 W conectados en serie.
- [x] Revisar valores predeterminados de absorción y flotación: 28.8 V y 27.6 V para banco de 24 V.
- [ ] Configurar tipo de batería GEL o parámetros manuales equivalentes.
- [ ] Configurar corriente máxima de carga en 18 A para respetar la ficha técnica de las baterías.
- [ ] Verificar si el perfil GEL del controlador coincide con los valores de la ficha Tensite.
- [ ] Revisar protección contra polaridad inversa.
- [ ] Revisar protección contra sobrecorriente.
- [ ] Revisar protección contra retorno de corriente.
- [ ] Revisar señalización mediante LEDs, pantalla o interfaz de configuración.

**Nota:** El controlador SmartSolar MPPT 100/30 es compatible de forma preliminar con el arreglo de 400 Wp y banco de 24 V. La tensión máxima del arreglo en serie debe mantenerse por debajo de 100 V; para Lima, el escenario de 10 °C usado en la revisión se considera conservador.

## Balance energético y banco de baterías

- [x] Definir potencia FV instalada: 400 Wp.
- [x] Definir HSP crítica de diseño: 1.44 h.
- [x] Definir energía bruta diaria en mes crítico: 576 Wh/día.
- [x] Expresar energía útil disponible en función de la eficiencia global: E_útil = 576 × η.
- [x] Definir tensión nominal del banco: 24 V, por compatibilidad con el inversor Victron Phoenix 24/375.
- [x] Definir autonomía objetivo preliminar: 1.5 días.
- [x] Considerar que el excedente de verano será recortado por el controlador si la batería está cargada.
- [x] Definir que el SFA alimentará cargas variables de proyectos Tech Lab, no una carga crítica fija única.
- [x] Verificar tipo de batería final: GEL VRLA ciclo profundo.
- [x] Definir banco nuevo de baterías.
- [x] Registrar tensión nominal de cada batería: 12 V.
- [x] Registrar capacidad nominal de cada batería: 100 Ah a C100.
- [x] Definir cantidad de baterías: 2.
- [x] Definir configuración del banco: serie.
- [x] Calcular tensión nominal del banco: 24 V.
- [x] Calcular capacidad nominal del banco: 100 Ah.
- [x] Calcular energía nominal del banco: 2400 Wh.
- [x] Registrar corriente máxima de carga admisible: 18 A.
- [x] Registrar rango de absorción/ciclo para banco de 24 V: 28.60–29.20 V.
- [x] Registrar rango de flotación para banco de 24 V: 27.20–27.60 V.
- [ ] Estimar potencia, tiempo de uso y energía diaria de cada proyecto que se conecte al SFA.
- [ ] Verificar que cada carga conectada se mantenga dentro de la energía disponible y de los límites eléctricos del sistema.
- [ ] Verificar bornes positivo y negativo.
- [ ] Revisar ubicación física, ventilación y accesibilidad del banco.
- [ ] Evitar mezclar baterías nuevas con baterías antiguas u obsoletas.

**Nota:** Dos baterías de 12 V y 100 Ah conectadas en serie forman un banco de 24 V y 100 Ah. La capacidad en Ah no se suma en serie; se suma el voltaje.

## Cableado y protecciones

- [ ] Revisar sección de conductores.
- [ ] Revisar longitud de tramos.
- [ ] Verificar caída de tensión.
- [ ] Revisar terminales y conectores.
- [ ] Revisar fusibles o interruptores DC.
- [ ] Verificar fijación mecánica y canalización.
