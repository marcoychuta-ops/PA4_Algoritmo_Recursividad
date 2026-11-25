# PA4_Algoritmo_Recursividad
## Objetivo del proyecto
Proponer y desarrollar una solución algorítmica para un **módulo inteligente de orientación dentro del campus**, integrando recursividad, ordenamiento recursivo y grafos (DFS, BFS y A*) para organizar información del campus, analizar rutas y justificar decisiones técnicas.

## Integrantes y organización del equipo
- **[Joseph Antonio Fong Millones]:** Actividad 1 – Recursividad aplicada (`ZonaCampus.java` y `Recursividad.java`).
- **[Integrante 2]:** Actividad 2 – Ordenamiento recursivo.
- **[Integrante 3]:** Actividad 3 – Modelado con grafos (DFS, BFS y A*).
- **[Integrante 4]:** Actividad 4 – Argumentación final, relación con IA, informe PDF y video.

## Resumen del trabajo: Actividad 1 – Recursividad aplicada

### Enfoque y relación con *Divide y vencerás*
La recursividad consiste en que una función se llame a sí misma sobre instancias más pequeñas hasta llegar a un caso base. En el contexto del módulo de orientación, se articula con *Divide y vencerás* para descomponer la estructura jerárquica del campus (**Campus → Pabellones → Pisos/Áreas → Aulas o Laboratorios**) en subzonas más pequeñas, resolver el cálculo en cada nivel y combinar los resultados obtenidos.

### ¿Qué resuelve el algoritmo implementado?
En `ZonaCampus.java` y `Recursividad.java` (paquete `pa4_algoritmo`) se implementa `contarEspaciosAccesibles(zona)`, un algoritmo recursivo que recorre la jerarquía de zonas del campus para contar cuántos ambientes **accesibles** (aptos para movilidad reducida) y **disponibles** existen a partir de una zona dada:
- **Caso base:** Cuando una zona no tiene subzonas (`subzonas` vacía), representa un ambiente terminal (como un aula o laboratorio) y devuelve `1` si es accesible y está disponible, o `0` en caso contrario (y `0` si la zona es nula).
- **Caso recursivo:** Cuando una zona contiene subzonas, invoca `contarEspaciosAccesibles(sub)` en cada subzona y acumula los resultados parciales en un total.
- **Condición de finalización:** Al tratarse de una jerarquía finita y sin ciclos, cada llamada desciende un nivel hasta alcanzar nodos terminales (sin subzonas), garantizando que el proceso termine en un número finito de pasos.

## Resumen del trabajo: Actividad 2 – Ordenamiento Recursivo

2.1. Planteen un algoritmo recursivo de ordenamiento aplicable a un conjunto de datos del caso.
Se propone utilizar el algoritmo Merge Sort, que permite ordenar un conjunto de datos de menor a mayor mediante la técnica Divide y Vencerás.
Para desarrollar el ejercicio utilizaremos el siguiente conjunto de números:
[38, 12, 45, 8, 23, 16, 50, 4]
El algoritmo funciona mediante dos condiciones fundamentales:
•	Caso base: cuando la lista contiene uno o ningún elemento, se considera que ya está ordenada.
•	Caso recursivo: la función se llama a sí misma para dividir el conjunto de datos en grupos más pequeños hasta llegar al caso base.



2.2 Describan paso a paso cómo se divide el problema y cómo se obtiene el resultado final.
El algoritmo Merge Sort desarrolla el proceso mediante las siguientes etapas:
Paso 1. División del conjunto: Se recibe la lista original y se divide en dos grupos:
•	Grupo 1: [38, 12, 45, 8]
•	Grupo 2: [23, 16, 50, 4]
Paso 2. Subdivisión: Cada grupo vuelve a dividirse en partes más pequeñas hasta obtener listas con un solo elemento.
[38] [12] [45] [8] [23] [16] [50] [4]
Paso 3. Caso base: Cuando cada grupo contiene un solo elemento, se detiene la división porque cada elemento individual ya está ordenado.
Paso 4. Combinación: Se comparan los números y se unen de menor a mayor, formando nuevos grupos ordenados.
Por ejemplo:
•	[38] + [12] = [12, 38]
•	[45] + [8] = [8, 45]
•	[23] + [16] = [16, 23]
•	[50] + [4] = [4, 50]

Paso 5. Resultado final: Se combinan los grupos ordenados hasta obtener una sola lista:
•	Resultado del ordenamiento
•	[4,8,12,16,23,38,45,50]
•	Datos ordenados de menor a mayor.


2.3. Mencionen por qué el enfoque recursivo puede ser útil en este contexto.
El enfoque recursivo es útil porque permite resolver problemas complejos dividiéndolos en subproblemas más pequeños y fáciles de procesar.
En este caso, Merge Sort facilita el ordenamiento de grandes cantidades de datos sin tener que procesar todos los elementos directamente en una sola operación.
Además, utiliza el principio Divide y Vencerás, que permite organizar el proceso de manera estructurada y presenta una complejidad temporal de \(O(n\log n)\).
Por lo tanto, este enfoque resulta conveniente para trabajar con grandes conjuntos de información, facilitando su organización, procesamiento y análisis.



### 01. DEFINIR LOS DATOS
numeros = [38, 12, 45, 8, 23, 16, 50, 4]

# 02. ALGORITMO RECURSIVO MERGE SORT

def merge_sort(lista):

    # Caso base
    if len(lista) <= 1:
        return lista

    # Dividir el conjunto
    medio = len(lista) // 2

    izquierda = lista[:medio]
    derecha = lista[medio:]

    # Llamadas recursivas
    izquierda = merge_sort(izquierda)
    derecha = merge_sort(derecha)

    # Combinar los resultados
    return combinar(izquierda, derecha)

# 03. COMBINAR LAS LISTAS

def combinar(izquierda, derecha):

    resultado = []
    i = 0
    j = 0
    while i < len(izquierda) and j < len(derecha):
        if izquierda[i] <= derecha[j]:
            resultado.append(izquierda[i])
            i += 1
        else:
            resultado.append(derecha[j])
            j += 1
    resultado.extend(izquierda[i:])
    resultado.extend(derecha[j:])
    return resultado

# 04. EJECUTAR EL ALGORITMO
resultado = merge_sort(numeros)

# 05. MOSTRAR RESULTADOS

print("Lista original:", numeros)
print("Lista ordenada:", resultado)

<img width="1146" height="181" alt="image" src="https://github.com/user-attachments/assets/f2a9d765-de04-4d1a-8886-9fdc76d613b0" />









## Siguientes secciones por completar en equipo
- **Actividad 2 (Ordenamiento recursivo):** [Resumen del algoritmo y criterio de ordenamiento].
- **Actividad 3 (Grafos – DFS, BFS y A*):** [Resumen del grafo, nodos, aristas y comparación de recorridos].
- **Actividad 4 (Conclusión e IA):** [Justificación técnica y vínculo con IA].
- **Video de exposición (YouTube):** [Enlace al video con cámaras encendidas]
