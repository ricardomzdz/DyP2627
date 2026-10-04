# EJEMPLO PRÁCTICO 1: Clasificador Automático de Bolas de Colores (Visión e Industria)

## Planteamiento de Ingeniería

Una cinta transportadora industrial mueve bolas de plástico. Un sensor de tamaño (diámetro) y un sensor cromático leen cada unidad. Si la bola mide menos de $30\text{ mm}$ o el color es `"Desconocido"`, se considera defectuosa y un pistón la descarta. Si es correcta, se activa el desviador hacia su caja correspondiente (Rojo, Verde, Azul).

* **Entradas:** `color_detectado` (Texto: `"Rojo"`, `"Verde"`, `"Azul"`, `"Desconocido"`), `diametro_mm` (Número entero).
* **Proceso:** Comprobar si $\text{diametro\\_mm} < 30$ o $\text{color\\_detectado} == \text{"Desconocido"}$. Si es defectuosa, activar `Piston_Descarte`. Si es válida, bifurcar según `color_detectado` y activar el desviador adecuado.
* **Salidas:** Activación del actuador adecuado (`Piston_Descarte`, `Desviador_Rojo`, `Desviador_Verde`, `Desviador_Azul`).

---

## Diagrama de Flujo

![Diagrama de Flujo - Clasificador de Bolas](./img/Ejemplo%20pr%C3%A1ctico%202.jpg)

### Explicación del Diagrama de Flujo Paso a Paso

El diagrama de flujo describe el proceso secuencial y de control condicional ejecutado por el sistema de control industrial:

1. **Inicio del Proceso:**
   * El sistema inicia en el nodo `INICIO` cuando la bola alcanza el punto de inspección en la cinta transportadora.

2. **Lectura de Datos de Sensores:**
   * Se capturan los datos mediante el bloque de entrada/salida: **"Leer color y diámetro"**, obteniendo los valores para las variables `color_detectado` y `diametro_mm`.

3. **Control de Calidad (Filtrado de Defectos):**
   * El primer rombo de decisión evalúa la condición lógica: `¿Diámetro < 30 o color desconocido?`.
   * **Rama SÍ (Defectuosa):** Si el diámetro es inferior a $30\text{ mm}$ o el color no puede identificarse, la bola no cumple los estándares. Se deriva al bloque de proceso **"Activar Pistón Descarte"**, enviando la pieza a la bandeja de desecho y finalizando el flujo en `FIN`.
   * **Rama NO (Válida):** Si la bola cumple el tamaño mínimo y tiene un color reconocido, continúa hacia la fase de clasificación.

4. **Bifurcación por Color (Selección de Destino):**
   * **Evaluación 1 (`¿Color rojo?`):**
     * **SÍ:** Se ejecuta **"Activar Desviador Rojo"** para canalizar la bola hacia la caja correspondiente y el programa termina en `FIN`.
     * **NO:** Continúa a la siguiente verificación.
   * **Evaluación 2 (`¿Color verde?`):**
     * **SÍ:** Se ejecuta **"Activar Desviador Verde"** y el programa concluye en `FIN`.
     * **NO:** Dado que la bola ya fue validada como no defectuosa y no es ni roja ni verde, por descartes lógicos corresponde al color azul. Se activa el bloque **"Activar Desviador Azul"** y se dirigi al nodo `FIN`.

---

## Pseudocódigo Formal

```
ALGORITMO ClasificadorBolasColores
    VAR
        TEXTO: color_detectado
        ENTERO: diametro_mm
    FIN_VAR

    INICIO
        ESCRIBIR "Sensor detectando bola..."
        LEER color_detectado, diametro_mm

        SI diametro_mm < 30 O color_detectado == "Desconocido" ENTONCES
            ESCRIBIR "ALERTA: Bola defectuosa. Activando Pistón de Descarte."
        SINO
            SEGUN color_detectado HACER
                "Rojo":
                    ESCRIBIR "Bola Roja correcta. Activando Desviador 1 (Caja Roja)."
                "Verde":
                    ESCRIBIR "Bola Verde correcta. Activando Desviador 2 (Caja Verde)."
                "Azul":
                    ESCRIBIR "Bola Azul correcta. Activando Desviador 3 (Caja Azul)."
                DE OTRO MODO:
                    ESCRIBIR "Error de lectura imprevisto."
            FIN_SEGUN
        FIN_SI
    FIN
FIN_ALGORITMO
```
