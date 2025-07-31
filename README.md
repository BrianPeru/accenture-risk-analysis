# Análise de Risco de Mercado - Accenture RiskControl

Este projeto visa demonstrar a criação de um pipeline básico para análise de risco de mercado, utilizando dados de ativos financeiros negociados no Brasil. Este trabalho foi desenvolvido como parte do processo seletivo para a vaga de estágio em RiskControl na Accenture.

## Objetivo do Projeto

O principal objetivo deste projeto é desenvolver um pipeline funcional para:
* Coletar dados históricos de ativos financeiros brasileiros.
* Calcular indicadores de risco de mercado essenciais, como Volatilidade Histórica Anualizada, Valor em Risco (VaR) paramétrico e Correlação entre ativos.
* Apresentar e visualizar os resultados de forma clara e interativa.

## Ferramentas Utilizadas

As seguintes linguagens e bibliotecas foram utilizadas no desenvolvimento deste projeto:

* **Linguagem de Programação:** Python.
* **Bibliotecas Python:**
    * `pandas`: Para manipulação e análise de dados.
    * `numpy`: Para operações numéricas e matemáticas.
    * `scipy`: Para funções estatísticas, especialmente para o cálculo do VaR.
    * `yfinance`: Para coleta de dados históricos do Yahoo Finance.
    * `matplotlib` e `seaborn`: Para visualização estática de dados.
    * `jupyter`: Para desenvolvimento e apresentação do notebook interativo.

## Como Executar o Projeto

Para replicar e executar este projeto em seu ambiente local, siga os passos abaixo:

1.  **Clonar o Repositório:**
    ```bash
    git clone [https://github.com/BrianPeru/accenture-risk-analysis.git](https://github.com/BrianPeru/accenture-risk-analysis.git)
    cd accenture-risk-analysis
    ```
2.  **Configurar o Ambiente Virtual (recomendado):**
    É altamente recomendável criar um ambiente virtual para isolar as dependências do projeto.
    ```bash
    python -m venv .venv
    # Ativar o ambiente virtual (Windows PowerShell):
    # .venv\Scripts\Activate.ps1
    # Ativar o ambiente virtual (Linux/macOS ou WSL Bash):
    source .venv/bin/activate
    ```
3.  **Instalar as Dependências:**
    Com o ambiente virtual ativado, instale todas as bibliotecas necessárias usando o arquivo `requirements.txt`:
    ```bash
    pip install -r requirements.txt
    ```
4.  **Executar o Jupyter Notebook:**
    Após a instalação das dependências, inicie o Jupyter Notebook ou abra o arquivo `.ipynb` diretamente no VS Code:
    ```bash
    jupyter notebook
    ```
    (Alternativamente, abra o arquivo `analise_risco_mercado.ipynb` no VS Code e execute as células.)

## Explicações dos Cálculos

Nesta seção, serão detalhadas as fórmulas e os métodos utilizados para calcular os indicadores de risco. (Esta seção será preenchida conforme o desenvolvimento do código no Jupyter Notebook.)

### Volatilidade Histórica Anualizada
* **Definição:** Mede a dispersão dos retornos de um ativo em um determinado período.
* **Cálculo:** Baseia-se no desvio padrão dos retornos diários. Para anualizar, o desvio padrão diário é multiplicado pela raiz quadrada do número de dias úteis em um ano (tipicamente 252 para o mercado brasileiro).
    $$\text{Volatilidade Anualizada} = \sigma_{\text{diário}} \times \sqrt{252}$$

### Valor em Risco (VaR) Paramétrico a 95%
* **Definição:** Estima a perda máxima esperada de um investimento em um determinado horizonte de tempo e com um dado nível de confiança, assumindo uma distribuição normal dos retornos.
* **Cálculo:** Para um VaR a 95%, e assumindo retornos com distribuição normal, utilizamos a média dos retornos ($\mu$) e o desvio padrão dos retornos ($\sigma$), juntamente com o Z-score correspondente ao percentil 5% (ou 95% na cauda superior, dependendo da convenção).
    $$\text{VaR}_{95\%} = \text{Retorno Médio} - (Z_{0.05} \times \text{Desvio Padrão})$$
    Onde $Z_{0.05}$ é o valor crítico da distribuição normal padrão para um nível de confiança de 95% (percentil 5%).

### Correlação entre Ativos
* **Definição:** Mede a força e a direção da relação linear entre os retornos de dois ativos. Varia de -1 (correlação negativa perfeita) a +1 (correlação positiva perfeita).
* **Cálculo:** Será utilizada a função de correlação de bibliotecas como `pandas` ou `numpy` sobre os retornos diários dos ativos.