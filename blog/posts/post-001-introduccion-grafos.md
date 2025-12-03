# Post #1: Introducción a los Grafos: Nodos, Aristas y Tipos

**Fecha:** Diciembre 3, 2025  
**Categoría:** Estructuras de Datos - Grafos  
**Nivel:** Principiante  
**Tiempo de lectura:** 8 minutos

---

## 📚 Contenido

### ¿Qué es un Grafo?

Un **grafo** es una estructura de datos no lineal que permite representar relaciones entre objetos. Formalmente, un grafo es un conjunto de **nodos** (vértices) conectados por **aristas** (ejes).

Los grafos se utilizan en muchas aplicaciones del mundo real:
- **Redes sociales:** Representar amigos y conexiones
- **Mapas y navegación:** GPS, rutas óptimas
- **Redes de computadoras:** Conectividad entre dispositivos
- **Sistemas de recomendación:** Relaciones entre usuarios y productos
- **Análisis de dependencias:** Proyectos, tareas, compiladores

---

## 🔑 Conceptos Clave

### 1. **Vértices o Nodos**
Son los elementos individuales del grafo. Cada nodo representa un objeto o entidad en el sistema que modelamos.

**Ejemplo:** En una red social, cada usuario es un nodo.

### 2. **Aristas o Ejes**
Son las conexiones entre dos nodos. Representan la relación entre los vértices.

**Ejemplo:** En una red social, una amistad es una arista que conecta dos usuarios.

### 3. **Peso o Ponderación** (Opcional)
Algunos grafos tienen valores asociados a las aristas, llamados pesos. Representan el costo, distancia o capacidad de una conexión.

**Ejemplo:** En un mapa, el peso de una arista podría ser la distancia en kilómetros entre dos ciudades.

---

## 🎯 Tipos de Grafos

### **Grafo No Dirigido**
- Las aristas no tienen dirección
- La relación es simétrica: si hay arista de A a B, entonces hay arista de B a A
- **Ejemplo:** Red de amigos (la amistad es mutua)

```
    A ---- B
    |      |
    |      |
    C ---- D
```

### **Grafo Dirigido (Dígrafo)**
- Las aristas tienen dirección (representadas por flechas)
- Una arista va de un nodo A a un nodo B, pero no necesariamente en sentido contrario
- **Ejemplo:** Seguidos en Twitter (puedo seguir a alguien sin que me siga de vuelta)

```
    A ----> B
    |       |
    v       v
    C ----> D
```

### **Grafo Ponderado**
- Las aristas tienen asociado un valor numérico (peso)
- Puede ser dirigido o no dirigido
- **Ejemplo:** Distancias entre ciudades en un mapa

```
    A --5-- B
    |       |
   3|       |7
    |       |
    C ---2--D
```

### **Grafo Cíclico vs Acíclico**
- **Cíclico:** Contiene al menos un ciclo (camino que comienza y termina en el mismo nodo)
- **Acíclico:** No contiene ciclos. Los árboles son grafos acíclicos especiales

### **Grafo Conexo vs Desconexo**
- **Conexo:** Existe un camino entre cualquier par de nodos
- **Desconexo:** Existen nodos sin camino entre ellos

---

## 📊 Ejemplo Visual: Grafo No Dirigido con 5 Nodos

A continuación, se muestra un grafo no dirigido con 5 nodos (A, B, C, D, E) y sus conexiones:

```
          B -------- D
         / \         /
        /   \       /
       A     \     /
        \     \   /
         \     \ /
          \     E
           \   /
            \ /
             C
```

**Descripción del grafo:**
- **Nodos:** {A, B, C, D, E}
- **Aristas:** {(A,B), (A,C), (B,C), (B,E), (B,D), (C,E), (D,E)}
- **Total de nodos:** 5
- **Total de aristas:** 7
- **Es conexo:** Sí (podemos llegar de cualquier nodo a cualquier otro)

### Matriz de adyacencia (preliminar):
```
  A B C D E
A 0 1 1 0 0
B 1 0 1 1 1
C 1 1 0 0 1
D 0 1 0 0 1
E 0 1 1 1 0
```

---

## 🔍 Terminología Común

| Término | Definición |
|---------|-----------|
| **Grado** | Número de aristas conectadas a un nodo |
| **Camino** | Secuencia de nodos conectados por aristas |
| **Ciclo** | Camino que comienza y termina en el mismo nodo |
| **Distancia** | Número de aristas en el camino más corto entre dos nodos |
| **Componente conexo** | Subconjunto de nodos que están conectados entre sí |

---

## ✅ Puntos Clave a Recordar

1. Un grafo es una estructura que conecta nodos mediante aristas
2. Los nodos representan entidades; las aristas representan relaciones
3. Los grafos pueden ser **dirigidos o no dirigidos**
4. Los grafos pueden ser **ponderados o no ponderados**
5. Existen múltiples aplicaciones prácticas para los grafos en ciencia de datos e ingeniería

---

## 📌 Próximas Lecturas

- **Post #2:** Representación de Grafos (Listas y Matrices de Adyacencia)
- **Post #3:** Algoritmos Fundamentales de Recorrido (BFS y DFS)

---

**¿Preguntas o comentarios?** Déjalos en la sección de comentarios o contacta al equipo técnico.
