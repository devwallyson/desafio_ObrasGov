# Análise de Projetos de Investimento no DF - ObrasGov.br

**Autor:** Wallyson Souza
**Data:** 17 de Outubro de 2025

## 1. Visão Geral

Este projeto consiste em um pipeline completo de análise de dados, desenvolvido como parte de um desafio técnico. O objetivo é extrair dados de projetos de investimento do Distrito Federal da API ObrasGov.br, realizar um processo de tratamento e limpeza (Transformação), carregar os dados em um banco de dados relacional (Carga) e, por fim, realizar uma análise quantitativa e qualitativa para extrair insights.

O notebook `obrasgov_analise.ipynb` contém todo o processo documentado, desde a extração até as conclusões finais.

## 2. Etapas do Projeto

O projeto foi estruturado seguindo um fluxo de trabalho padrão de análise de dados:

1.  **Extração de Dados:** Conexão com a API do ObrasGov.br para extrair todos os registros de projetos de investimento para o Distrito Federal (DF). O código inclui uma lógica para salvar os dados brutos localmente, evitando chamadas excessivas à API.

2.  **Tratamento e Limpeza (Transformação):**
    * Seleção das colunas mais relevantes para a análise.
    * Padronização dos nomes das colunas para o formato `snake_case`.
    * Correção dos tipos de dados (strings para `datetime` e `numeric`).
    * Tratamento de dados complexos, como listas e dicionários aninhados em formato de texto, que foram simplificados.
    * Criação de uma nova coluna (`categoria_social`) através da categorização de textos longos para viabilizar a análise.
    * Tratamento de valores ausentes.

3.  **Armazenamento (Carga):** Os dados limpos e tratados foram carregados em um banco de dados **SQLite**, contido no arquivo `dados/obras_gov_df.db`.

4.  **Análise e Visualização:** Foram gerados gráficos para responder a perguntas-chave, como:
    * Qual a distribuição dos projetos por situação?
    * Onde os investimentos estão sendo focados (por categoria social)?
    * Como o número de novos projetos evoluiu ao longo dos anos?

5.  **Análise Qualitativa e Conclusão:** Interpretação dos gráficos para identificar padrões, formular hipóteses e apresentar os principais insights do projeto.

## 3. Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * `pandas` para manipulação e análise de dados.
    * `requests` para consumo da API.
    * `matplotlib` e `seaborn` para visualização de dados.
    * `sqlite3` para interação com o banco de dados.
* **Ambiente:** Jupyter Notebook

## 4. Como Executar o Projeto

Siga os passos abaixo para configurar e executar o projeto localmente.

### Pré-requisitos
* Git
* Python 3.8 ou superior

### Passos

1.  **Clone o repositório:**
    ```bash
    git clone git@github.com:devwallyson/desafio_ObrasGov.git
    ```

2.  **Navegue até a pasta do projeto:**
    ```bash
    cd desafio_obrasGov
    ```

3.  **Crie e ative um ambiente virtual:**
    * No Windows:
        ```bash
        python -m venv venv
        .\venv\Scripts\activate
        ```
    * No macOS / Linux:
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```

4.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

5.  **Inicie o Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```

6.  Abra o arquivo `obrasgov_analise.ipynb` e execute as células. Recomenda-se usar a opção "Restart & Run All" para garantir a execução na ordem correta.
