# Post #3: Algoritmos Fundamentales de Recorrido

**Fecha:** Diciembre 3, 2025  
**Categoría:** Estructuras de Datos - Grafos  
**Nivel:** Intermedio  
**Tiempo de lectura:** 12 minutos

---

## 📚 Contenido

### Introducción

Una de las operaciones más fundamentales en grafos es **recorrer** o **visitar** todos los nodos. Existen dos algoritmos clásicos que permiten esto:

1. **BFS (Breadth-First Search)** - Búsqueda en Amplitud
2. **DFS (Depth-First Search)** - Búsqueda en Profundidad

Ambos algoritmos exploran todos los nodos alcanzables desde un nodo inicial, pero con diferentes estrategias.

---

## 🔍 1. BFS - Búsqueda en Amplitud (Breadth-First Search)

### Concepto

BFS es un algoritmo que explora el grafo **nivel por nivel**. Comienza en un nodo inicial y:

1. Visita el nodo inicial
2. Visita todos los vecinos del nodo inicial (nivel 1)
3. Luego visita todos los vecinos no visitados de los nodos del nivel 1 (nivel 2)
4. Continúa expandiendo nivel por nivel

**Estructura de datos:** Utiliza una **cola (Queue)**

### Características

✅ **Explora por niveles:** Visita primero los nodos más cercanos  
✅ **Encuentra el camino más corto:** En grafos no ponderados  
✅ **Completo:** Garantiza encontrar solución si existe  
✅ **Óptimo:** En grafos no ponderados

### Complejidad

```
Complejidad de Tiempo:    O(V + E)
Complejidad de Espacio:   O(V)
Donde V = número de vértices, E = número de aristas
```

### Pseudocódigo BFS

```
function BFS(grafo, nodoInicial):
    cola = Cola()
    visitados = Conjunto()
    
    cola.encolar(nodoInicial)
    visitados.agregar(nodoInicial)
    
    while cola no está vacía:
        nodoActual = cola.desencolar()
        imprimir(nodoActual)  // Procesar el nodo
        
        for cada vecino en grafo[nodoActual]:
            if vecino no está en visitados:
                visitados.agregar(vecino)
                cola.encolar(vecino)
```

### Implementación en Python

```python
from collections import deque

def bfs(grafo, nodoInicial):
    """
    Realiza BFS comenzando desde nodoInicial
    
    Args:
        grafo: Diccionario representando lista de adyacencia
        nodoInicial: Nodo donde comienza la búsqueda
    """
    visitados = set()
    cola = deque([nodoInicial])
    visitados.add(nodoInicial)
    resultado = []
    
    while cola:
        nodo = cola.popleft()
        resultado.append(nodo)
        
        for vecino in grafo[nodo]:
            if vecino not in visitados:
                visitados.add(vecino)
                cola.append(vecino)
    
    return resultado

# Ejemplo de uso
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

print(bfs(grafo, 'A'))  # Salida: ['A', 'B', 'C', 'D', 'E', 'F']
```

### Implementación en JavaScript

```javascript
function bfs(grafo, nodoInicial) {
    const visitados = new Set();
    const cola = [nodoInicial];
    visitados.add(nodoInicial);
    const resultado = [];
    
    while (cola.length > 0) {
        const nodo = cola.shift();
        resultado.push(nodo);
        
        for (const vecino of grafo[nodo]) {
            if (!visitados.has(vecino)) {
                visitados.add(vecino);
                cola.push(vecino);
            }
        }
    }
    
    return resultado;
}

// Ejemplo de uso
const grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
};

console.log(bfs(grafo, 'A'));  // ['A', 'B', 'C', 'D', 'E', 'F']
```

### Visualización de BFS

Para el siguiente grafo:

```
        A
       / \
      B   C
     / \   \
    D   E   F
```

**Orden de visita en BFS (comenzando en A):**

```
Paso 0: Visitar A
        Cola: []
        Visitados: {A}

Paso 1: Procesar A, agregar B y C
        Cola: [B, C]
        Visitados: {A}

Paso 2: Procesar B, agregar D y E
        Cola: [C, D, E]
        Visitados: {A, B}

Paso 3: Procesar C, agregar F
        Cola: [D, E, F]
        Visitados: {A, B, C}

Paso 4: Procesar D (sin nuevos vecinos)
        Cola: [E, F]
        Visitados: {A, B, C, D}

Paso 5: Procesar E (sin nuevos vecinos)
        Cola: [F]
        Visitados: {A, B, C, D, E}

Paso 6: Procesar F (sin nuevos vecinos)
        Cola: []
        Visitados: {A, B, C, D, E, F}

Resultado BFS: A → B → C → D → E → F
```

### Aplicaciones de BFS

- Encontrar el camino más corto en grafos no ponderados
- Análisis de redes sociales (amigos de amigos)
- Algoritmo de Dijkstra (extensión para grafos ponderados)
- Búsqueda de componentes conexas
- Comprobación de bipartición

---

## 🔄 2. DFS - Búsqueda en Profundidad (Depth-First Search)

### Concepto

DFS es un algoritmo que explora el grafo **en profundidad**. Comienza en un nodo inicial y:

1. Visita el nodo inicial
2. Elige un vecino no visitado y lo visita
3. Repite el proceso recursivamente hasta llegar a un nodo sin vecinos no visitados
4. Retrocede (backtrack) y explora otras ramas

**Estructura de datos:** Utiliza una **pila (Stack)** o **recursión**

### Características

✅ **Explora profundamente:** Sigue un camino hasta el final  
✅ **Usa menos memoria (iterativo):** O(h) donde h es la altura  
✅ **Versión recursiva:** Más elegante pero usa pila de recursión  
✅ **Detecta ciclos:** Útil para análisis de grafos

