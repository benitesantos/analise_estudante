
<img src = 'https://img1.gratispng.com/20180421/tje/kisspng-education-course-organization-student-university-5adb996b4bd295.3236197915243410993106.jpg' width = '200' height= '150' >

# Análise notas de estudante.
Analise das notas dos alunos de matemática, leitura e redação, e alguns aspectos que influenciaram em sua nota.

## Requisitos:
- Ter o jupyter notebook instalado.
- Ter o arquivo StudentesPerformance.csv na mesma pasta do arquivo
Projeto2-notas_alunos.ipynb


## Pacotes instalados:
- Pandas
``` bash
pip install pandas
```
- Matplotlib
``` bash
pip install matplotlib
```
- Seaborn
``` bash
pip install seaborn
```
### Processo das ferramentas que foram usadas:

Código que importa a tabela em csv e trás para o python.
```python
df = pd.read_csv('StudentsPerformance.csv')
```
Código que vê o tamanho total da tabela , suas linhas e colunas.

``` python
df.shape
```
Mostra as primeiras 5 linhas da tabela.
``` python
df.head()
```

Plota um gráfico com os valores nulos.
```python
nulos = df.isnull()

plt.figure(figsize=(16,5))
plt.title('Analise campos nulos')
sns.heatmap(nulos, cbar=False);
```
Visualiza campos únicos da tabela
``` python
df.nunique()
```
Código que exibe se tem valores duplicados.
```python
df.duplicated().sum()
```
Exibe um resumo estatístico
```python
df.describe()
```
Visualiza o tipo dos dados na tabela e valores nulos.
``` python
df.info()
```
Exibe a tabela filtrada a partir do genero, com a quantidade em porcentagem de homem e mulher que fez a prova.

``` python
df['gender'].value_counts(normalize=True) * 100
```
Exibe a tabela filtrada a partir de grupos, com a quatidade em porcentagem de grupos que fez a prova.
``` python
df['race/ethnicity'].value_counts(normalize=True)*100
```
Exibe a tabela filtrada a partir do grau de escolaridade dos pais , com a quantidade em porcentagem. 

```python
df['parental level of education'].value_counts(normalize=True)*100
```
Exibe a tabela filtrada a partir do almoço, com a quantidade em porcentagem.
```python
df['lunch'].value_counts(normalize=True)*100
```
Exibe a tabela filtrada a partir do teste de preparação , com a quantidade em porcentagem, de quem estudou e se preparou , e o que não estudou.

```python
df['test preparation course'].value_counts(normalize=True)*100
```
Plota um gráfico  das notas dos alunos na prova de matemática, filtrada por genero.
```python
sns.boxplot(data=df,x='math score',y='gender');
```

Plota um gráfico das notas dos alunos na prova de leitura, filtrada por genero.
```python
sns.boxplot(data=df,x='reading score',y='gender');
```
Plota um gráfico das otas dos alunos na prova de redação, filtrada por genero.
```python
sns.boxplot(data=df,x='writing score',y='gender');
```
Mostra um resumo estatistico, filtrado da prova de matematica por genero.

```python
df.groupby(by=['gender']).describe()['math score'].reset_index()
```
 Gráfico que mostra a relação de grupos que influenciam na nota dos alunos na disciplina de matemática.

 ```python
 sns.boxplot(data=df,x='math score',y='race/ethnicity');
 ```
Gráfico que mostra a relação do nivel de escolaridade dos pais que influenciam na nota dos alunos na disciplina de matemática.
```python
sns.boxplot(data=df,x='math score',y='race/ethnicity');
```
Resumo estatístico da relação do nivel de escolaridade dos pais que influenciam na nota dos alunos na disciplina de matemática.
```python
df.groupby(by=['parental level of education']).describe()['math score'].reset_index()
```
Gráfico que mostra a relação da preparação para a prova ou não , que influencia na nota dos alunos na disciplina de matemática.
```python
sns.boxplot(data=df,x = 'math score',y='test preparation course');
```
Resumo estatístico da relação de preparação para a prova ou não , que influencia na nota dos alunos na disciplina de matemática.

```python
df.groupby(by=['test preparation course']).describe()['math score'].reset_index()
```
# Aprendizado:
- Entender mais os filtros que podem ser visualidado. 

# Dificuldade:
- Analisar determinados gráficos.
