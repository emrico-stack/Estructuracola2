# Ejemplos de Código - Implementaciones de Grafos

Este archivo contiene implementaciones completas y reutilizables de estructuras y algoritmos de grafos.

---

## 📁 Índice

1. [Clase Grafo en Python](#clase-grafo-en-python)
2. [Clase Grafo en JavaScript](#clase-grafo-en-javascript)
3. [Ejemplos de Uso](#ejemplos-de-uso)
4. [Pruebas y Validación](#pruebas-y-validación)

---

## 🐍 Clase Grafo en Python

### Implementación Completa

```python
from collections import deque, defaultdict

class Grafo:
    """
    Clase que representa un grafo usando lista de adyacencia.
    Soporta grafos dirigidos y no dirigidos.
    """
    
    def __init__(self, dirigido=False):
        """
        Inicializa el grafo.
        
        Args:
            dirigido (bool): Si True, crea un grafo dirigido. Por defecto False.
        """
        self.grafo = defaultdict(list)
        self.dirigido = dirigido
        self.nodos = set()
    
    def agregar_arista(self, u, v, peso=1):
        """
        Agrega una arista entre dos nodos.
        
        Args:
            u: Nodo origen
            v: Nodo destino
            peso: Peso de la arista (por defecto 1)
        """
        self.grafo[u].append((v, peso))
        self.nodos.add(u)
        self.nodos.add(v)
        
        # Si el grafo es no dirigido, agregar la arista inversa
        if not self.dirigido:
            self.grafo[v].append((u, peso))
    
    def agregar_nodo(self, nodo):
        """Agrega un nodo aislado al grafo."""
        self.nodos.add(nodo)
        if nodo not in self.grafo:
            self.grafo[nodo] = []
    
    def obtener_vecinos(self, nodo):
        """Retorna la lista de vecinos de un nodo."""
        return self.grafo[nodo]
    
    def bfs(self, inicio):
        """
        Realiza búsqueda en amplitud (BFS).
        
        Args:
            inicio: Nodo inicial de la búsqueda
        
        Returns:
            Lista con el orden de visita
        """
        visitados = set()
        cola = deque([inicio])
        visitados.add(inicio)
        resultado = []
        
        while cola:
            nodo = cola.popleft()
            resultado.append(nodo)
            
            for vecino, _ in self.grafo[nodo]:
                if vecino not in visitados:
                    visitados.add(vecino)
                    cola.append(vecino)
        
        return resultado
    
    def dfs_recursivo(self, nodo, visitados=None):
        """
        Realiza búsqueda en profundidad (DFS) recursiva.
        
        Args:
            nodo: Nodo actual
            visitados: Conjunto de nodos visitados
        
        Returns:
            Conjunto de nodos visitados
        """
        if visitados is None:
            visitados = set()
        
        visitados.add(nodo)
        
        for vecino, _ in self.grafo[nodo]:
            if vecino not in visitados:
                self.dfs_recursivo(vecino, visitados)
        
        return visitados
    
    def dfs_iterativo(self, inicio):
        """
        Realiza búsqueda en profundidad (DFS) iterativa.
        
        Args:
            inicio: Nodo inicial de la búsqueda
        
        Returns:
            Lista con el orden de visita
        """
        visitados = set()
        pila = [inicio]
        visitados.add(inicio)
        resultado = []
        
        while pila:
            nodo = pila.pop()
            resultado.append(nodo)
            
            for vecino, _ in self.grafo[nodo]:
                if vecino not in visitados:
                    visitados.add(vecino)
                    pila.append(vecino)
        
        return resultado
    
    def obtener_componentes_conexas(self):
        """
        Encuentra todas las componentes conexas del grafo.
        
        Returns:
            Lista de listas, cada una con los nodos de una componente
        """
        visitados = set()
        componentes = []
        
        for nodo in self.nodos:
            if nodo not in visitados:
                componente = self.dfs_recursivo(nodo, set())
                visitados.update(componente)
                componentes.append(list(componente))
        
        return componentes
    
    def tiene_ciclo(self):
        """
        Determina si el grafo tiene ciclos.
        
        Returns:
            bool: True si tiene ciclos, False si es acíclico
        """
        visitados = set()
        rec_stack = set()
        
        def tiene_ciclo_util(nodo):
            visitados.add(nodo)
            rec_stack.add(nodo)
            
            for vecino, _ in self.grafo[nodo]:
                if vecino not in visitados:
                    if tiene_ciclo_util(vecino):
                        return True
                elif vecino in rec_stack:
                    return True
            
            rec_stack.remove(nodo)
            return False
        
        for nodo in self.nodos:
            if nodo not in visitados:
                if tiene_ciclo_util(nodo):
                    return True
        
        return False
    
    def __str__(self):
        """Representación en string del grafo."""
        resultado = "Grafo:\n"
        for nodo in sorted(self.grafo.keys()):
            vecinos = ", ".join([f"{v}({p})" for v, p in self.grafo[nodo]])
            resultado += f"  {nodo} -> [{vecinos}]\n"
        return resultado
```

---

## 📱 Clase Grafo en JavaScript

### Implementación Completa

```javascript
class Grafo {
    /**
     * Clase que representa un grafo usando lista de adyacencia.
     * @param {boolean} dirigido - Si true, el grafo es dirigido. Por defecto false.
     */
    constructor(dirigido = false) {
        this.grafo = new Map();
        this.dirigido = dirigido;
        this.nodos = new Set();
    }
    
    /**
     * Agrega una arista entre dos nodos.
     * @param {*} u - Nodo origen
     * @param {*} v - Nodo destino
     * @param {number} peso - Peso de la arista (por defecto 1)
     */
    agregarArista(u, v, peso = 1) {
        if (!this.grafo.has(u)) {
            this.grafo.set(u, []);
        }
        this.grafo.get(u).push({ destino: v, peso });
        this.nodos.add(u);
        this.nodos.add(v);
        
        // Si el grafo es no dirigido, agregar la arista inversa
        if (!this.dirigido) {
            if (!this.grafo.has(v)) {
                this.grafo.set(v, []);
            }
            this.grafo.get(v).push({ destino: u, peso });
        }
    }
    
    /**
     * Agrega un nodo aislado al grafo.
     */
    agregarNodo(nodo) {
        this.nodos.add(nodo);
        if (!this.grafo.has(nodo)) {
            this.grafo.set(nodo, []);
        }
    }
    
    /**
     * Obtiene los vecinos de un nodo.
     */
    obtenerVecinos(nodo) {
        return this.grafo.get(nodo) || [];
    }
    
    /**
     * Realiza búsqueda en amplitud (BFS).
     * @param {*} inicio - Nodo inicial
     * @returns {Array} Lista con el orden de visita
     */
    bfs(inicio) {
        const visitados = new Set();
        const cola = [inicio];
        visitados.add(inicio);
        const resultado = [];
        
        while (cola.length > 0) {
            const nodo = cola.shift();
            resultado.push(nodo);
            
            for (const { destino } of this.grafo.get(nodo) || []) {
                if (!visitados.has(destino)) {
                    visitados.add(destino);
                    cola.push(destino);
                }
            }
        }
        
        return resultado;
    }
    
    /**
     * Realiza búsqueda en profundidad (DFS) recursiva.
     * @param {*} nodo - Nodo actual
     * @param {Set} visitados - Conjunto de nodos visitados
     * @returns {Set} Conjunto de nodos visitados
     */
    dfsRecursivo(nodo, visitados = new Set()) {
        visitados.add(nodo);
        
        for (const { destino } of this.grafo.get(nodo) || []) {
            if (!visitados.has(destino)) {
                this.dfsRecursivo(destino, visitados);
            }
        }
        
        return visitados;
    }
    
    /**
     * Realiza búsqueda en profundidad (DFS) iterativa.
     * @param {*} inicio - Nodo inicial
     * @returns {Array} Lista con el orden de visita
     */
    dfsIterativo(inicio) {
        const visitados = new Set();
        const pila = [inicio];
        visitados.add(inicio);
        const resultado = [];
        
        while (pila.length > 0) {
            const nodo = pila.pop();
            resultado.push(nodo);
            
            for (const { destino } of this.grafo.get(nodo) || []) {
                if (!visitados.has(destino)) {
                    visitados.add(destino);
                    pila.push(destino);
                }
            }
        }
        
        return resultado;
    }
    
    /**
     * Encuentra todas las componentes conexas del grafo.
     * @returns {Array<Array>} Lista de componentes conexas
     */
    obtenerComponentesConexas() {
        const visitados = new Set();
        const componentes = [];
        
        for (const nodo of this.nodos) {
            if (!visitados.has(nodo)) {
                const componente = this.dfsRecursivo(nodo, new Set());
                for (const n of componente) {
                    visitados.add(n);
                }
                componentes.push(Array.from(componente));
            }
        }
        
        return componentes;
    }
    
    /**
     * Determina si el grafo tiene ciclos.
     * @returns {boolean} True si tiene ciclos
     */
    tieneCiclo() {
        const visitados = new Set();
        const recStack = new Set();
        
        const tieneCicloUtil = (nodo) => {
            visitados.add(nodo);
            recStack.add(nodo);
            
            for (const { destino } of this.grafo.get(nodo) || []) {
                if (!visitados.has(destino)) {
                    if (tieneCicloUtil(destino)) {
                        return true;
                    }
                } else if (recStack.has(destino)) {
                    return true;
                }
            }
            
            recStack.delete(nodo);
            return false;
        };
        
        for (const nodo of this.nodos) {
            if (!visitados.has(nodo)) {
                if (tieneCicloUtil(nodo)) {
                    return true;
                }
            }
        }
        
        return false;
    }
    
    /**
     * Obtiene una representación en string del grafo.
     */
    toString() {
        let resultado = "Grafo:\n";
        for (const [nodo, vecinos] of this.grafo) {
            const adyacentes = vecinos
                .map(v => `${v.destino}(${v.peso})`)
                .join(", ");
            resultado += `  ${nodo} -> [${adyacentes}]\n`;
        }
        return resultado;
    }
}
```

---

## 📚 Ejemplos de Uso

### Python

```python
# Crear un grafo no dirigido
g = Grafo(dirigido=False)

# Agregar aristas
g.agregar_arista('A', 'B')
g.agregar_arista('A', 'C')
g.agregar_arista('B', 'D')
g.agregar_arista('B', 'E')
g.agregar_arista('C', 'F')
g.agregar_arista('E', 'F')

print(g)

# BFS
print("BFS desde A:", g.bfs('A'))

# DFS
print("DFS desde A:", g.dfs_iterativo('A'))

# Componentes conexas
print("Componentes:", g.obtener_componentes_conexas())

# Detectar ciclos
print("¿Tiene ciclos?:", g.tiene_ciclo())
```

### JavaScript

```javascript
// Crear un grafo no dirigido
const g = new Grafo(false);

// Agregar aristas
g.agregarArista('A', 'B');
g.agregarArista('A', 'C');
g.agregarArista('B', 'D');
g.agregarArista('B', 'E');
g.agregarArista('C', 'F');
g.agregarArista('E', 'F');

console.log(g.toString());

// BFS
console.log("BFS desde A:", g.bfs('A'));

// DFS
console.log("DFS desde A:", g.dfsIterativo('A'));

// Componentes conexas
console.log("Componentes:", g.obtenerComponentesConexas());

// Detectar ciclos
console.log("¿Tiene ciclos?:", g.tieneCiclo());
```

---

## ✅ Pruebas y Validación

### Test Script en Python

```python
def ejecutar_pruebas():
    """Ejecuta pruebas de validación del grafo."""
    
    print("=" * 50)
    print("PRUEBAS DE VALIDACIÓN - GRAFOS")
    print("=" * 50)
    
    # Test 1: Grafo simple
    print("\n[Test 1] Grafo simple no dirigido")
    g1 = Grafo(dirigido=False)
    g1.agregar_arista('A', 'B')
    g1.agregar_arista('B', 'C')
    g1.agregar_arista('C', 'D')
    print(f"BFS: {g1.bfs('A')}")
    print(f"DFS: {g1.dfs_iterativo('A')}")
    
    # Test 2: Grafo con ciclo
    print("\n[Test 2] Grafo con ciclo")
    g2 = Grafo(dirigido=False)
    g2.agregar_arista('A', 'B')
    g2.agregar_arista('B', 'C')
    g2.agregar_arista('C', 'A')
    print(f"¿Tiene ciclo?: {g2.tiene_ciclo()}")
    
    # Test 3: Grafo desconexo
    print("\n[Test 3] Grafo desconexo")
    g3 = Grafo(dirigido=False)
    g3.agregar_arista('A', 'B')
    g3.agregar_arista('C', 'D')
    g3.agregar_nodo('E')
    componentes = g3.obtener_componentes_conexas()
    print(f"Número de componentes: {len(componentes)}")
    print(f"Componentes: {componentes}")
    
    print("\n" + "=" * 50)
    print("PRUEBAS COMPLETADAS")
    print("=" * 50)

if __name__ == "__main__":
    ejecutar_pruebas()
```

---

## 📝 Notas

- Las implementaciones soportan tanto grafos dirigidos como no dirigidos
- Los algoritmos BFS y DFS tienen complejidad O(V + E)
- La detección de ciclos funciona para grafos dirigidos
- Todas las operaciones están documentadas con docstrings

---

