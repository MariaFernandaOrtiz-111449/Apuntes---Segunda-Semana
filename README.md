# Apuntes---Segunda-Semana
Apuntes control de movimiento primer corte, Segunda Semana

# CONTROL CASCADA
El control en cascada se utiliza en sistemas en los que sea necesario mejorar la estabilidad y el rendimiento de un proceso, y que con los procesos convencionales de control no se pudo lograr. Se basa en el uso de dos o más lazos de control anidados, donde un controlador primario (casi siempre es el lazo externo) regula una variable principal y su salida se usa como referencia para un controlador secundario (casi siempre el lazo interno), que regula una variable intermedia del sistema.

![]()

* Lazo primario (externo): Controla la variable de proceso principal (PV) y envía su señal de salida como referencia al lazo secundario.
* Lazo secundario (interno): Responde más rápido y ajusta una variable intermedia que afecta directamente la variable principal, mejorando la respuesta del sistema.

>🔑 *Sintonización:* La sintonización de controladores se difine como el proceso usado para ajustar los parámetros de un controlador, y con ello optimizar el desempeño de un sistema de control. Su objetivo principal es lograr una respuesta estable, rápida y precisa ante cambios en la referencia o perturbaciones externas al sistema.
>
>🔑 *Lazo Abierto:* Un lazo abierto es un tipo de sistema de control en el que la salida no tiene retroalimentación hacia la entrada, es decir, el sistema opera sin corregir automáticamente su comportamiento en función de la respuesta obtenida.
>
>🔑 *Lazo Cerrado:* Un lazo cerrado es un sistema de control que utiliza retroalimentación para comparar la salida con una referencia y ajustar automáticamente la entrada con el objetivo de minimizar el error.

## 1. MÉTODOS DE SINTONIZACIÓN
Para la sintonización de controles tipo cascada, tenemos los siguiente métodos:

### 1.1. Metodologías empíricas de lazo abierto

#### 1.1.1. Sintonización Lazo Abierto
En algunos sistemas, se pueden realizar pruebas de lazo abierto por separado para cada variable del control en cascada. Estas pruebas permiten sintonizar los controladores con métodos conocidos, considerando la interacción entre ambos lazos.

Si tenemos las siguiente funciones de transferencia, primiero debemos determinar cual de ellas es más rapida, y esta será la del lazo interno.
* Función de transferencia 1 = $G_{1} = \frac{e^{-10s}}{15s + 1}$
  
* Función de transferencia 2 = $G_{2} = \frac{0.5 e^{-s}}{2s + 1}$

Podemos darnos cuenta, que en este caso la función de transferencia con una respuesta más rápida es la función 2 ($\tau = 2$) por lo que esta función será del lazo secundario, es decir el lazo interno, así que empezamos con la sincronización del lazo secundario.

$$G_{2} = \frac{0.5 e^{-s}}{2s + 1}$$

$$K_{c2} = \frac{0.9}{K_{2}} * \left[ \frac{\tau 2}{tm} \right]  =  \frac{0.9}{0.5} * \left[ \frac{2}{1} \right] = 3.6$$

### 1.2. Metodologías empíricas de lazo abierto Austin

#### 1.2.1. Sintonización Lazo Abierto
El método de Austin (1986) permite sintonizar controladores en cascada con una sola prueba, proporcionando ecuaciones de ajuste para un controlador primario PI o PID cuando el secundario es P o PI.

#### 1.2.2. Sintonización 
El método consiste en aplicar un cambio de paso en la señal de la válvula de control y registrar la respuesta de las variables secundarias y primarias. A partir de estas respuestas, se calculan la ganancia, la constante de tiempo y el tiempo muerto de ambos lazos.





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
