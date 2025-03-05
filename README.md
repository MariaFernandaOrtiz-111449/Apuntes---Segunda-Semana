# Apuntes---Segunda-Semana
Apuntes control de movimiento primer corte, Segunda Semana

# CONTROL CASCADA
El control en cascada se utiliza en sistemas en los que sea necesario mejorar la estabilidad y el rendimiento de un proceso, y que con los procesos convencionales de control no se pudo lograr. Se basa en el uso de dos o más lazos de control anidados, donde un controlador primario (casi siempre es el lazo externo) regula una variable principal y su salida se usa como referencia para un controlador secundario (casi siempre el lazo interno), que regula una variable intermedia del sistema.

![]()

* Lazo primario (externo): Controla la variable de proceso principal (PV) y envía su señal de salida como referencia al lazo secundario.
* Lazo secundario (interno): Responde más rápido y ajusta una variable intermedia que afecta directamente la variable principal, mejorando la respuesta del sistema.

## 1. MÉTODOS DE SINTONIZACIÓN
Son dispositivso que convierten la energía eléctrica en energía mecánica a través de la interacción de campos magnéticos, esto mediante el paso de corriente eléctrica por un devanado, generando un campo magnético que induce el movimiento de un rotor. Se utilizan ampliamente en maquinaria industrial, electrodomésticos, vehículos eléctricos y sistemas automatizados, debido a su eficiencia, precisión y facilidad de control. 

>🔑 *Motores DC:* Los motores DC o motores de corriente continua, son dispositivos electromecánicos capaces de convertir energía eléctrica en energía mecánica.
>
>🔑 *Motores AC Asíncrono:* También conocidos como motores de inducción, son motores que funcionan con corriente alterna (AC), pero al ser asíncronos la velocidad de rotación no es igual a la velocidad del campo magnéticos del estator. 
>
>🔑 *Motores AC Síncrono:* Son motores que funcionan con corriente alterna (AC), pero al ser asíncronos la velocidad de rotación es exactamente igual a la velocidad del campo magnéticos del estator, esto hace que no haya deslizamiento, osea que el rotor gira en síncronica con el campo magnético del estator.
>
>🔑 *Servomotores:* Se asocia a un sistemas que es capaz se seguir referencias, es decir que sigue cambios en determinado tiempo, estas referencias pueden llegar a ser de posición, velocidad o torque mediante un sistema de control.

### 1.1. Motores Corriente Continua
Estos motores contienen las siguientes caracteristicas fisicas:
* Estator: El devanado inductor genera el campo magnético de excitación. Está compuesto por una corona de material ferromagnético (culata) con polos en su interior, alrededor de los cuales se enrollan los devanados de excitación que crean el campo magnético al circular corriente.
* Rotor: Está constituido por una pieza cilíndrica ranurada de material ferromagnético, donde se aloja el devanado inducido cerrado en las ranuras del rotor.
* Colector de Delgas: Es un conjunto de láminas de cobre aisladas entre sí que giran con el rotor y están conectadas eléctricamente a las bobinas del devanado inducido, permitiendo su conexión al exterior.
  
En cuestiones industriales estos tipos de motores tienen varias aplicaciones, por lo que podemos resaltas las siguientes ventajas y desventajas:

| **Ventajas**                                 | **Desventajas**                                                           |
|----------------------------------------------|---------------------------------------------------------------------------|
| • Control más simple                         | • Requiere mantenimiento e inspección periódicas                          |
| • Driver de potencia más simple              | • No se usa en entornos limpios debido a la abrasión de las escobillas    |
| • Bajo precio en bajas capacidades           | • No se puede utilizar para altos torques                                 |
| • Alta eficiencia en aplicaciones pequeñas   | • Sus imanes pueden sufrir desmagnetización con el tiempo                 |

Tabla 1. Motores DC

### 1.2. Motores Corriente Alterna - Asíncronos
El motor funciona mediante un campo magnético giratorio generado en el devanado inductor del estator. Al atravesar el devanado del rotor, induce fuerzas electromagnéticas que generan corrientes, provocando una reacción que hace girar el motor a una velocidad inferior a la de sincronismo.
  
En cuestiones industriales estos tipos de motores tienen varias aplicaciones, por lo que podemos resaltas las siguientes ventajas y desventajas:

