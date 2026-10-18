# Módulo 1.2: Apuntes de Programación y Pseudocódigo
## Digitalización y Programación - 2.º de Bachillerato

Este documento contiene la guía completa de teoría y casos prácticos de programación mediante pseudocódigo, diseñada para asimilar los fundamentos de la programación estructurada y la transición desde los diagramas de flujo.

---

## 1. Introducción al Pseudocódigo

El **pseudocódigo** es un lenguaje intermedio entre el lenguaje humano (natural) y un lenguaje de programación formal (como Python, C++ o Java). A diferencia de los **diagramas de flujo**, que utilizan bloques gráficos y flechas para representar el flujo de control, el pseudocódigo utiliza palabras clave estructuradas y sangrado (indentación) para reflejar la lógica del programa de forma legible y precisa.

---

## 2. Clasificación de Instrucciones Básicas

### A. Asignación y Declaración de Variables
Sirven para declarar el tipo de dato de una variable e inicializar o modificar su valor almacenado.
* **Declaración:** `Definir <variable> Como <TipoDato>` (ej. `Entero`, `Real`, `Cadena`, `Logico`).
* **Asignación:** `<variable> <- <expresión>` o `<variable> = <expresión>`.

```pseudocode
Definir contador Como Entero  
contador <- 0
```

### B. Instrucciones de Entrada y Salida (I/O)
Permiten la interacción entre el usuario o el entorno (sensores) y el programa.
* **Entrada (`Leer`):** Solicita un dato al usuario o lee la señal de un sensor y lo guarda en una variable.
* **Salida (`Escribir` / `Mostrar`):** Muestra un texto, el valor de una variable o el resultado de un cálculo en pantalla o actuador.

```pseudocode
Escribir "Ingrese su edad:"  
Leer edad
```

### C. Estructuras de Control Condicionales (Toma de Decisiones)
Permiten ejecutar ciertos bloques de código según se cumpla o no una condición lógica.

#### 1. Condicional Simple (`Si ... Entonces`)
Ejecuta un bloque solo si la condición es verdadera.
```pseudocode
Si temperatura > 30 Entonces  
    Escribir "Alarma: Sobrecalentamiento"  
FinSi
```

#### 2. Condicional Doble (`Si ... Entonces ... Sino`)
Ofrece una alternativa si la condición resulta ser falsa.
```pseudocode
Si edad >= 18 Entonces  
    Escribir "Acceso permitido"  
Sino  
    Escribir "Acceso denegado"  
FinSi
```

#### 3. Condicional Anidado o Múltiple
Combina varias condiciones de forma consecutiva o dentro de otras condiciones.
```pseudocode
Si nota >= 9 Entonces  
    Escribir "Sobresaliente"  
Sino  
    Si nota >= 5 Entonces  
        Escribir "Aprobado"  
    Sino  
        Escribir "Suspenso"  
    FinSi  
FinSi
```

---

## 3. Operadores Lógicos y Tablas de Verdad

Los **operadores lógicos** (o booleanos) permiten combinar o modificar expresiones condicionales simples para evaluar condiciones compuestas. Evalúan valores de verdad (`Verdadero` o `Falso`).

### A. Operador Lógico "Y" (AND / Conjunción)
Devuelve `Verdadero` únicamente cuando **todas** las condiciones evaluadas son verdaderas. Si al menos una es falsa, el resultado global es `Falso`.

| Condición A | Condición B | A Y B |
| :--- | :--- | :--- |
| Falso | Falso | Falso |
| Falso | Verdadero | Falso |
| Verdadero | Falso | Falso |
| Verdadero | Verdadero | Verdadero |

```pseudocode
Si altura_cm >= 140 Y edad >= 12 Entonces  
    Escribir "Acceso Autorizado: Individual"  
FinSi
```

### B. Operador Lógico "O" (OR / Disyunción)
Devuelve `Verdadero` si al menos **una** de las condiciones evaluadas es verdadera. Solo devuelve `Falso` cuando todas las condiciones son falsas.

| Condición A | Condición B | A O B |
| :--- | :--- | :--- |
| Falso | Falso | Falso |
| Falso | Verdadero | Verdadero |
| Verdadero | Falso | Verdadero |
| Verdadero | Verdadero | Verdadero |

```pseudocode
Si diametro < 30 O color == "Desconocido" Entonces  
    Escribir "Producto defectuoso: Descartar"  
FinSi
```

### C. Operador Lógico "NO" (NOT / Negación)
Invierte el valor de verdad de la expresión a la que se aplica: transforma `Verdadero` en `Falso` y viceversa.

| Condición A | NO A |
| :--- | :--- |
| Falso | Verdadero |
| Verdadero | Falso |

```pseudocode
Mientras NO acertado Hacer  
    Escribir "Siga intentándolo..."  
FinMientras
```

---

## 4. Ampliación de Estructuras Iterativas (Bucles)

Los bucles permiten repetir la ejecución de un bloque de código mientras se cumpla una condición o durante un número determinado de veces. Según cómo y cuándo se evalúa la condición de parada, distinguimos tres tipos principales:

### A. Bucle Precondición (`Mientras ... Hacer`)
* **Funcionamiento:** La condición se evalúa antes de entrar al bucle. Si la condición resulta ser falsa desde el principio, el bloque interno no se ejecuta ninguna vez.
* **Uso recomendado:** Cuando no sabemos de antemano cuántas veces se repetirá el proceso y es posible que no deba ejecutarse si no se cumple el estado inicial.

```pseudocode
Mientras hayFrutasEnCesta == Verdadero Hacer  
    Leer tipoFruta  
    // Proceso de clasificación...  
FinMientras
```

