# Post #2: Representación de Grafos

**Fecha:** Diciembre 3, 2025  
**Categoría:** Estructuras de Datos - Grafos  
**Nivel:** Intermedio  
**Tiempo de lectura:** 10 minutos

---

## 📚 Contenido

### Introducción

Cuando trabajamos con grafos en un programa, necesitamos almacenarlos en la memoria de la computadora de una manera que sea eficiente. Existen **dos métodos principales** para representar un grafo:

1. **Lista de Adyacencia** - Eficiente en espacio
2. **Matriz de Adyacencia** - Eficiente en tiempo

La elección entre una u otra depende de las características del grafo y las operaciones que necesitemos realizar.

---

## 🔗 1. Lista de Adyacencia

### Concepto

Una **lista de adyacencia** es una estructura donde cada nodo tiene asociada una lista de sus nodos adyacentes (vecinos). Se representa típicamente como:
- Un diccionario/mapa donde la clave es el nodo y el valor es una lista de sus vecinos
- Una matriz de listas (array of lists)

### Ventajas

✅ **Eficiencia de espacio:** Para grafos dispersos (con pocas aristas), es mucho más compacta  
✅ **Iteración eficiente:** Fácil recorrer solo los vecinos de un nodo  
✅ **Flexibilidad:** Fácil agregar o remover nodos

### Desventajas

❌ **Consulta de aristas:** Verificar si existe una arista entre dos nodos requiere búsqueda en la lista  
❌ **No ideal para grafos densos:** Si hay muchas aristas, consume más memoria

### Complejidad Espacial

```
Espacio = O(V + E)
Donde V = número de vértices, E = número de aristas
```

### Ejemplo: Lista de Adyacencia

Para el siguiente grafo:

```
    A --- B
    |     |
    C --- D
```

**Representación en código (Python):**

```python
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D'],
    'C': ['A', 'D'],
    'D': ['B', 'C']
}
```

**Representación en código (JavaScript):**

```javascript
const grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D'],
    'C': ['A', 'D'],
    'D': ['B', 'C']
};
```

**Representación alternativa usando Array de Listas:**

```
Nodo 0: [1, 2]
Nodo 1: [0, 3]
Nodo 2: [0, 3]
Nodo 3: [1, 2]
```

### Casos de Uso

- Redes sociales (grafo disperso de usuarios)
- Sistemas de recomendación
- Grafos con muchos nodos pero pocas conexiones

---

## 📋 2. Matriz de Adyacencia

### Concepto

Una **matriz de adyacencia** es una matriz cuadrada M de tamaño V×V (donde V es el número de vértices). Cada celda M[i][j] contiene:
- **1 (o true)** si existe una arista entre el nodo i y el nodo j
- **0 (o false)** si no existe arista
- **Peso de la arista** si el grafo es ponderado

### Ventajas

✅ **Consulta O(1):** Verificar si existe una arista es instantáneo  
✅ **Simétrica para grafos no dirigidos:** M[i][j] = M[j][i]  
✅ **Fácil de implementar:** Estructura simple y directa

### Desventajas

❌ **Ineficiente en espacio:** Para grafos dispersos, desperdicia mucha memoria  
❌ **Iteración ineficiente:** Para listar vecinos, hay que recorrer toda la fila  
❌ **No escalable:** Para grafos enormes, requiere memoria prohibitiva

### Complejidad Espacial

```
Espacio = O(V²)
Siempre, independientemente del número de aristas
```

### Ejemplo: Matriz de Adyacencia

Para el mismo grafo anterior:

```
    A --- B
    |     |
    C --- D
```

**Representación como matriz:**

```
     A  B  C  D
A  [ 0  1  1  0 ]
B  [ 1  0  0  1 ]
C  [ 1  0  0  1 ]
D  [ 0  1  1  0 ]
```

**Interpretación:**
- M[0][1] = 1 → Existe arista entre A y B
- M[0][3] = 0 → No existe arista entre A y D
- M[2][3] = 1 → Existe arista entre C y D

**Representación en código (Python):**

```python
grafo = [
    [0, 1, 1, 0],  # A
    [1, 0, 0, 1],  # B
    [1, 0, 0, 1],  # C
    [0, 1, 1, 0]   # D
]
```

**Representación en código (JavaScript):**

```javascript
const grafo = [
    [0, 1, 1, 0],  // A
    [1, 0, 0, 1],  // B
    [1, 0, 0, 1],  // C
    [0, 1, 1, 0]   // D
];
```

### Ejemplo con Grafo Ponderado

Para un grafo con pesos en las aristas:

```
    A --5-- B
    |       |
   2|       |3
    |       |
    C ---1--D
```

**Matriz de Adyacencia Ponderada:**

```
     A  B  C  D
A  [ 0  5  2  0 ]
B  [ 5  0  0  3 ]
C  [ 2  0  0  1 ]
D  [ 0  3  1  0 ]
```

### Casos de Uso

- Procesamiento de imágenes (píxeles como nodos)
- Problemas de optimización donde se necesita consulta rápida
- Grafos completamente densos

---

## 🔄 Comparación Lado a Lado

### Mismo Grafo con Ambas Representaciones

**Grafo No Dirigido:**

```
    E --- B --- D
    |     |     |
    A --- C ----+
```

### Lista de Adyacencia

```python
grafo_lista = {
    'A': ['E', 'C'],
    'B': ['E', 'C', 'D'],
    'C': ['A', 'B', 'D'],
    'D': ['B', 'C'],
    'E': ['A', 'B']
}
```

### Matriz de Adyacencia

```
     A  B  C  D  E
A  [ 0  0  1  0  1 ]
B  [ 0  0  1  1  1 ]
C  [ 1  1  0  1  0 ]
D  [ 0  1  1  0  0 ]
E  [ 1  1  0  0  0 ]
```

---

## 📊 Tabla Comparativa

| Aspecto | Lista de Adyacencia | Matriz de Adyacencia |
|--------|-------------------|------------------|
| **Espacio** | O(V + E) | O(V²) |
| **Consultar arista** | O(grado del vértice) | O(1) |
| **Listar vecinos** | O(grado) | O(V) |
| **Agregar arista** | O(1) | O(1) |
| **Remover arista** | O(grado) | O(1) |
| **Mejor para grafos dispersos** | ✅ Sí | ❌ No |
| **Mejor para grafos densos** | ❌ No | ✅ Sí |

---

## 💡 ¿Cuál Usar?

### Usa **Lista de Adyacencia** si:
- El grafo es **disperso** (pocas aristas respecto a nodos potenciales)
- Necesitas iterar frecuentemente sobre los vecinos
- El número de nodos es muy grande
- La memoria es limitada

### Usa **Matriz de Adyacencia** si:
- El grafo es **denso** (muchas aristas)
- Necesitas verificar frecuentemente si una arista existe
- El tamaño del grafo es pequeño a mediano
- La velocidad de consulta es más importante que la memoria

---

## ✅ Puntos Clave a Recordar

1. La **lista de adyacencia** es compacta pero requiere búsqueda para verificar aristas
2. La **matriz de adyacencia** permite consultas O(1) pero consume mucha memoria
3. Grafos **dispersos** → usa lista de adyacencia
4. Grafos **densos** → usa matriz de adyacencia
5. La elección afecta la eficiencia general del algoritmo

---

## 📌 Próximas Lecturas

- **Post #3:** Algoritmos Fundamentales de Recorrido (BFS y DFS)

---

**¿Preguntas o comentarios?** Déjalos en la sección de comentarios o contacta al equipo técnico.