| **Ventajas**                                 | **Desventajas**                                                           |
|----------------------------------------------|---------------------------------------------------------------------------|
| • Poco mantenimiento                         | • Baja eficiencia en aplicaciones pequeñas                                |
| • Excelente resistencia al entorno           |  Control más complicado que el DC por las señales de potencia             |
| • Alta velocidad y alto torque               | • Puede sufrir cambios en sus características debido a temperaturas       |
| • Alta eficiencia en aplicaciones grandes    |                                                                           |
| • Estructura robusta                         |                                                                           |

Tabla 2. Motores AC Asíncronicos

### 1.3. Motores Corriente Alterna - Síncronos
Son máquinas eléctricas cuya velocidad de rotación depende de la frecuencia de la red AC, manteniendo igual velocidad entre el rotor y el campo magnético del estator. Los imanes de campo se montan en el rotor y se excitan con corriente continua, mientras que las bobinas de armadura, divididas en tres partes, se alimentan con corriente trifásica. Estos motores contienen las siguientes caracteristicas fisicas:
* Estator:  Bobinado trifásico para producir el campo magnético giratorio.
* Rotor: Tiene unos imanes o bobinas de excitación recorridas por una corriente continua. Gira a la velocidad del campo magnético.
* Anillos Rozantes: Son anillos metálicos que sirven para alimentar de corriente continua al rotor.

Se debe tener en cuenta que para iniciar el motor síncronico se debe aplica una señal alterna trifásica al estator y una señal DC al rotor, generando un campo magnético con polaridad. El campo del estator atrae al del rotor, provocando su giro a velocidad de sincronismo.
  
En cuestiones industriales estos tipos de motores tienen varias aplicaciones, por lo que podemos resaltas las siguientes ventajas y desventajas:

| **Ventajas**                                     | **Desventajas**                                                           |
|--------------------------------------------------|---------------------------------------------------------------------------|
| • Muy poco mantenimiento                         | • Control de dificultad intermedia                                        |
| • Excelente resistencia al entorno               | • Se requiere respuesta 1:1 entre driver motor                            |
| • Compactos y ligeros                            | • Sus imanes pueden sufrir desmagnetización con el tiempo                 |
| • Alta eficiencia en todo tipo de aplicaciones   |                                                                           |

Tabla 3. Motores AC Síncronicos

### 1.4. Servomotores
**Modelo por corriente de armadura**
* Parte Eléctrica: $\upsilon a= La*Ia + Ra*Ia + Vb$
* Parte Magnética: $Tm = ( Ka*Kc*Ic )*Ia( t ) = K\tau *Ia( t )$  $Vb = Ke* \omega$  $Tm = Tc + Tp$
* Parte Mecánica: $J*\frac{\partial^2 \theta }{\partial t^2  } + b*\frac{\mathrm{d} \theta }{\mathrm{d} t} + R\theta = \tau ( t )$
$La * \frac{\mathrm{d} ( \frac{J \theta   + b\theta  + K\theta }{K\tau } )}{\mathrm{d} t} + Ra * ( \frac{J \theta   + b\theta  + K\theta }{K\tau } ) + Ke \theta  = \upsilon a$

## 2. SENSORES
Un sensores un dispositivo que detecta cambios en una magnitud física o química, como temperatura, presión o luz, y los convierte en señales eléctricas para su procesamiento. Se usa en diversos sistemas para monitoreo y automatización.

>🔑 *Encoder:* Un encoder es un sensor que convierte el movimiento (rotación o desplazamiento) en señales eléctricas para medir posición, velocidad o dirección en motores y sistemas automatizados.
>
>🔑 *Resolver:* Es un sensor electromecánico que mide la posición angular y la velocidad de un eje, utilizando señales eléctricas sin necesidad de componentes electrónicos en el rotor, lo que lo hace resistente y preciso. 

Los servomecanismos utilizan sensores para medir corriente (torque), posición y velocidad, asegurando el cumplimiento de las rutinas de movimiento necesarias para diversas aplicaciones. Sin estas mediciones, no se puede garantizar un control preciso.
Se analizarán algunos tipos de sensores que existen, especialmente los encoder u otros sensores que nos permitan hacer mediciones de pulsos de un motor.

