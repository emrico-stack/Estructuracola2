# 🗺️ Mapa de Navegación del Blog

Este archivo proporciona una **vista completa** de toda la estructura del Blog Técnico sobre Grafos.

---

## 📊 Estructura Visual

```
╔════════════════════════════════════════════════════════════════╗
║             BLOG TÉCNICO: ESTRUCTURA DE DATOS - GRAFOS         ║
║                        Fase 1 Completada                       ║
╚════════════════════════════════════════════════════════════════╝

                         📚 ÍNDICE PRINCIPAL
                            (index.md)
                                 │
                ┌────────────────┼────────────────┐
                │                │                │
            POST #1          POST #2          POST #3
        Introducción      Representación     Algoritmos
          (8 min)           (10 min)         (12 min)
```

---

## 🧭 Guía de Navegación

### Punto de Inicio Recomendado

**Para Principiantes:**
```
1. Comienza: README.md (Este directorio)
   ↓
2. Lee: blog/index.md (Índice principal)
   ↓
3. Estudia: blog/posts/post-001-introduccion-grafos.md
   ↓
4. Continúa: blog/posts/post-002-representacion-grafos.md
   ↓
5. Aprende: blog/posts/post-003-algoritmos-recorrido.md
   ↓
6. Practica: blog/EJEMPLOS_CODIGO.md
```

**Para Desarrolladores:**
```
1. Accede directamente: blog/EJEMPLOS_CODIGO.md
   ↓
2. Lee la teoría: blog/posts/ (según necesidad)
   ↓
3. Implementa: Usa las clases de Python/JavaScript
```

---

## 📄 Contenido por Archivo

### 📑 Raíz del Proyecto

| Archivo | Descripción | Tamaño |
|---------|-------------|--------|
| `README.md` | Descripción general del proyecto | 3 KB |

### 📚 Carpeta `/blog/`

#### Archivos Principales

| Archivo | Descripción | Tipo | Audiencia |
|---------|-------------|------|-----------|
| `index.md` | Índice principal del blog | 📖 Índice | Todos |
| `FASE1-RESUMEN.md` | Resumen ejecutivo Fase 1 | 📋 Resumen | Todos |
| `EJEMPLOS_CODIGO.md` | Código reutilizable | 💻 Código | Desarrolladores |

#### Artículos (Carpeta `/blog/posts/`)

| Post | Título | Nivel | Tiempo | Palabras |
|------|--------|-------|--------|----------|
| #1 | `post-001-introduccion-grafos.md` | Principiante | 8 min | ~2000 |
| #2 | `post-002-representacion-grafos.md` | Intermedio | 10 min | ~2500 |
| #3 | `post-003-algoritmos-recorrido.md` | Intermedio | 12 min | ~3000 |

#### Recursos (Carpeta `/blog/assets/`)

```
assets/
├── diagramas/        [Preparado para Fase 2]
├── ejemplos/         [Preparado para Fase 2]
└── datos/            [Preparado para Fase 2]
```

---

## 🎯 Mapa de Contenidos por Tópico

### Concepto: Grafos Básicos
- **Ubicación:** `posts/post-001-introduccion-grafos.md`
- **Secciones:**
  - ¿Qué es un Grafo?
  - Conceptos Clave (Vértices, Aristas)
  - Tipos de Grafos
  - Ejemplo Visual (Grafo de 5 nodos)
  - Terminología Común

### Concepto: Representación en Memoria
- **Ubicación:** `posts/post-002-representacion-grafos.md`
- **Secciones:**
  - Lista de Adyacencia
  - Matriz de Adyacencia
  - Comparación Lado a Lado
  - Tabla Comparativa
  - Guía de Selección

### Concepto: Algoritmos de Recorrido
- **Ubicación:** `posts/post-003-algoritmos-recorrido.md`
- **Secciones:**
  - BFS (Breadth-First Search)
  - DFS (Depth-First Search)
  - Visualización de Ejecución
  - Comparación BFS vs DFS
  - Aplicaciones Prácticas

### Recurso: Código Ejecutable
- **Ubicación:** `EJEMPLOS_CODIGO.md`
- **Contenido:**
  - Clase Grafo (Python)
  - Clase Grafo (JavaScript)
  - Ejemplos de Uso
  - Pruebas de Validación

---

## 🔍 Búsqueda Rápida

### Por Lenguaje de Programación

**Python:**
- Implementación: `EJEMPLOS_CODIGO.md` (Sección: "Clase Grafo en Python")
- Ejemplo BFS: `posts/post-003-algoritmos-recorrido.md`
- Ejemplo DFS: `posts/post-003-algoritmos-recorrido.md`

**JavaScript:**
- Implementación: `EJEMPLOS_CODIGO.md` (Sección: "Clase Grafo en JavaScript")
- Ejemplo BFS: `posts/post-003-algoritmos-recorrido.md`
- Ejemplo DFS: `posts/post-003-algoritmos-recorrido.md`

### Por Concepto

**Nodos y Aristas:**
- `posts/post-001-introduccion-grafos.md` → Sección "Conceptos Clave"

**Lista de Adyacencia:**
- `posts/post-002-representacion-grafos.md` → Sección "1. Lista de Adyacencia"
- `EJEMPLOS_CODIGO.md` → Método `obtener_vecinos()`

**Matriz de Adyacencia:**
- `posts/post-002-representacion-grafos.md` → Sección "2. Matriz de Adyacencia"

