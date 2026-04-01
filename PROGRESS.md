# urban-data-explorer — Progresso de Estudo

---

## Recursos disponíveis e onde cada um entra

|Recurso|O que cobre|Onde usar|
|---|---|---|
|Automate the Boring Stuff (gratuito: automatetheboringstuff.com)|Python do zero — variáveis, listas, funções, arquivos|Seções 1.1 e 1.2|
|Real Python — OOP Tutorial (gratuito: realpython.com/python3-object-oriented-programming)|Classes, herança, métodos especiais|Seção 1.2|
|Géron cap. 2 (Projeto de Ponta a Ponta)|NumPy, Pandas, visualização, pré-processamento aplicados|Seções 1.3, 1.4, 1.5|
|Escovedo cap. 3|Estatística e álgebra linear com exemplos|Fase 2 (próxima)|
|Géron caps. 1, 3, 4|Fundamentos de ML, classificação, treinamento de modelos|Fase 3 (futura)|
|Géron caps. 5, 6, 7|SVM, árvores de decisão, Random Forest|Fase 3 (futura)|
|Géron caps. 10–13 (só teoria, ignorar código TensorFlow)|Redes neurais, CNNs — conceitos para Fase 4|Fase 4 (futura)|
|PyTorch docs oficiais (pytorch.org/tutorials)|Implementação de redes neurais — substitui código do Géron Parte II|Fase 4 (futura)|

---

## Seção 1.1 — Python do zero

**Notebook:** `notebooks/01_python_fundamentos.ipynb` **Recurso:** Automate the Boring Stuff caps. 1–9

### Conceitos

- [ ] Variáveis e tipos: int, float, str, bool, None
- [ ] Operadores aritméticos, de comparação e lógicos
- [ ] Strings: fatiamento, split, join, strip, f-strings
- [ ] Listas: criação, indexação, append, pop, sort
- [ ] Dicionários: chave-valor, get, keys, values, items
- [ ] Conjuntos (sets): união, interseção, diferença
- [ ] Estruturas de controle: if, elif, else
- [ ] Laços: for, while, break, continue
- [ ] List comprehensions
- [ ] Funções: def, parâmetros, retorno, escopo local vs global
- [ ] *args e **kwargs
- [ ] Funções lambda, map, filter
- [ ] Módulos: import, from ... import
- [ ] Tratamento de erros: try, except, finally, raise
- [ ] Leitura de arquivos: open, with, modos r/w/a
- [ ] JSON: json.loads, json.dumps, json.load, json.dump
- [ ] Caminhos de arquivo: os, pathlib
- [ ] Iteradores e geradores: yield, next
- [ ] Decoradores: o que são, @staticmethod, @classmethod
- [ ] Context managers: with statement

### Entregas no notebook

- [ ] Função `ler_csv_manual(caminho)` que lê o dataset.csv linha a linha com `open` sem usar Pandas
- [ ] Retorna lista de dicionários — um por árvore, colunas como chaves
- [ ] Função `filtrar_por_risco(arvores, nivel)` filtrando PEQUENO / MÉDIO / GRANDE
- [ ] Função `resumo_por_especie(arvores)` retornando `{especie: quantidade}`
- [ ] Exportar o resumo como `outputs/resumo_especies.json`
- [ ] Tratar linhas malformadas com try/except sem travar o programa

### Checkpoint — responda com suas palavras antes de avançar

- [ ] O que acontece se acessar chave inexistente num dicionário sem `.get()`?
- [ ] Qual a diferença entre lista e conjunto (set) na prática?
- [ ] Por que usar `with open(...)` em vez de só `open(...)`?

---

## Seção 1.2 — Orientação a Objetos (OOP)

**Arquivo:** `src/dataset_loader.py` + `notebooks/02_oop_dataset_loader.ipynb` **Recurso:** Real Python — OOP Tutorial (realpython.com/python3-object-oriented-programming)

### Conceitos