### Complejidad

```
Complejidad de Tiempo:    O(V + E)
Complejidad de Espacio:   O(V)
```

### Pseudocódigo DFS (Recursivo)

```
function DFS(grafo, nodo, visitados):
    visitados.agregar(nodo)
    imprimir(nodo)  // Procesar el nodo
    
    for cada vecino en grafo[nodo]:
        if vecino no está en visitados:
            DFS(grafo, vecino, visitados)

// Llamada inicial
visitados = Conjunto()
DFS(grafo, nodoInicial, visitados)
```

### Pseudocódigo DFS (Iterativo)

```
function DFS_Iterativo(grafo, nodoInicial):
    pila = Pila()
    visitados = Conjunto()
    
    pila.apilar(nodoInicial)
    visitados.agregar(nodoInicial)
    
    while pila no está vacía:
        nodoActual = pila.desapilar()
        imprimir(nodoActual)
        
        for cada vecino en grafo[nodoActual]:
            if vecino no está en visitados:
                visitados.agregar(vecino)
                pila.apilar(vecino)
```

### Implementación en Python (Recursiva)

```python
def dfs_recursivo(grafo, nodo, visitados=None):
    """
    DFS recursivo
    """
    if visitados is None:
        visitados = set()
    
    visitados.add(nodo)
    print(nodo)  # Procesar el nodo
    
    for vecino in grafo[nodo]:
        if vecino not in visitados:
            dfs_recursivo(grafo, vecino, visitados)
    
    return visitados

# Ejemplo de uso
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

dfs_recursivo(grafo, 'A')  # Salida: A, B, D, E, F, C
```

### Implementación en Python (Iterativa)

```python
def dfs_iterativo(grafo, nodoInicial):
    """
    DFS iterativo usando pila
    """
    visitados = set()
    pila = [nodoInicial]
    visitados.add(nodoInicial)
    resultado = []
    
    while pila:
        nodo = pila.pop()
        resultado.append(nodo)
        
        for vecino in grafo[nodo]:
            if vecino not in visitados:
                visitados.add(vecino)
                pila.append(vecino)
    
    return resultado

# Ejemplo
print(dfs_iterativo(grafo, 'A'))  # Salida puede variar: ['A', 'C', 'F', 'E', 'B', 'D']
```

### Implementación en JavaScript (Recursiva)

```javascript
function dfsRecursivo(grafo, nodo, visitados = new Set()) {
    visitados.add(nodo);
    console.log(nodo);
    
    for (const vecino of grafo[nodo]) {
        if (!visitados.has(vecino)) {
            dfsRecursivo(grafo, vecino, visitados);
        }
    }
    
    return visitados;
}

// Ejemplo
const grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
};

dfsRecursivo(grafo, 'A');
```

### Visualización de DFS

Para el mismo grafo anterior:

```
        A
       / \
      B   C
     / \   \
    D   E   F
```

**Orden de visita en DFS (comenzando en A):**

```
Paso 0: Visitar A, explorar B
Paso 1: Visitar B, explorar D
Paso 2: Visitar D (sin vecinos no visitados), retroceder
Paso 3: Retroceder a B, explorar E
Paso 4: Visitar E, explorar F
Paso 5: Visitar F, explorar C
Paso 6: Visitar C (sin vecinos no visitados)

Resultado DFS: A → B → D → E → F → C
```

### Aplicaciones de DFS

- Detectar ciclos en grafos
- Ordenamiento topológico
- Búsqueda de componentes fuertemente conexas
- Resolución de problemas con backtracking
- Detección de puentes y puntos de articulación
- Generación de laberintos

---

## 🔄 Comparación BFS vs DFS

| Aspecto | BFS | DFS |
|--------|-----|-----|
| **Estructura** | Cola | Pila/Recursión |
| **Orden de exploración** | Por niveles | En profundidad |
| **Camino más corto** | ✅ Sí (no ponderado) | ❌ No garantizado |
| **Complejidad de Tiempo** | O(V + E) | O(V + E) |
| **Complejidad de Espacio** | O(V) | O(V) |
| **Memoria para grafos anchoss** | Más consumo | Menos consumo |
| **Recursión** | No natural | Natural y elegante |
| **Casos de uso** | Camino más corto | Ciclos, backtracking |

---

## 📊 Comparación Visual

### Orden de Visita en el Mismo Grafo

```
Grafo:
        A
       / \
      B   C
     / \   \
    D   E   F

BFS (desde A):  A → B → C → D → E → F
                (Por niveles: nivel 0, luego nivel 1, luego nivel 2)

DFS (desde A):  A → B → D → E → F → C
                (Explora profundamente cada rama)
```

---

## ✅ Puntos Clave a Recordar

1. **BFS** usa una **cola** y explora **por niveles**
2. **DFS** usa una **pila** (o recursión) y explora **en profundidad**
3. Ambos tienen complejidad **O(V + E)**
4. **BFS** encuentra el camino más corto en grafos no ponderados
5. **DFS** es útil para detectar ciclos y backtracking
6. Eligir el algoritmo correcto depende del problema específico

---

## 🎯 Resumen de la Serie

Esta serie de posts ha cubierto los fundamentos de los grafos:

1. **Post #1:** Introducción - Conceptos básicos y tipos de grafos
2. **Post #2:** Representación - Cómo almacenar grafos en memoria
3. **Post #3:** Recorrido - Algoritmos BFS y DFS

Con estos conocimientos, estás listo para explorar algoritmos más avanzados como:
- Algoritmo de Dijkstra (caminos más cortos)
- Algoritmo de Floyd-Warshall
- Búsqueda de componentes conexas
- Ordenamiento topológico

---

**¿Preguntas o comentarios?** Déjalos en la sección de comentarios o contacta al equipo técnico.
