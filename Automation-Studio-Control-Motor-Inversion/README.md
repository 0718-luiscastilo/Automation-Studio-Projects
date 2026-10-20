# Control de motor con inversión de giro y temporizadores en Automation Studio

## Descripción

Práctica educativa de control de motor mediante lógica Ladder. El
sistema arranca hacia adelante; al pulsar Backward, se detiene 5
segundos, gira hacia atrás durante 10 segundos, se detiene otros 5
segundos y finaliza sin rearranque automático.

## Secuencia de funcionamiento

1.  **Adelante:** el motor arranca al activar la orden Forward.
2.  **Solicitud de reversa:** al pulsar Backward, se desactiva la etapa
    de avance y el motor queda detenido.
3.  **Primera espera:** el temporizador TON `T4:2` cuenta 5 segundos
    mientras está activa la etapa `M2`.
4.  **Giro hacia atrás:** al finalizar `T4:2`, se activa `M3`; el motor
    gira en sentido inverso durante 10 segundos, medidos por `T4:3`.
5.  **Parada final:** al terminar `T4:3`, se activa `M4`, se desactiva
    la etapa de reversa y el motor queda detenido. `T4:4` cuenta 5
    segundos.
6.  **Fin del ciclo:** después de los últimos 5 segundos, el motor
    permanece detenido. No se produce rearranque automático hacia
    adelante.

## Etapas y temporizadores

  -----------------------------------------------------------------------
  Marca / temporizador                Función
  ----------------------------------- -----------------------------------
  `M1`                                Etapa de giro hacia adelante

  `M2`                                Etapa de parada previa a la reversa

  `M3`                                Etapa de giro hacia atrás

  `M4`                                Etapa de parada final

  `T4:2`                              TON de 5 segundos antes de reversa

  `T4:3`                              TON de 10 segundos de giro hacia
                                      atrás

  `T4:4`                              TON de 5 segundos de parada final

  `OUT0`                              Salida asignada al giro hacia
                                      adelante; verificar el mapeo real

  `OUT1`                              Salida asignada al giro hacia
                                      atrás; verificar el mapeo real
  -----------------------------------------------------------------------

Verifica las direcciones reales de entradas y salidas en el proyecto de
Automation Studio.

## Objetivos de aprendizaje

-   Programar una secuencia de motor con lógica Ladder.
-   Utilizar temporizadores TON y contactos de finalización `DN`.
-   Coordinar etapas mediante marcas internas.
-   Evitar órdenes simultáneas de avance y reversa.
-   Diagnosticar transiciones que no se ejecutan o temporizadores que no
    se reinician.

## Pruebas recomendadas

-   Confirmar que Forward active `M1` y `OUT0`.
-   Pulsar Backward y verificar que ambas salidas queden apagadas
    durante 5 segundos.
-   Comprobar que, al finalizar `T4:2`, se active `M3` y la salida de
    reversa.
-   Confirmar que el giro inverso dure 10 segundos.
-   Verificar que, al finalizar `T4:3`, las salidas se apaguen y
    comience la espera final de 5 segundos.
-   Confirmar que, al finalizar `T4:4`, el motor permanezca detenido y
    `OUT0` no se reactive.

## Buenas prácticas y diagnóstico

-   Comprueba la base de tiempo y los presets: 5, 10 y 5 segundos.
-   Habilita cada TON con la etapa correcta y verifica que se reinicie
    al desactivarse esa etapa.
-   Asegúrate de que `OUT0` y `OUT1` nunca se activen simultáneamente.
-   Evita asignar una misma salida física desde varios rungs sin una
    estrategia clara.
-   Verifica el mapeo real de entradas/salidas antes de conectar
    dispositivos físicos.

## Seguridad

Este documento describe una práctica educativa de simulación. En un
sistema real, la inversión de giro requiere contactores con
enclavamiento mecánico y eléctrico, protecciones adecuadas y una
evaluación de riesgos. Este ejemplo no sustituye un diseño de seguridad
validado.

## Tecnologías y conceptos

Automation Studio · Ladder Logic · Motor trifásico · Inversión de giro ·
Temporizadores TON · Secuenciación · Diagnóstico industrial

## Autor

Proyecto de práctica personal para desarrollar habilidades en
automatización industrial.
