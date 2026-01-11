# Primitive Reference

Full taxonomy for `ascii-explainer` skill. Consult when Quick Pick doesn't match.

---

## All Primitives

### Discrete
| Primitive | Definition | Key Property |
|-----------|------------|--------------|
| Graph | Nodes + edges, cycles OK | Anything→anything |
| DAG | Directed, no cycles | Topological sort |
| Tree | Single parent per node | Strict hierarchy |
| Bipartite | Two node sets | Edges cross sets |
| Hypergraph | Edges connect 2+ nodes | N-ary relations |
| Lattice | Partial order w/ meet/join | Sup/inf exist |

### Stateful
| Primitive | Definition | Key Property |
|-----------|------------|--------------|
| State Machine | States + transitions | One active state |
| Petri Net | Places + transitions + tokens | Concurrent states |

### Sequential
| Primitive | Definition | Key Property |
|-----------|------------|--------------|
| Sequence | Ordered events | Order matters |
| Queue | FIFO items | First in, first out |
| Stack | LIFO items | Last in, first out |
| Pipeline | Linear stages | Transform + pass |
| Timeline | Events w/ duration | Overlaps matter |

### Spatial
| Primitive | Definition | Key Property |
|-----------|------------|--------------|
| Matrix | 2D values | Row × column |
| Grid | 2D/3D cells | Neighbors by position |
| Tensor | N-dimensional | Semantic axes |

### Continuous
| Primitive | Definition | Key Property |
|-----------|------------|--------------|
| Manifold | Space + trajectories | States are points |

---

## Domain Mappings

### SWE
| Diagram | Primitive |
|---------|-----------|
| Class Diagram | Graph |
| ERD | Graph |
| Sequence Diagram | DAG |
| State Machine | State Machine |
| DFD | DAG |

### AI/ML
| Diagram | Primitive |
|---------|-----------|
| Computational Graph | DAG |
| Bayesian Network | DAG |
| Decision Tree | Tree |
| Markov Chain | Graph |

### DevOps
| Diagram | Primitive |
|---------|-----------|
| CI/CD Pipeline | Pipeline |
| K8s Architecture | Tree+Graph |
| Message Queue | Queue |
| Log Timeline | Timeline |

### Networking
| Diagram | Primitive |
|---------|-----------|
| OSI Model | Stack |
| Network Topology | Graph |
| Load Balancer | Bipartite |

### Finance
| Diagram | Primitive |
|---------|-----------|
| Order Book | Bipartite+Queue |
| Correlation Matrix | Matrix |
| Trade Flow | DAG |

### Biology
| Diagram | Primitive |
|---------|-----------|
| Phylogenetic Tree | Tree |
| Metabolic Pathway | Hypergraph |
| Gene Regulatory | Graph |
| Cell Cycle | State Machine |

### Physics
| Diagram | Primitive |
|---------|-----------|
| Feynman Diagram | Hypergraph |
| Phase Space | Manifold |
| Crystal Lattice | Lattice |
| Quantum Circuit | DAG |

### Product/UX
| Diagram | Primitive |
|---------|-----------|
| User Flow | State Machine |
| Sitemap | Tree |
| Journey Map | Timeline |
| A/B Results | Matrix |

### Data Engineering
| Diagram | Primitive |
|---------|-----------|
| ETL | DAG |
| Data Lineage | DAG |
| Star Schema | Tree |

### Security
| Diagram | Primitive |
|---------|-----------|
| Attack Tree | Tree |
| Kill Chain | Pipeline |
| Access Control | Lattice |

---

## ASCII Templates

**Graph/DAG:**
```
A → B → D
↓       ↑
C ──────┘
```

**Tree:**
```
     Root
    /    \
   A      B
  / \    / \
 C   D  E   F
```

**Bipartite:**
```
Users     Resources
  ●─────────●
  ●────╲╱───●
  ●─────╳───●
```

**State Machine:**
```
[Idle] --start--> [Running]
   ↑                  │
   └──────stop────────┘
```

**Queue:**
```
IN ──▶ [A][B][C][D] ──▶ OUT
          FIFO
```

**Stack:**
```
   ┌───┐
   │ A │ ←── top
   │ B │
   │ C │
   └───┘
```

**Pipeline:**
```
[Extract] ──▶ [Transform] ──▶ [Load]
```

**Timeline:**
```
─────[████████]──────────────▶ time
        Task A
──────────[████████████]─────▶
              Task B
```

**Matrix:**
```
     t1  t2  t3
    ┌───┬───┬───┐
 N1 │ ● │   │ ● │
    ├───┼───┼───┤
 N2 │   │ ● │   │
    └───┴───┴───┘
```

**Manifold:**
```
  ↑ x2
  │    ╭──→ attractor
  │  ●╱
  └────────→ x1
```
