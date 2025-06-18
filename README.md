# Analise-com-SQL-no-Metabase

https://dncgroupbr.notion.site/Desafio-Gere-planos-de-a-o-a-partir-de-an-lises-com-SQL-b1d2722500654bceba2944c6a7b22995

# Análise de Leads para EdTech: Insights e Planos de Ação com SQL

Este repositório documenta um projeto de análise de dados focado em otimizar a estratégia de aquisição de clientes para uma empresa EdTech. [cite\_start]Utilizando **SQL** para manipulação e consulta de dados, foi construído um dashboard no **Metabase** para visualizar o funil de leads e gerar insights acionáveis. [cite: 1]

## 📝 Sumário

  * [Visão Geral do Projeto](https://www.google.com/search?q=%231-vis%C3%A3o-geral-do-projeto)
  * [Dashboard Final](https://www.google.com/search?q=%232-dashboard-final)
  * [Análises e Descobertas](https://www.google.com/search?q=%233-an%C3%A1lises-e-descobertas)
  * [Planos de Ação Estratégicos](https://www.google.com/search?q=%234-planos-de-a%C3%A7%C3%A3o-estrat%C3%A9gicos)
  * [Ferramentas e Queries](https://www.google.com/search?q=%235-ferramentas-e-queries)
  * [Autor](https://www.google.com/search?q=%236-autor)

-----

### 1\. Visão Geral do Projeto

O desafio central deste projeto foi analisar a base de dados de leads de uma EdTech para identificar padrões de aquisição e comportamento. [cite\_start]O objetivo era transformar esses dados brutos em inteligência de negócio, permitindo à empresa tomar decisões estratégicas para impulsionar o crescimento de sua base de usuários. [cite: 1]

### 2\. Dashboard Final

O resultado do projeto foi consolidado em um dashboard abrangente no Metabase, que apresenta os principais indicadores de performance (KPIs) do funil de aquisição de leads.

[cite\_start]*(Print do dashboard completo apresentado no projeto) [cite: 4]*

-----

### 3\. Análises e Descobertas

Cada componente do dashboard foi criado para responder a uma pergunta de negócio específica, revelando um aspecto diferente do comportamento dos leads.

#### Análise 1: Perfil Demográfico por Gênero

  * **Objetivo:** Entender a distribuição de gênero na base de leads.
  * [cite\_start]**Descoberta:** A base é majoritariamente feminina, com **55,3% de mulheres** contra 44,7% de homens. [cite: 6]
  * **Visualização:**
    [cite\_start] [cite: 6]

#### Análise 2: Média de Idade

  * **Objetivo:** Identificar a faixa etária central dos leads.
  * [cite\_start]**Descoberta:** A idade média dos leads é de **22 anos**, indicando um público jovem, provavelmente em transição de carreira ou recém-formado. [cite: 9]
  * **Visualização:**
    [cite\_start] [cite: 9]

#### Análise 3: Formação Acadêmica

  * **Objetivo:** Mapear o nível de escolaridade mais comum entre os leads.
  * [cite\_start]**Descoberta:** Há uma grande concentração de leads com formação **"B.Tech"** e que estão **"Procurando Emprego"** ("Looking for Job"). [cite: 11]
  * **Visualização:**
    [cite\_start] [cite: 11]

#### Análise 4: Engajamento com Demos por Idioma

  * **Objetivo:** Medir a eficácia do conteúdo de demonstração em diferentes idiomas.
  * [cite\_start]**Descoberta:** As demos em **Inglês** possuem a maior taxa média de visualização (82%), seguidas por Telugu (76%) e Hindi (69%). [cite: 14]
  * **Visualização:**
    [cite\_start] [cite: 14]

#### Análise 5: Volume de Ligações por Plataforma

  * **Objetivo:** Comparar a performance dos canais de aquisição na geração de contatos efetivos ao longo do tempo.
  * [cite\_start]**Descoberta:** **Referências de usuários** ("user\_referrals") e o **website** foram os canais com os maiores picos de ligações atendidas, especialmente em janeiro. [cite: 18]
  * **Visualização:**
    [cite\_start] [cite: 18]

-----

### 4\. Planos de Ação Estratégicos

Com base nas descobertas, foram propostos os seguintes planos de ação:

1.  **Marketing Direcionado:**

      * [cite\_start]**Insight:** O perfil predominante é de mulheres jovens (22 anos) [cite: 6, 9][cite\_start], com formação em tecnologia ("B.Tech") ou em busca de emprego[cite: 11].
      * **Ação:** Criar campanhas de marketing digital e conteúdo de redes sociais com linguagem e apelo visual direcionados a este público. Desenvolver parcerias com grupos universitários e de tecnologia focados no público feminino.

2.  **Otimização de Conteúdo:**

      * [cite\_start]**Insight:** A demo em Inglês tem o melhor desempenho, enquanto a em Hindi tem a menor taxa de engajamento (69%)[cite: 14].
      * **Ação:** Realizar uma auditoria de qualidade na demo em Hindi para identificar possíveis melhorias no conteúdo ou na tradução. Promover mais ativamente a demo em Inglês, que já prova ser altamente eficaz.

3.  **Alocação de Investimento em Canais:**

      * [cite\_start]**Insight:** Referências de usuários e o tráfego direto do site são as fontes mais fortes de leads contatados com sucesso[cite: 18].
      * **Ação:** Implementar um programa de incentivos para fortalecer as referências de usuários ("member-get-member"). Aumentar o investimento em SEO e otimização da experiência do usuário (UX) no website para capitalizar sobre a performance do canal.

### 5\. Ferramentas e Queries

  * **Ferramentas:** `SQL`, `Metabase`

  * **Queries Utilizadas:**

    \<details\>
    \<summary\>Clique para ver as queries SQL\</summary\>

    **Gráfico 1 - Pizza (Gênero):**

    ```sql
    SELECT gender, COUNT(lead_id)
    FROM leads_basic_details
    GROUP BY gender;
    ```

    [cite\_start][cite: 6]

    **Gráfico 2 - Cartão (Média de Idade):**

    ```sql
    SELECT SUM(AGE) / COUNT(lead_id) AS MEDIA_IDADE
    FROM leads_basic_details;
    ```

    [cite\_start][cite: 9]

    **Gráfico 3 - Barras (Formação):**

    ```sql
    SELECT current_education, COUNT(current_education)
    FROM leads_basic_details
    GROUP BY current_education
    ORDER BY current_education;
    ```

    [cite\_start][cite: 11]

    **Gráfico 4 - Tabela (Engajamento por Idioma):**

    ```sql
    SELECT 
        language,
        AVG(watched_percentage) AS media_watched
    FROM 
        leads_demo_watched_details
    WHERE 
        watched_percentage > 0.5
    GROUP BY 
        language;
    ```

    [cite\_start][cite: 13]

    **Gráfico 5 - Linhas (Ligações por Plataforma):**

    ```sql
    SELECT
        `leads_basic_details`.`lead_gen_source` AS `lead_gen_source`,
        STR_TO_DATE(CONCAT(YEARWEEK(`Leads Interaction Details - Lead`.`call_done_date`), ' Sunday'), '%X%V %W') AS `Leads Interaction Details - Lead__call_done_date`,
        COUNT(*) AS `count`
    FROM `leads_basic_details`
    LEFT JOIN `leads_interaction_details` AS `Leads Interaction Details - Lead`
        ON `leads_basic_details`.`lead_id` = `Leads Interaction Details - Lead`.`lead_id`
    GROUP BY
        `leads_basic_details`.`lead_gen_source`,
        STR_TO_DATE(CONCAT(YEARWEEK(`Leads Interaction Details - Lead`.`call_done_date`), ' Sunday'), '%X%V %W')
    ORDER BY
        `leads_basic_details`.`lead_gen_source` ASC,
        STR_TO_DATE(CONCAT(YEARWEEK(`Leads Interaction Details - Lead`.`call_done_date`), ' Sunday'), '%X%V %W') ASC;
    ```

    [cite\_start][cite: 16, 17]

    \</details\>

### 6\. Autor

  * **Jonathan**
