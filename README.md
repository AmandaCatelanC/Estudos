# Estudos
Estudos de Python para melhor desempenho em análises de dados

🆚 Diferenças entre list (array nativo) e numpy.ndarray:

| Característica         | `list` (array nativo)                         | `numpy.ndarray` (NumPy)                                     |
|------------------------|-----------------------------------------------|--------------------------------------------------------------|
| **Tipo dos elementos** | Pode misturar tipos (int, str, float etc.)    | Deve ser homogêneo (todos do mesmo tipo, ex: float64)        |
| **Desempenho**         | Mais lento, não otimizado para cálculos       | Muito mais rápido (implementado em C, vetorizado)            |
| **Operações vetoriais**| Não suporta (`[1, 2, 3] * 2` repete a lista)  | Suporta (`np.array([1, 2, 3]) * 2` dá `[2, 4, 6]`)           |
| **Dimensões**          | Apenas 1D ou listas de listas                 | Suporte nativo a 1D, 2D, nD (matrizes, tensores)             |
| **Uso em Data Science**| Limitado                                      | Padrão da indústria para computação numérica e científica     |
| **Funções matemáticas**| Não tem                                       | Tem: `np.mean`, `np.std`, `np.sum`, `np.dot`, etc.           |
| **Memória**            | Mais ineficiente                              | Mais eficiente (tipagem estática, uso otimizado de memória)  |


Formatos de arquivos JSON
✔️ Caso 1: Lista de objetos (ideal para read_json)
<pre>
[
  {"id": 1, "price": 250000, "area": 120, ...},
  {"id": 2, "price": 320000, "area": 150, ...}
]
</pre>
