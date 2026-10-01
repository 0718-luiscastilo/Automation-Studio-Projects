# Práctica de Automatización Industrial – Banda Transportadora

## Descripción
Práctica de nivel básico desarrollada en **Automation Studio** para simular el control de una banda transportadora con arranque, paro, enclavamiento, sensor de pieza, lámpara indicadora y protección del motor.

## Objetivo
Practicar:
- Entradas y salidas digitales
- Contactos NO y NC
- Enclavamiento eléctrico
- Sensores industriales
- Control de motores
- Señalización
- GRAFCET
- Troubleshooting básico

## Componentes

### Entradas
| Elemento | Descripción |
|---|---|
| START | Pulsador de arranque, NO |
| STOP | Pulsador de paro, NC |
| S1 | Sensor fotoeléctrico de pieza |

### Salidas
| Elemento | Descripción |
|---|---|
| K1 | Relé/contactor de mando |
| M1 | Motor de la banda |
| H1 | Lámpara indicadora |

### Protección
| Elemento | Descripción |
|---|---|
| OL | Contacto auxiliar del relé de sobrecarga |

## Secuencia de funcionamiento
1. El sistema inicia detenido.
2. Al presionar **START**, se energiza K1.
3. El contacto auxiliar de K1 mantiene el circuito enclavado.
4. El motor M1 permanece funcionando aunque se libere START.
5. Al presionar **STOP**, K1 se desenergiza y el motor se detiene.
6. Cuando S1 detecta una pieza, H1 se enciende.
7. Cuando la pieza deja de ser detectada, H1 se apaga.
8. Si actúa OL, el circuito debe impedir que el motor continúe funcionando.

## GRAFCET
- **Etapa 0:** Sistema detenido. M1=0, H1=0.
- **Transición:** START=1.
- **Etapa 1:** Banda funcionando. K1=1, M1=1.
- **Transición:** S1=1.
- **Etapa 2:** Pieza detectada. M1=1, H1=1.
- **Transición:** S1=0.
- **Retorno:** Regresa a la etapa de banda funcionando.
- **Paro:** STOP → K1=0 → M1=0 → H1=0.

## Lógica simplificada

```text
START ──┐
        ├── K1 ── OL ── M1
K1 NO ──┘

S1 ─────────────────── H1

STOP ──► K1 OFF ──► M1 OFF
```

## Retos posteriores
- Temporizador TON
- Contador CTU de piezas
- Paro automático después de cierta cantidad
- Selector MANUAL/AUTOMÁTICO
- Indicador de falla
- Sensor adicional
- Secuencia automática de clasificación
- Integración con PLC
- Simulación con Factory I/O

## Software
**Automation Studio**

## Nivel
**Nivel 1 – Básico**

## Tipo de práctica
**Automatización industrial / Control eléctrico / Banda transportadora**

## Autor
Proyecto de práctica personal de Automatización Industrial.

## Nota
Proyecto educativo y de simulación. Una implementación industrial real debe considerar evaluación de riesgos, normativa aplicable y arquitectura de seguridad de la máquina.