- [ ] O que é OOP e quando usar classes em vez de funções soltas
- [ ] Classes e instâncias: class, **init**, self
- [ ] Atributos de instância vs atributos de classe
- [ ] Métodos de instância, @classmethod, @staticmethod
- [ ] Encapsulamento: convenções de _ e __
- [ ] Herança: herdar de uma classe, super()
- [ ] Polimorfismo: sobrescrever métodos
- [ ] Métodos especiais: **str**, **repr**, **len**, **eq**
- [ ] @property, getter e setter
- [ ] @dataclass para classes simples de dados
- [ ] Abstract classes: ABC, @abstractmethod

### Entregas em src/dataset_loader.py

- [ ] Classe `TreeDataset` com:
    - [ ] `__init__(self, filepath)` — recebe caminho do CSV
    - [ ] `load(self)` — carrega e retorna lista de dicionários
    - [ ] `filter_by_risk(self, nivel)` — filtra por Risco de Queda
    - [ ] `filter_by_species(self, especie)` — filtra por espécie
    - [ ] `summary(self)` — contagem por nível de risco
    - [ ] `__len__` — retorna quantas árvores foram carregadas
    - [ ] `__repr__` — ex: `TreeDataset(2028 árvores, 42 colunas)`
- [ ] Subclasse `GeoTreeDataset(TreeDataset)` com:
    - [ ] `validate_coordinates(self)` — checa presença de colunas GPS
    - [ ] Sobrescreve `summary()` adicionando info de coordenadas
- [ ] Notebook demonstrando uso das duas classes com exemplos reais

### Checkpoint

- [ ] Por que `__init__` recebe `self` como primeiro parâmetro?
- [ ] Qual a diferença entre herança e composição?
- [ ] O que acontece se não chamar `super().__init__()` numa subclasse?

---

## Seção 1.3 — NumPy

**Notebook:** `notebooks/03_numpy_arvores.ipynb` **Recurso:** Géron cap. 2 — seção "Obtenha os Dados" até "Prepare os Dados" (leia com dataset da Califórnia, reimplemente com dataset de árvores)

### Conceitos

- [ ] O que é NumPy e por que é mais rápido que listas Python
- [ ] ndarray: criação com array, zeros, ones, arange, linspace
- [ ] Shape e dimensões: diferença entre (3,) e (3,1) e (3,3)
- [ ] Reshape, flatten, squeeze, expand_dims
- [ ] Indexação básica e fatiamento multidimensional
- [ ] Fancy indexing
- [ ] Boolean indexing: filtrar arrays com condições
- [ ] Broadcasting: operações com shapes diferentes
- [ ] Operações matemáticas: +, -, *, /, np.sqrt, np.exp, np.log
- [ ] Reduções: sum, mean, std, min, max, argmin, argmax por eixo
- [ ] Álgebra linear: np.dot, np.matmul, @, np.linalg.norm
- [ ] Transposição: .T
- [ ] Stack e concatenação: np.stack, np.concatenate, np.vstack
- [ ] np.random: seed, rand, randn, randint
- [ ] Imagens como arrays: shape (H, W, C), uint8 vs float32

### Entregas no notebook

- [ ] Carregar colunas numéricas do dataset como array NumPy (usando leitor da seção 1.1)
- [ ] Calcular média, desvio padrão, mínimo e máximo de cada coluna por eixo
- [ ] Boolean indexing: separar árvores com `Probabilidade de ruptura > 50`
- [ ] Normalizar `Diâmetro Altura do Peito` para [0,1] manualmente
- [ ] Demonstrar broadcasting somando vetor de médias a uma matriz
- [ ] Carregar uma imagem com OpenCV e inspecionar shape, dtype, min, max

### Checkpoint

- [ ] O que significa `shape (2028, 42)`? Qual eixo são árvores, qual são variáveis?
- [ ] Por que normalizar antes de treinar certos modelos?
- [ ] O que é broadcasting? Dê um exemplo com dois shapes diferentes.

---

## Seção 1.4 — Pandas

**Notebook:** `notebooks/04_pandas_arvores.ipynb` **Recurso:** Géron cap. 2 completo — siga o projeto da Califórnia e reimplemente cada passo com o dataset de árvores

### Conceitos

