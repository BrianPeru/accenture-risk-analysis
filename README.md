\section*{Análise de Risco de Mercado - Accenture RiskControl}

Este projeto visa demonstrar a criação de um pipeline básico para análise de risco de mercado, utilizando dados de ativos financeiros negociados no Brasil. Este trabalho foi desenvolvido como parte do processo seletivo para a vaga de estágio em RiskControl na Accenture.

\subsection*{Objetivo do Projeto}

O principal objetivo deste projeto é desenvolver um pipeline funcional para:
\begin{itemize}
    \item Coletar dados históricos de ativos financeiros brasileiros.
    \item Calcular indicadores de risco de mercado essenciais, como Volatilidade Histórica Anualizada, Valor em Risco (VaR) paramétrico e Correlação entre ativos.
    \item Apresentar e visualizar os resultados de forma clara e interativa.
\end{itemize}

\subsection*{Ferramentas Utilizadas}

As seguintes linguagens e bibliotecas foram utilizadas no desenvolvimento deste projeto:

\begin{itemize}
    \item \textbf{Linguagem de Programação:} Python
    \item \textbf{Bibliotecas Python:}
    \begin{itemize}
        \item \texttt{pandas}: Para manipulação e análise de dados.
        \item \texttt{numpy}: Para operações numéricas e matemáticas.
        \item \texttt{scipy}: Para funções estatísticas, especialmente para o cálculo do VaR.
        \item \texttt{yfinance}: Para coleta de dados históricos do Yahoo Finance.
        \item \texttt{matplotlib} e \texttt{seaborn}: Para visualização estática de dados.
        \item \texttt{jupyter}: Para desenvolvimento e apresentação do notebook interativo.
    \end{itemize}
\end{itemize}

\subsection*{Como Executar o Projeto}

Para replicar e executar este projeto em seu ambiente local, siga os passos abaixo:

\begin{enumerate}
    \item \textbf{Clonar o Repositório:}
    \begin{verbatim}
git clone [https://github.com/BrianPeru/accenture-risk-analysis.git](https://github.com/BrianPeru/accenture-risk-analysis.git)
cd accenture-risk-analysis
    \end{verbatim}
    \item \textbf{Configurar o Ambiente Virtual (recomendado):}
    É altamente recomendável criar um ambiente virtual para isolar as dependências do projeto.
    \begin{verbatim}
python -m venv .venv
# Ativar o ambiente virtual (Windows PowerShell):
# .venv\Scripts\Activate.ps1
# Ativar o ambiente virtual (Linux/macOS ou WSL Bash):
source .venv/bin/activate
    \end{verbatim}
    \item \textbf{Instalar as Dependências:}
    Com o ambiente virtual ativado, instale todas as bibliotecas necessárias usando o arquivo \texttt{requirements.txt}:
    \begin{verbatim}
pip install -r requirements.txt
    \end{verbatim}
    \item \textbf{Executar o Jupyter Notebook:}
    Após a instalação das dependências, inicie o Jupyter Notebook ou abra o arquivo \texttt{.ipynb} diretamente no VS Code:
    \begin{verbatim}
jupyter notebook
    \end{verbatim}
    (Alternativamente, abra o arquivo \texttt{analise\_risco\_mercado.ipynb} no VS Code e execute as células.)
\end{enumerate}

\subsection*{Explicações dos Cálculos}

Nesta seção, serão detalhadas as fórmulas e os métodos utilizados para calcular os indicadores de risco. (Esta seção será preenchida conforme o desenvolvimento do código no Jupyter Notebook.)

\subsubsection*{Volatilidade Histórica Anualizada}
\begin{itemize}
    \item \textbf{Definição:} Mede a dispersão dos retornos de um ativo em um determinado período.
    \item \textbf{Cálculo:} Baseia-se no desvio padrão dos retornos diários. Para anualizar, o desvio padrão diário é multiplicado pela raiz quadrada do número de dias úteis em um ano (tipicamente 252 para o mercado brasileiro).
    $$ \text{Volatilidade Anualizada} = \sigma_{\text{diário}} \times \sqrt{252} $$
\end{itemize}

\subsubsection*{Valor em Risco (VaR) Paramétrico a 95\%}
\begin{itemize}
    \item \textbf{Definição:} Estima a perda máxima esperada de um investimento em um determinado horizonte de tempo e com um dado nível de confiança, assumindo uma distribuição normal dos retornos.
    \item \textbf{Cálculo:} Para um VaR a 95\%, e assumindo retornos com distribuição normal, utilizamos a média dos retornos ($\mu$) e o desvio padrão dos retornos ($\sigma$), juntamente com o Z-score correspondente ao percentil 5\% (ou 95\% na cauda superior, dependendo da convenção).
    $$ \text{VaR}_{95\%} = \text{Retorno Médio} - (Z_{0.05} \times \text{Desvio Padrão}) $$
    Onde $Z_{0.05}$ é o valor crítico da distribuição normal padrão para um nível de confiança de 95\% (percentil 5%).
\end{itemize}

\subsubsection*{Correlação entre Ativos}
\begin{itemize}
    \item \textbf{Definição:} Mede a força e a direção da relação linear entre os retornos de dois ativos. Varia de -1 (correlação negativa perfeita) a +1 (correlação positiva perfeita).
    \item \textbf{Cálculo:} Será utilizada a função de correlação de bibliotecas como \texttt{pandas} ou \texttt{numpy} sobre os retornos diários dos ativos.
\end{itemize}