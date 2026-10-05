# EJEMPLO PRÁCTICO 4: Sistema Domótico de Climatización y Alarma Anti-Incendios

## Planteamiento de Ingeniería
Microcontrolador de confort y seguridad en una vivienda. La detección de humo anula el sistema de climatización y activa los protocolos de emergencia.

---

## Diagrama de Flujo

![Diagrama de Flujo del Sistema Domótico](Ejemplo%20pr%C3%A1ctico%204.jpg)

### Explicación del Diagrama de Flujo

El diagrama de flujo modela la toma de decisiones del microcontrolador siguiendo una jerarquía clara donde la **seguridad es prioritaria sobre el confort e incremento del ahorro energético**:

1. **Inicio e Inicialización:** 
   * Se da comienzo al proceso y se define la variable `temperatura_confortable = 24`.
2. **Lectura de Sensores:** 
   * Se realiza la lectura de las entradas del sistema: sensores de temperatura, presencia humana y detección de humo.
3. **Prioridad 1 — Evaluación de Seguridad (Detección de Humo):**
   * El primer bloque de decisión evalúa `¿Humo detectado?`.
   * **SÍ:** Se cancela de inmediato la gestión del clima, se activa la `Alarma y apagar clima`, terminando directamente el proceso en `FIN`.
   * **NO:** El sistema procede a evaluar las condiciones de confort y eficiencia energética.
4. **Prioridad 2 — Presencia Humana (Ahorro Energético):**
   * Si no hay humo, se comprueba `¿Hay presencia humana?`.
   * **NO:** La habitación está vacía, por lo que el sistema ejecuta `Apagar climatización` para ahorrar energía y finaliza.
   * **SÍ:** Se pasa a la gestión del clima en función de la temperatura ambiente.
5. **Prioridad 3 — Control de Climatización (Confort):**
   * Se evalúa `¿temperatura > temperatura_confortable?`:
     * **SÍ:** Se ejecuta `Encender aire acondicionado` y finaliza.
     * **NO:** Se evalúa la condición de frío mediante `¿temperatura_C < temperatura_confortable?`:
       * **SÍ:** Se ejecuta `Encender calefacción` y finaliza.
       * **NO:** La temperatura está dentro del rango deseado, por lo que se ajusta a `Clima en reposo` y finaliza.

---

## Pseudocódigo Formal

```algol
ALGORITMO ControlDomotico
    VAR
        BOOLEANO: sensor_humo, presencia_humana
        ENTERO: temperatura_C
    FIN_VAR

    INICIO
        LEER sensor_humo, temperatura_C, presencia_humana

        SI sensor_humo == VERDADERO ENTONCES
            ESCRIBIR "¡EMERGENCIA! Humo detectado. Activando aspersores y sirena."
        SINO
            SI presencia_humana == VERDADERO ENTONCES
                SI temperatura_C > 25 ENTONCES
                    ESCRIBIR "Modo Confort: Encendiendo Aire Acondicionado."
                SINO_SI temperatura_C < 18 ENTONCES
                    ESCRIBIR "Modo Confort: Encendiendo Calefacción."
                SINO
                    ESCRIBIR "Temperatura agradable. Climatizador en espera."
                FIN_SI
            SINO
                ESCRIBIR "Habitación vacía. Climatización apagada por ahorro energético."
            FIN_SI
        FIN_SI
    FIN
FIN_ALGORITMO
```