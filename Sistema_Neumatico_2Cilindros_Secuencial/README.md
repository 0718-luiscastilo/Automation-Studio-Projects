# Secuencia electro-neumática de dos cilindros con temporización en Automation Studio

## Nombre del proyecto

**Control secuencial de dos cilindros neumáticos con temporizador de 10
segundos**

## Descripción

Práctica de automatización industrial que simula una secuencia de dos
cilindros controlados mediante lógica tipo Ladder. El objetivo es
coordinar el avance y el retroceso de los cilindros, validar finales de
carrera y mantener una pausa temporizada.

## Secuencia de funcionamiento

1.  Al presionar **START**, el cilindro 1 avanza.
2.  Cuando **S1** confirma que el cilindro 1 llegó al extremo extendido,
    se habilita el avance del cilindro 2.
3.  Cuando **S2** detecta el cilindro 2 extendido, comienza el
    temporizador de **10 segundos**.
4.  Al terminar el temporizador, se desenergiza la bobina de la válvula
    del cilindro 2 y este regresa por acción del resorte de la válvula
    monoestable.
5.  Cuando **S3** confirma que el cilindro 2 está retraído, se
    desenergiza la bobina del cilindro 1 y este regresa.
6.  **S4** confirma que el cilindro 1 volvió a su posición inicial.

> Verifica la asignación exacta de entradas, salidas y bits internos en
> tu archivo de Automation Studio. Los nombres S1--S4 se describen según
> la función prevista en esta secuencia.

## Componentes principales

-   Dos cilindros neumáticos de doble efecto.
-   Dos válvulas direccionales monoestables con retorno por resorte,
    según el esquema.
-   Sensores de posición para las posiciones retraída y extendida.
-   Pulsador START.
-   Entradas y salidas digitales.
-   Temporizador TON ajustado a 10 segundos.
-   Bits internos para representar las etapas de la secuencia.

## Objetivos de aprendizaje

-   Diseñar una secuencia secuencial de actuadores.
-   Utilizar sensores de posición como condiciones de transición.
-   Aplicar un temporizador TON.
-   Separar las etapas del proceso de las órdenes físicas de salida.
-   Diagnosticar señales activas al inicio del ciclo y evitar
    transiciones prematuras.

## Puntos de diagnóstico

-   Confirmar que cada sensor está conectado a la entrada digital
    correcta.
-   Comprobar el estado inicial de S3 y S4 antes de arrancar.
-   Evitar que un sensor activo desde el inicio habilite una etapa fuera
    de contexto.
-   Usar la condición de etapa junto con el sensor para validar cada
    transición.
-   Revisar la base de tiempo, el preset y el bit DN del temporizador.
-   Confirmar la lógica real de las válvulas: en una válvula
    monoestable, desenergizar la bobina permite que el resorte devuelva
    la válvula, siempre que el símbolo y la conexión neumática
    correspondan.
-   Probar en simulación y observar entradas, bits internos y salidas
    durante cada transición.

## Mejoras futuras

-   Incorporar un pulsador STOP y definir el comportamiento de parada.
-   Añadir una condición de ciclo completo y rearme.
-   Añadir detección de timeout si un cilindro no llega al sensor
    esperado.
-   Incorporar enclavamientos para evitar órdenes incompatibles.
-   Documentar el mapeo de entradas/salidas y capturas de cada etapa.

## Seguridad y alcance

Este es un ejercicio educativo de simulación. Antes de aplicar una
lógica similar a maquinaria real, debe realizarse una evaluación de
riesgos e implementarse el circuito de seguridad apropiado. Este ejemplo
no sustituye funciones de seguridad certificadas.

## Tecnologías y conceptos

-   Automation Studio
-   Ladder Logic
-   Neumática
-   Sensores digitales
-   Temporizador TON
-   Secuenciación de actuadores
-   Diagnóstico de automatización industrial

## Autor

Proyecto de práctica personal para desarrollar habilidades en
automatización industrial.
