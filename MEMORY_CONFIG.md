# Configuración de Memoria para Autocoder

## Configuración Actual (Laptop con RAM limitada)

```python
MAX_PARALLEL_AGENTS = 2      # Máximo de coding agents simultáneos
MAX_TOTAL_AGENTS = 4         # Máximo total de agentes (coding + testing)
DEFAULT_CONCURRENCY = 1      # Concurrencia por defecto
CODING_AGENT_TIMEOUT = 1200  # Timeout de 20 min para agentes colgados
```

## Configuraciones por Tipo de Equipo

### Laptop Básica (8GB RAM)
```python
MAX_PARALLEL_AGENTS = 1
MAX_TOTAL_AGENTS = 2
DEFAULT_CONCURRENCY = 1
```

### Laptop Media (16GB RAM) - ACTUAL
```python
MAX_PARALLEL_AGENTS = 2
MAX_TOTAL_AGENTS = 4
DEFAULT_CONCURRENCY = 1
```

### Desktop/Workstation (32GB RAM)
```python
MAX_PARALLEL_AGENTS = 3
MAX_TOTAL_AGENTS = 6
DEFAULT_CONCURRENCY = 2
```

### Servidor (64GB+ RAM) - CONFIGURACIÓN ORIGINAL
```python
MAX_PARALLEL_AGENTS = 5
MAX_TOTAL_AGENTS = 10
DEFAULT_CONCURRENCY = 3
```

## Cómo Cambiar la Configuración

Edita `parallel_orchestrator.py` líneas 122-124:

```bash
# Para ver configuración actual:
grep -n "MAX_PARALLEL\|MAX_TOTAL\|DEFAULT_CONC" parallel_orchestrator.py
```

## Optimizaciones Adicionales Aplicadas

1. **gc.collect()** - Libera memoria después de cada agente completado
2. **CODING_AGENT_TIMEOUT** - Mata agentes colgados después de 20 min

## Tips para Reducir RAM

1. Usar `--yolo` para desactivar testing agents
2. Usar `--testing-ratio 0` si usas la UI
3. No abrir la UI si no es necesario (consume ~700MB por proceso Node)
4. Usar modelo `claude-sonnet` en lugar de `claude-opus`

## Revertir a Configuración Original

```python
MAX_PARALLEL_AGENTS = 5
MAX_TOTAL_AGENTS = 10
DEFAULT_CONCURRENCY = 3
# Remover CODING_AGENT_TIMEOUT si no lo necesitas
```
