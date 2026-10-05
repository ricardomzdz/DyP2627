# EJEMPLO PRÁCTICO 0: Clasificador Manual y Contador de Naranjas y Limones

## Planteamiento de Ingeniería
Se dispone de una cesta origen que contiene una mezcla de frutas (naranjas y limones). Un operario debe realizar un proceso iterativo de clasificación manual mientras queden frutas en la cesta principal. El proceso consiste en tomar una fruta, identificar su tipo y depositarla en su contenedor correspondiente: las naranjas en la caja de la izquierda y los limones en la caja de la derecha. Además, el sistema debe llevar un registro continuo mediante contadores para contabilizar el número total de naranjas, limones y frutas procesadas.

* **Entradas:** `hay_frutas` (Booleano: VERDADERO / FALSO), `tipo_fruta` (Texto: "Naranja", "Limón").
* **Proceso:** Mientras `hay_frutas` sea VERDADERO, extraer una fruta, evaluar `tipo_fruta`. Si es "Naranja", incrementa `total_naranjas` y deposita a la izquierda; si es "Limón", incrementa `total_limones` y deposita a la derecha. Tras cada iteración, actualizar el acumulador total `total_frutas = total_naranjas + total_limones` e inspeccionar nuevamente la cesta.
* **Salidas:** Colocación física de las frutas en sus respectivas cajas y el reporte del recuento final (`total_naranjas`, `total_limones`, `total_frutas`).

---

## Diagrama de Flujo

![Diagrama de Flujo - Clasificador Manual y Contador de Naranjas y Limones](./img/Ejemplo%20pr%C3%A1ctico%202.jpg)

### Explicación del Diagrama de Flujo Paso a Paso
El diagrama de flujo describe un algoritmo iterativo combinado con una estructura de decisión condicional:

1. **Inicio e Inicialización de Variables:**
   * El algoritmo da comienzo en el nodo INICIO.
   * Se realiza la lectura de las variables principales de entrada: `color` y `diámetro`.
2. **Evaluación de Control de Calidad (Bolas Defectuosas):**
   * Se evalúa si el diámetro es menor a 30 mm o si el color es desconocido.
   * **SÍ:** Se activa el pistón de descarte para apartar la bola defectuosa y finaliza esa unidad.
   * **NO:** La bola es válida y pasa a la clasificación por color.
3. **Bifurcación Condicional (Clasificación por Color):**
   * **¿Color Rojo?** $\rightarrow$ **SÍ:** Activa el desviador rojo.
   * **¿Color Verde?** $\rightarrow$ **SÍ:** Activa el desviador verde.
   * **En caso contrario (Azul):** Activa el desviador azul.
4. **Finalización:**
   * Todas las ramas convergen en el nodo FIN tras activar el actuador correspondiente.

---

## Pseudocódigo Formal

```text
ALGORITMO ClasificadorBolas
    VAR
        TEXTO: color
        ENTERO: diametro
    FIN_VAR

    INICIO
        ESCRIBIR "Leyendo sensores de la cinta transportadora..."
        LEER color, diametro

        SI diametro < 30 O color == "desconocido" ENTONCES
            ESCRIBIR "Bola defectuosa detectada. Activando Pistón de Descarte."
        SINO
            SI color == "rojo" ENTONCES
                ESCRIBIR "Bola roja identificada. Activando Desviador Rojo."
            SINO_SI color == "verde" ENTONCES
                ESCRIBIR "Bola verde identificada. Activando Desviador Verde."
            SINO
                ESCRIBIR "Bola azul identificada. Activando Desviador Azul."
            FIN_SI
        FIN_SI
    FIN
FIN_ALGORITMO