### B. Bucle Postcondición (`Repetir ... Hasta Que`)
* **Funcionamiento:** La condición de salida se evalúa al final del bloque. Esto garantiza que el conjunto de instrucciones interno se ejecute al menos una vez.
* **Uso recomendado:** Cuando es obligatorio realizar una acción previa antes de poder validar el resultado (por ejemplo, solicitar una clave de acceso o mostrar un menú de opciones).

```pseudocode
Repetir  
    Escribir "Ingrese un número mayor que cero:"  
    Leer numero  
Hasta Que numero > 0
```

### C. Bucle Determinado (`Para ... Hasta ... Con Paso ... Hacer`)
* **Funcionamiento:** Utiliza una variable de control (habitualmente llamada `i`, `j`, `k`) que se inicializa, se incrementa automáticamente en cada vuelta según el paso indicado y finaliza al alcanzar un límite preestablecido.
* **Uso recomendado:** Cuando se conoce con exactitud el número de iteraciones antes de iniciar la ejecución del bucle.

```pseudocode
Para i <- 1 Hasta 5 Con Paso 1 Hacer  
    Escribir "Atendiendo al visitante número: ", i  
FinPara
```

---

## 5. Herramientas de Control: Contadores y Acumuladores

### A. Los Contadores
Un contador es una variable de tipo entero que se incrementa o decrementa en una cantidad constante (habitualmente de 1 en 1) cada vez que ocurre un evento específico.
* **Fórmula general:** `contador <- contador + 1`
* **Requisito crítico:** Debe inicializarse (normalmente a `0`) antes de entrar al bucle.

```pseudocode
Definir totalNaranjas Como Entero  
totalNaranjas <- 0 // Inicialización obligatoria  
  
Mientras hayFruta Hacer  
    Si fruta == "Naranja" Entonces  
        totalNaranjas <- totalNaranjas + 1  
    FinSi  
FinMientras
```

### B. Los Acumuladores
Un acumulador (o sumador) es una variable numérica que suma valores variables a lo largo de las ejecuciones del bucle.
* **Fórmula general:** `acumulador <- acumulador + variable`
* **Requisito crítico:** Debe inicializarse (normalmente a `0`) antes de entrar al bucle.

```pseudocode
Definir sumaPares Como Entero  
sumaPares <- 0 // Inicialización obligatoria  
  
Mientras hayNumeros Hacer  
    Leer numero  
    Si numero % 2 == 0 Entonces  
        sumaPares <- sumaPares + numero  
    FinSi  
FinMientras
```

---

## 6. Fundamentos de Metodología de Programación

### A. La Programación Estructurada
La Programación Estructurada es un paradigma que promueve la creación de códigos claros, legibles y fáciles de mantener. Se basa en el Teorema de la Estructura, el cual demuestra que cualquier algoritmo puede expresarse combinando únicamente tres estructuras lógicas fundamentales:
1. **Secuencia:** Ejecución de instrucciones una tras otra, en orden descendente.
2. **Selección:** Toma de decisiones condicionales (`Si ... Sino`).
3. **Iteración:** Bucles y repetición de instrucciones (`Mientras`, `Para`, `Repetir`).

> **Regla de oro:** Todo bloque o subprograma estructurado debe tener un único punto de entrada y un único punto de salida.

### B. Importancia de la Tabulación e Indentación
La indentación (o tabulación) consiste en desplazar hacia la derecha el texto de las líneas de código que se encuentran dentro de una estructura de control.
* **Claridad visual:** Permite identificar a simple vista dónde empieza y termina un bucle o condicional.
* **Prevención de errores:** Evita confundir qué instrucciones dependen de qué condición.
* **Sintaxis en lenguajes reales:** En lenguajes como Python, la indentación define la propia estructura sintáctica del programa.

### C. La Técnica del "Divide y Vencerás" (Divide and Conquer)
El enfoque Divide y Vencerás es una estrategia metodológica clave en la resolución de problemas complejos:
1. **Dividir:** Tomar un problema complejo y desglosarlo en subproblemas más sencillos e independientes.
2. **Vencer:** Resolver cada subproblema de forma individual.
3. **Combinar:** Unir las soluciones para obtener el resultado global.

En programación, esta técnica se concreta mediante la **Modularización** (subprocesos, funciones o procedimientos).

---

## 7. Ejemplos Prácticos Resueltos

### A. Enunciados de los Retos Prácticos

* **Ejemplo 1: Clasificación Manual de Fruta (Cesta Origen)**  
  Un operario clasifica naranjas y limones de una cesta origen. Deposita las naranjas a la izquierda y los limones a la derecha, contabilizando el total de cada tipo y el total procesado.
* **Ejemplo 2: Control de Calidad e Inspección en Cinta Transportadora**  
  Una cinta industrial mide el diámetro y color de bolas de plástico. Si mide menos de 30 mm o el color es "Desconocido", se descarta. Si es correcta, se desvía a la caja correspondiente (Rojo, Verde, Azul).
* **Ejemplo 3: Contador y Acumulador de Números Pares**  
  Lee números introducidos por teclado y calcula cuántos son pares y su suma acumulada hasta que se introduce "No".
* **Ejemplo 4: Máquina Dispensadora Automática de Bebidas Calientes**  
  Simula la preparación de bebidas validando existencias de vasos, azúcar y leche.
* **Ejemplo 5: Control de Acceso a Montaña Rusa (Cola de 5 Visitantes)**  
  Controla el acceso según edad y altura para una cola de 5 personas.
* **Ejemplo 6: Juego "Adivina el Número" (Límite Máximo de Intentos)**  
  Adivinar un número secreto en un máximo de 3 intentos con pistas de mayor/menor.

---