### 2.1. Encoders
Generalmente son usados para medir tanto la posición como la velocidad del eje de cualquier tipo de motor.
* Encoders Absolutos: Tienen un Código digital de posición absoluta para una sola revolución y un contador de revoluciones.
* Encoders Incrementales: Generan un número específico de pulsos por unidad de longitud de movimiento lineal.

Comparandos ambos tipos de encoders, tenemos que:

| **Elemento**              | **Encoder Incremental**                 |  **Encoder Absoluto**                                                     |
|---------------------------|-----------------------------------------|---------------------------------------------------------------------------|
| Salida                    | Salida aumenta incrementalmente         | Hay posiciones absolutas en una revolución                                |
| Reinicialización          | Operación de retorno durante encendido  | No require ninguna operación de retorno ya que se sabe siempre su posición dentro de una revolución   |
| Precio                    | Bajo                                    |Alto                                                                        |
| Estructura                | ![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/7c772e8d44d86a24e2e5148ac6cf6bbda825b5d9/Encoder%20incremental.png)  |  ![](https://github.com/MariaFernandaOrtiz-111449/Apuntes---Tercera-Semana/blob/b67c06e9965e10d66c7d25e072653e2fdb2df51d/Encoder%20Absoluto.png)            |
|Adicionales                |  Solamente se detectan pulsos           | Hay un Código perforado en el encoder. El mas usado es gray                |

### 2.2. Resolver
Un resolver es un sensor analógico de posición angular con un rotor y un estator embobinados. Su funcionamiento es similar al de un transformador, donde la amplitud inducida en el rotor varía según la posición relativa. Existen modelos con y sin escobillas.
* **Voltajes del resolver**: entre 2V RMS y 40V RMS.  
* **Frecuencia de operación**: 50 Hz a 20 kHz.  
* **Relación de transformación**: 0.2 V/V a 1 V/V.

### 2.3. Medición de Torque
torque se infiere a partir de la corriente, debido a su relación aproximadamente lineal.   
* **Shunt**: Usa una pequeña resistencia para medir voltaje y aplicar la ley de Ohm.  
* **Efecto Hall**: Detecta cambios en el campo magnético y, por la ley de Faraday, permite obtener la corriente.

## 3. DRIVERS DE POTENCIA
Un driver es un amplificador que convierte señales de control de baja potencia en señales de alta potencia (voltaje y/o corriente) para alimentar actuadores como motores, por lo que también se le conoce como amplificador. Cada eje requiere su propio driver y controlador. En los servomotores modernos, el controlador gestiona la retroalimentación de posición y velocidad, mientras que el driver maneja la retroalimentación de corriente.
El manejo del driver se realiza mediante PWM (modulación por ancho de pulso), el estándar industrial para motores DC y AC, debido a su alta eficiencia. Algunos de los ejemplos de drivers de potencia que se pueden encontrar en el mercado, y que son bastante usados son:

* Puente H
* L293 y L298 (AN240/1288)

## 4. Ejercicios
**Validación de Modelo**
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 5. Conclusiones
Los motores eléctricos, junto con los sensores y drivers, forman la base de innumerables aplicaciones industriales y tecnológicas. Su correcto funcionamiento depende de una integración efectiva de los diferentes componentes, desde la generación del movimiento hasta su regulación mediante señales de control y retroalimentación.
El uso de tecnologías como PWM en los drivers y la incorporación de sensores de posición y corriente han permitido aumentar la eficiencia y precisión de los sistemas de automatización. Comprender estos conceptos es esencial para diseñar y optimizar motores en diversas aplicaciones, desde robótica hasta maquinaria industrial, garantizando un desempeño confiable y eficiente.

## 6. Referencias
* CHAPMAN. 2005. Maquinas eléctricas. Madrid: McGraw-Hill Interamericana
* LANGSDORF. 1968. Principios de las maquinas de corriente continua. McGrawHill
* SERRANO IRIBARNEGARAY. 1989: Fundamentos de maquinas eléctricas rotativas. Marcombo.
* https://www.swe.siemens.com/spain/web/es/industry/drive_tech/variadores /Pages/Variadores.aspx
* https://www.areatecnologia.com/electricidad/motor-trifasico.html
* https://www.areatecnologia.com/electricidad/motores-corrientecontinua.html