- [ ] Series e DataFrame: criação, diferença entre os dois
- [ ] read_csv: carregar o dataset.csv
- [ ] Inspeção: head, tail, info, describe, shape, dtypes
- [ ] Seleção: df['coluna'], loc, iloc
- [ ] Filtragem condicional: df[df['col'] > valor]
- [ ] Valores ausentes: isna, notna, fillna, dropna
- [ ] Duplicatas: duplicated, drop_duplicates
- [ ] Ordenação: sort_values, sort_index
- [ ] Agrupamento: groupby, agg, transform
- [ ] Junções: merge, join, concat
- [ ] apply e map
- [ ] Strings: str accessor
- [ ] Exportar: to_csv, to_numpy, df.values

### Entregas no notebook

- [ ] Carregar dataset.csv com `pd.read_csv` e inspeção completa
- [ ] Quantas árvores por nível de Risco de Queda?
- [ ] Qual espécie tem maior média de Probabilidade de ruptura?
- [ ] Qual a correlação entre Diâmetro Altura do Peito e Probabilidade de ruptura?
- [ ] Criar coluna derivada: `copa_volume_aprox = Largura da Copa * Altura da Copa`
- [ ] Detectar e tratar valores ausentes
- [ ] Exportar DataFrame limpo como `outputs/dataset_limpo.csv`
- [ ] Exportar array NumPy como `outputs/features.npy`
- [ ] Criar função `preprocess(df)` em `src/preprocessor.py`

### Checkpoint

- [ ] Qual a diferença entre `loc` e `iloc`?
- [ ] Quando usar `groupby` em vez de filtrar manualmente?
- [ ] O que retorna `df.describe()` e por que é útil antes de treinar?

---

## Seção 1.5 — Matplotlib e Seaborn

**Notebook:** `notebooks/05_visualizacao_arvores.ipynb` **Recurso:** Géron cap. 2 — seção "Descubra e Visualize os Dados para Obter Informações"

### Conceitos

- [ ] Matplotlib: fig, ax — modelo orientado a objetos
- [ ] plot, scatter, bar, hist, boxplot, imshow
- [ ] Personalização: título, labels, legend, grid, cores
- [ ] Subplots: plt.subplots, gridspec
- [ ] Salvar figuras: savefig, dpi, formatos
- [ ] Seaborn: heatmap, pairplot, violinplot
- [ ] Plotar imagens com anotações (bounding boxes)

### Entregas no notebook

- [ ] Histograma de `Probabilidade de ruptura` separado por nível de risco
- [ ] Boxplot de `Diâmetro Altura do Peito` agrupado por `Risco de Queda`
- [ ] Scatter de `Altura da Árvore` vs `Probabilidade de ruptura` com cor por espécie
- [ ] Heatmap de correlação das 10 principais variáveis numéricas (Seaborn)
- [ ] Barplot das 10 espécies mais frequentes
- [ ] Figura composta `plt.subplots(2, 3)` reunindo todos os gráficos
- [ ] Salvar em `outputs/relatorio_eda.png` com dpi=150

### Checkpoint

- [ ] O que o heatmap revela sobre as variáveis que mais influenciam a probabilidade de ruptura?
- [ ] Por que separar o histograma por nível de risco?
- [ ] Qual variável visual usaria para mostrar uma terceira dimensão num scatter?

---

## Status geral

|Seção|Status|Data de conclusão|
|---|---|---|
|1.1 Python do zero|🟡 em andamento|—|
|1.2 OOP|⬜ não iniciado|—|
|1.3 NumPy|⬜ não iniciado|—|
|1.4 Pandas|⬜ não iniciado|—|
|1.5 Matplotlib + Seaborn|⬜ não iniciado|—|

Atualize para: ⬜ não iniciado / 🟡 em andamento / ✅ concluído

---

## Quando tudo estiver concluído

Substitua este arquivo pelo README.md de portfólio com:

- O que o projeto faz (2–3 frases)
- Quais conceitos foram aplicados por seção
- Principais descobertas nos dados
- Como rodar
- Print da figura composta `outputs/relatorio_eda.png`
