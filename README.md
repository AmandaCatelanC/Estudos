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

Nesse caso:

<pre>
df = pd.read_json('house-price.json')
</pre>

❌ Caso 2: Objetos linha por linha (JSONL ou NDJSON)

<pre>
{"id": 1, "price": 250000, "area": 120, ...}
{"id": 2, "price": 320000, "area": 150, ...}
</pre>

Use:

<pre>
df = pd.read_json('house-price.json', lines=True)
</pre>
  
❌ Caso 3: Objeto com metadados (dicionário grande)

<pre>
{
  "metadata": { "source": "Kaggle", "columns": [...] },
  "data": [
    {"id": 1, "price": 250000, "area": 120, ...},
    {"id": 2, "price": 320000, "area": 150, ...}
  ]
}
</pre>

Use:

<pre>
with open('house-price.json', 'r') as f:
    raw = json.load(f)
df = pd.DataFrame(raw['data'])  # ou o nome correto da chave
</pre>

✅ 2. Inspeção Inicial
<pre>
df.head()             # Primeiras 5 linhas
df.tail()             # Últimas 5 linhas
df.shape              # Dimensão do DataFrame (linhas, colunas)
df.columns            # Nome das colunas
df.info()             # Tipos de dados + valores nulos
df.describe()         # Estatísticas descritivas de colunas numéricas
</pre>

✅ 3. Tratamento de Dados Faltantes

<pre>
df.isnull().sum()             # Contar valores nulos por coluna
df.dropna()                   # Remove linhas com valores nulos (use com cuidado)
df['Coluna'].fillna(valor)   # Preencher nulos com média, mediana, zero etc.
</pre>

✅ 4. Análise Estatística

<pre>
df['SalePrice'].mean()        # Média
df['SalePrice'].median()      # Mediana
df['SalePrice'].std()         # Desvio padrão
df.corr(numeric_only=True)    # Matriz de correlação (somente colunas numéricas)
</pre>

🧩 Mapa de calor de correlações numéricas
Pergunta: quais variáveis estão mais relacionadas?

<pre>
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.show()
</pre>
