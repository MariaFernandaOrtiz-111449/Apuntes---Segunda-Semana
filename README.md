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

💡**Ejemplo 1:**
Si tenemos las siguiente funciones de transferencia, primiero debemos determinar cual de ellas es más rapida, y esta será la del lazo interno.
* Función de transferencia 1 = $G_{1} = \frac{e^{-10s}}{15s + 1}$
  
* Función de transferencia 2 = $G_{2} = \frac{0.5 e^{-s}}{2s + 1}$

Podemos darnos cuenta, que en este caso la función de transferencia con una respuesta más rápida es la función 2 ($\tau = 2$) por lo que esta función será del lazo secundario, es decir el lazo interno, así que empezamos con la sincronización del lazo secundario.

**Sintonización Lazo secundario**

$$G_{2} = \frac{0.5 e^{-s}}{2s + 1}$$

$$K_{c2} = \frac{0.9}{K_{2}} * \left[ \frac{\tau 2}{tm} \right]  =  \frac{0.9}{0.5} * \left[ \frac{2}{1} \right] = 3.6$$
$$T_{i2} = 3.33 * tm   =  3.33$$

**Sintonización Lazo primario**

$$T_{Total} = K_{1} * 1 = K_{1}  =  1$$
$$t_{mTotal} = t_{m1} +  t_{m2}  =  10 + 1  =  11$$
$$\tau _{Total} \approx  \tau _{1}  \approx  15$$
$$K _{c1}  =  \frac{1.2}{K _{Total}} * \left[ \frac{\tau  _{Total} }{t _{mTotal}} \right]   =    \frac{1.2}{1} * \left[ \frac{15 }{11} \right]   =   1.63$$
$$T _{i1}  =  2 * T _{mTotal} = 2 * 11  = 22$$
$$T _{d1}  =  0.5 * T _{mTotal} = 0.5 * 11  = 5.5$$

### 1.2. Metodologías empíricas de lazo abierto Austin

#### 1.2.1. Sintonización Lazo Abierto
El método de Austin (1986) permite sintonizar controladores en cascada con una sola prueba, proporcionando ecuaciones de ajuste para un controlador primario PI o PID cuando el secundario es P o PI.

#### 1.2.2. Sintonización 
El método consiste en aplicar un cambio de paso en la señal de la válvula de control y registrar la respuesta de las variables secundarias y primarias. A partir de estas respuestas, se calculan la ganancia, la constante de tiempo y el tiempo muerto de ambos lazos.

| **Controlador**        | **KP**                 |  **Ti**                   | **Td**                   |
|------------------------|------------------------|---------------------------|--------------------------|
| P                      | 0.5 Kcr                | Infinity                  | 0                        |
| PI                     |  0.45 Kcr              | Pcr / 1.2                 | 0                        |
| PID                    |  0.6 Kcr               | Pcr / 2                   | 0.125 Pcr                |

Tabla 1. Método Hang (1994)

### 1.3. Metodologías empíricas de lazo Cerrado

#### 1.3.1. Método Hang (1994)

💡**Ejemplo 2:** Siguiendo el siguiente ejemplos podemos ver el funcionamiento del método Hang

* Función de transferencia 1 = $G_{1} = \frac{e^{-s}}{(s+1)^{2}}$
  
* Función de transferencia 2 = $G_{2} = \frac{e^{-\alpha s}}{\alpha s + 1}$
* Tener en cuenta que: $\alpha = 0.1$

Usando el método de Réle obtenemos los siguientes valores:

$$T_{u2}   =   0.3 s$$
$$K_{u2}   =   \frac{4d}{\pi a}$$

**Sintonización del secundario**

| **Controlador**        | **KP**                 |  **Ti**                   | **Td**                   |
|------------------------|------------------------|---------------------------|--------------------------|
| P                      | 0.5 Kcr                | Infinity                  | 0                        |
| PI                     |  0.45 Kcr              | Pcr / 1.2                 | 0                        |
| PID                    |  0.6 Kcr               | Pcr / 2                   | 0.125 Pcr                |

Tabla 3. Método Hang (1994)

Usando la tabla, y despejando los valores, obtenemos que:

$$K_{p2}   =   0.45  * K_{u2}   =   0.45 * 1.99   =   0.89$$
$$T_{i2}   =   \frac{T_{u2} }{1.2}   =  \frac{0.3}{1.2}   =   0.25$$

**Sintonización del primario**
Se ubica el secundario sintonizado dentro del lazo del primario para realizar la respectiva sintonización utilizando nuevamente el método del relé.
Cuando se haya sintonizado por el método del réle, utilizamos nuevamente la Tabla 3., y obtenemos los siguientes resultados:

$$K_{p1}   =   0.45  * K_{u1}   =   0.45 * 2.27   =   1.02$$
$$T_{i1}   =   \frac{T_{u1} }{1.2}   =  \frac{5.56}{1.2}   =   4.63$$

## 2. Ejercicios

Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 3. Conclusiones
El control en cascada mejora la estabilidad y precisión de un sistema al utilizar dos lazos de control: uno primario y uno secundario. La sintonización adecuada de estos lazos permite optimizar la respuesta del sistema ante perturbaciones y variaciones en la referencia.

## 4. Referencias

