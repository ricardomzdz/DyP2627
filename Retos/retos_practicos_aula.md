# 3. Propuestas de Retos Prácticos para el Aula (Trabajo por Parejas)

Estas actividades están diseñadas para ejecutarse en parejas utilizando herramientas digitales de diagramación (como Draw.io, Lucidchart o aplicaciones similares).

---

## Reto 1: Contador y Acumulador de Números Pares (Finalización con "No")

**Consigna:** Diseñar el algoritmo que procese una secuencia indeterminada de números enteros introducidos por el usuario y cuente cuántos de ellos son pares. El programa funcionará mediante un bucle centinela: en cada iteración solicitará un número o la palabra `"No"` si se desea terminar. Si el usuario ingresa un número, el sistema evaluará si es par (utilizando la operación módulo `numero % 2 == 0`), incrementará un contador específico y acumulará la suma. El proceso se repetirá continuamente hasta que el usuario responda `"No"`. Al finalizar, el algoritmo deberá mostrar el total de números pares encontrados y la suma acumulada de dichos números.

---

## Reto 2: Verificador de Secuencia Ordenada (Finalización con "No")

**Consigna:** Diseñar el algoritmo que determine si una serie de números introducidos dinámicamente por el usuario se encuentra ordenada de forma estrictamente ascendente (de menor a mayor). El programa solicitará el primer número para iniciar la secuencia y, a continuación, mediante un bucle, irá pidiendo nuevos números uno a uno hasta que el usuario escriba `"No"`. En cada iteración, comparará el valor ingresado con el anterior. Si en algún momento el nuevo número es menor o igual que el previo, el sistema registrará internamente que la secuencia ha perdido el orden. Al ingresar la palabra `"No"`, el algoritmo finalizará e informará si la secuencia introducida estuvo correctamente ordenada o no.

---

## Reto 3: Máquina Dispensadora Automática de Bebidas Calientes

**Consigna:** Diseñar el algoritmo de control para una máquina expendedora de café y chocolate mediante diagrama de flujo. El programa debe realizar las siguientes acciones en orden:

1. Solicitar directamente al usuario que escriba la bebida que desea (`CaféSolo`, `CaféConLeche` o `Chocolate`).
2. Solicitar al usuario el nivel de azúcar deseado (un entero entre 0 y 5).
3. Verificar la disponibilidad de **ingredientes y suministros** en el inventario antes de proceder:
   * Para cualquier bebida, comprobar que haya existencias de `vasos` (> 0).
   * Si la opción elegida es `CaféConLeche`, verificar adicionalmente que exista `leche_disponible` (> 0).
4. Si falta algún **ingrediente o suministro** necesario, mostrar un mensaje de error ("Existencias insuficientes") y cancelar la operación.
5. Si hay stock suficiente, descontar los **ingredientes** correspondientes del inventario (un vaso, la leche si aplica y las dosis de azúcar) y mostrar en pantalla el mensaje de preparación y servido de la bebida.

---

## Reto 4: Control de Acceso a Montaña Rusa con Cola de Espera (5 Visitantes)

**Consigna:** Diseñar el algoritmo completo mediante un diagrama de flujo que regule el acceso a una montaña rusa de alta velocidad procesando exactamente a 5 visitantes en cola mediante un bucle contador (`PARA` / `FOR` de 1 a 5). Por cada visitante se debe pedir su `altura_cm` y su `edad`. La lógica de validación aplicará las siguientes reglas:

* **Acceso Individual:** Si mide al menos 140 cm Y tiene 12 años o más, se autoriza el acceso solo.
* **Acceso Acompañado:** Si mide entre 120 cm y 139 cm (ambos inclusive), se debe preguntar si va acompañado por un adulto (Booleano: SÍ/NO). Si va acompañado, se autoriza el acceso; de lo contrario, se rechaza.
* **Rechazo Automático:** Si mide menos de 120 cm, se rechaza automáticamente sin importar la edad.
* **Control de Cola:** El algoritmo debe emitir el mensaje correspondiente a la decisión (Permitido / Acompañado / Rechazado) e indicar cuántos visitantes quedan pendientes en la cola antes de pasar al siguiente turno.

---

## Reto 5: Juego "Adivina el Número" (Versión por Intentos y Versión por Límite)

**Consigna:** Diseñar la lógica del diagrama de flujo para un juego interactivo donde la computadora guarda un número secreto prefijado entre 1 y 10 (por ejemplo, `numero_secreto = 7`). El usuario debe intentar adivinarlo introduciendo números por teclado. En cada intento, si el usuario no acierta, el programa debe responder indicando si el número ingresado es **MAYOR** o **MENOR** que el número secreto. Se deben plantear dos variantes de resolución:

* **Variante A (Contador de intentos):** El bucle se repite indefinidamente hasta que el jugador acierte. Al lograrlo, se muestra el mensaje "¡Has acertado!" seguido del número total de intentos que necesitó.
* **Variante B (Límite máximo de intentos):** El jugador dispone de un máximo de 3 intentos. Si acierta dentro del límite, se le felicita y se interrumpe el juego. Si agota los 3 intentos sin acertar, el programa finaliza mostrando el mensaje "Has agotado tus intentos. El número era X".

---

## Reto 6: Juego Completo del Ahorcado

**Consigna:** Diseñar la estructura algorítmica para una versión simplificada del clásico juego del Ahorcado. El sistema contendrá una palabra secreta guardada (por ejemplo, "C O D I G O") y establecerá un límite de 6 fallos/vidas. En cada turno del bucle:

1. Se muestra el estado actual de la palabra (letras adivinadas y guiones en las ocultas) y el número de vidas restantes.
2. El jugador ingresa una letra.
3. Se comprueba si la letra está presente en la palabra secreta:
   * Si está presente, se revela en todas sus posiciones correspondientes.
   * Si no está presente, se descuenta una vida (`vidas = vidas - 1`).
4. El juego finaliza si se cumple cualquiera de estas dos condiciones de parada:
   * **Victoria:** El jugador ha descubierto todas las letras de la palabra antes de quedarse sin vidas.
   * **Derrota:** El contador de vidas llega a 0, mostrando el mensaje "¡Juego Terminado! Has sido ahorcado. La palabra era...".