**BFS:**
- `posts/post-003-algoritmos-recorrido.md` → Sección "1. BFS"
- `EJEMPLOS_CODIGO.md` → Método `bfs()`

**DFS:**
- `posts/post-003-algoritmos-recorrido.md` → Sección "2. DFS"
- `EJEMPLOS_CODIGO.md` → Método `dfs_recursivo()` / `dfs_iterativo()`

---

## 📈 Progresión Recomendada

### Nivel 1: Conceptos Fundamentales (15 minutos)
```
1. Leer: post-001-introduccion-grafos.md
   Aprenderás: Qué es un grafo, nodos, aristas, tipos

2. Visualizar: Los diagramas ASCII en el mismo post
   Comprenderás: Cómo se ven grafos reales
```

### Nivel 2: Implementación (20 minutos)
```
1. Leer: post-002-representacion-grafos.md
   Aprenderás: Cómo guardar grafos en memoria

2. Estudiar: EJEMPLOS_CODIGO.md (parte Python/JavaScript)
   Comprenderás: Código real que funciona
```

### Nivel 3: Algoritmos (25 minutos)
```
1. Leer: post-003-algoritmos-recorrido.md
   Aprenderás: BFS y DFS

2. Ejecutar: Código de EJEMPLOS_CODIGO.md
   Practicarás: Implementar por tu cuenta

3. Visualizar: Los pasos de ejecución en el post
   Comprenderás: Cómo funcionan los algoritmos
```

---

## 🔗 Enlaces Rápidos

### Navegación Principal
- [README Principal](./README.md) - Descripción del proyecto
- [Índice del Blog](./blog/index.md) - Punto de inicio recomendado

### Posts
- [Post #1: Introducción](./blog/posts/post-001-introduccion-grafos.md)
- [Post #2: Representación](./blog/posts/post-002-representacion-grafos.md)
- [Post #3: Algoritmos](./blog/posts/post-003-algoritmos-recorrido.md)

### Recursos
- [Ejemplos de Código](./blog/EJEMPLOS_CODIGO.md)
- [Resumen Fase 1](./blog/FASE1-RESUMEN.md)

---

## 💡 Consejos de Navegación

### ✅ DO (Haz)
- Comienza con el Post #1 si eres principiante
- Lee los posts en orden secuencial
- Consulta EJEMPLOS_CODIGO.md mientras estudias
- Copia y ejecuta el código de ejemplo

### ❌ DON'T (No hagas)
- No saltes directamente al Post #3 sin leer #1 y #2
- No intentes memorizar - comprende los conceptos
- No copies código sin entenderlo
- No ignores los diagramas - son esenciales

---

## 📊 Estadísticas Generales

| Métrica | Valor |
|---------|-------|
| Total de Archivos | 7 |
| Total de Palabras | 7500+ |
| Total de Ejemplos de Código | 12+ |
| Lenguajes Cubiertos | 2 (Python, JavaScript) |
| Tiempo Total de Lectura | ~30 minutos |
| Nivel de Dificultad | Principiante a Intermedio |

---

## 🎓 Matriz de Habilidades

Después de completar este blog, deberías ser capaz de:

| Habilidad | Post | Nivel |
|-----------|------|-------|
| Explicar qué es un grafo | #1 | ⭐ |
| Identificar nodos y aristas | #1 | ⭐ |
| Clasificar tipos de grafos | #1 | ⭐⭐ |
| Implementar lista de adyacencia | #2 | ⭐⭐ |
| Implementar matriz de adyacencia | #2 | ⭐⭐ |
| Seleccionar representación óptima | #2 | ⭐⭐⭐ |
| Implementar BFS | #3 | ⭐⭐ |
| Implementar DFS | #3 | ⭐⭐ |
| Analizar complejidad | #3 | ⭐⭐⭐ |

**Leyenda:** ⭐ Básico | ⭐⭐ Intermedio | ⭐⭐⭐ Avanzado

---

## 🚀 Próximos Pasos

Después de completar el blog:

1. **Practica:** Implementa los algoritmos en tu lenguaje preferido
2. **Experimenta:** Modifica los ejemplos de código
3. **Explora:** Busca casos de uso en tus proyectos
4. **Aprende Más:** Espera la Fase 2 (Web Development)

---

## 📞 Referencias Cruzadas

### Conceptos Relacionados
- Grafos → Árboles (caso especial de grafos)
- Grafos → Redes (aplicación práctica)
- BFS → Dijkstra (extensión para camino más corto)
- DFS → Topological Sort (aplicación de DFS)

### Algoritmos Relacionados
- Dijkstra (Fase 3)
- Floyd-Warshall (Fase 3)
- Kruskal (Fase 3)
- Prim (Fase 3)

---

## ✨ Resumen Ejecutivo

Este blog proporciona una introducción **completa y práctica** a los grafos:

✅ **3 artículos bien estructurados** con 7500+ palabras  
✅ **12+ ejemplos de código** en Python y JavaScript  
✅ **Teoría + Práctica** combinadas efectivamente  
✅ **Estructura clara** para aprendizaje progresivo  
✅ **Listo para expandir** en Fase 2 y 3  

---

**¡Comienza tu viaje por el mundo de los Grafos!**

👉 **[Ir a Index del Blog](./blog/index.md)**

---

*Última actualización: Diciembre 3, 2025*
