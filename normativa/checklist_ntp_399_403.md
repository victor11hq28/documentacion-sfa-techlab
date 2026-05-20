# Checklist técnico según NTP 399.403

## Estado general

Checklist preliminar para verificar componentes del SFA de 400 Wp. La revisión inicial de módulos fotovoltaicos ya fue realizada en laboratorio mediante registro de placa del panel Tensite EM200-PH. La verificación del nuevo controlador MPPT queda pendiente hasta recibir el equipo solicitado.

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

**Nota:** La ficha técnica completa del módulo Tensite EM200-PH ya fue revisada y permite reemplazar el coeficiente térmico asumido por el valor real de Voc. Las diferencias menores entre el sticker del módulo y la ficha técnica, especialmente en Isc e Imp, deberán verificarse mediante la medición de curva I-V.

## Controlador de carga

- [ ] Confirmar modelo exacto del controlador MPPT solicitado.
- [ ] Adjuntar o registrar ficha técnica del controlador.
- [ ] Verificar tensión nominal de operación.
- [ ] Verificar corriente máxima de carga.
- [ ] Verificar voltaje máximo de entrada FV.
- [ ] Revisar potencia FV máxima admisible.
- [ ] Validar compatibilidad con dos módulos de 200 W conectados en serie.
- [ ] Revisar protección contra polaridad inversa.
- [ ] Revisar protección contra sobrecorriente.
- [ ] Revisar protección contra retorno de corriente.
- [ ] Revisar valores de absorción, flotación, corte y reconexión.
- [ ] Revisar señalización mediante LEDs, pantalla o interfaz de configuración.

**Nota:** Los controladores PWM disponibles fueron revisados preliminarmente y presentan limitaciones para un arreglo de 400 Wp. Se indicó que se solicitó un controlador MPPT 100/30, por lo que la validación final queda pendiente hasta confirmar el modelo exacto y contar con su ficha técnica completa.

## Balance energético y banco de baterías

- [x] Definir potencia FV instalada: 400 Wp.
- [x] Definir HSP crítica de diseño: 1.44 h.
- [x] Definir energía bruta diaria en mes crítico: 576 Wh/día.
- [x] Expresar energía útil disponible en función de la eficiencia global: E_útil = 576 × η.
- [x] Definir tensión nominal del banco: 24 V, por compatibilidad con el inversor Victron Phoenix 24/375.
- [x] Definir autonomía objetivo preliminar: 1.5 días.
- [x] Considerar que el excedente de verano será recortado por el controlador si la batería está cargada.
- [x] Definir que el SFA alimentará cargas variables de proyectos Tech Lab, no una carga crítica fija única.
- [ ] Estimar potencia, tiempo de uso y energía diaria de cada proyecto que se conecte al SFA.
- [ ] Verificar que cada carga conectada se mantenga dentro de la energía disponible y de los límites eléctricos del sistema.
- [ ] Verificar tipo de batería final: AGM / GEL / litio / otra.
- [ ] Definir si se comprará un banco nuevo de baterías.
- [ ] Evaluar estado de las baterías actuales y descartar unidades obsoletas.
- [ ] Registrar tensión nominal de cada batería.
- [ ] Registrar capacidad nominal en Ah.
- [ ] Definir cantidad de baterías.
- [ ] Definir configuración del banco: serie / paralelo / serie-paralelo.
- [ ] Calcular capacidad mínima final del banco en Ah.
- [ ] Definir capacidad comercial del banco de baterías.
- [ ] Verificar bornes positivo y negativo.
- [ ] Revisar profundidad máxima de descarga recomendada.
- [ ] Revisar corriente máxima de carga admisible.
- [ ] Revisar recomendaciones de absorción, flotación y ecualización.
- [ ] Evitar mezclar baterías nuevas con baterías antiguas u obsoletas.

**Nota:** El banco de baterías debe ser de 24 V debido al uso del inversor Victron Phoenix 24/375. Si se emplean baterías de 12 V, se requiere al menos una conexión en serie de dos unidades. La capacidad final en Ah queda pendiente hasta confirmar el modelo de batería seleccionado y el criterio de eficiencia global η adoptado para el balance energético.

## Cableado y protecciones

- [ ] Revisar sección de conductores.
- [ ] Revisar longitud de tramos.
- [ ] Verificar caída de tensión.
- [ ] Revisar terminales y conectores.
- [ ] Revisar fusibles o interruptores DC.
- [ ] Verificar fijación mecánica y canalización.
