<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1b3d,100:3b82f6&height=200&section=header&text=Ant%C3%B4nio%20Neto&fontSize=52&fontColor=ffffff&desc=Banco%20de%20Dados%20%C2%B7%20SQL%20%C2%B7%20Modelagem%20de%20Dados&descSize=18&descAlignY=68" width="100%" alt="Banner Antônio Neto" />

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=20&pause=1200&color=3B82F6&center=true&vCenter=true&width=620&lines=Estudante+de+Tecnologia;Foco+em+Banco+de+Dados+%26+SQL;Modelagem+de+Dados+(DER);Desenvolvimento+Web" alt="Texto animado" />

<br>

[![GitHub](https://img.shields.io/badge/GitHub-diasantonio--dotcom-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/diasantonio-dotcom)
<!-- Para adicionar LinkedIn, apague as setas desta linha e a da linha de baixo e troque SEU-USUARIO:
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/SEU-USUARIO)
-->
<!-- Para adicionar e-mail, use esta linha:
[![E-mail](https://img.shields.io/badge/E--mail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:SEU-EMAIL)
-->

</div>

---

## 🎯 Objetivo

Buscando **estágio ou vaga júnior** em **Banco de Dados, Análise de Dados ou Desenvolvimento Back-end**, aplicando modelagem e SQL em problemas reais.

## 👨‍💻 Sobre mim

Sou estudante de Tecnologia e gosto de ver um sistema nascer pelos dados. Meu processo é: **entender o problema → desenhar o DER → normalizar → criar o banco → escrever as consultas** que respondem às perguntas do negócio. Também construo interfaces web com HTML e CSS.

| 🗄️ Banco de Dados | 📐 Modelagem | 🌐 Web |
|:---:|:---:|:---:|
| Tabelas, chaves, restrições, `JOIN`, agregações e views | Modelo conceitual e lógico, DER e normalização | Páginas e interfaces com HTML e CSS |

## 🛠️ Tecnologias

<p align="center">
  <img src="https://skillicons.dev/icons?i=postgres,html,css,git,github&theme=dark" alt="Tecnologias" />
</p>

## 📐 Modelagem de dados

> Exemplo de DER (modelo entidade-relacionamento) de uma loja, normalizado até a 3FN.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#0f2a5c','primaryTextColor':'#e6edf3','primaryBorderColor':'#3b82f6','lineColor':'#3b82f6','secondaryColor':'#0b1f45','tertiaryColor':'#0d1117','attributeBackgroundColorOdd':'#0f2a5c','attributeBackgroundColorEven':'#0b1f45','fontFamily':'Segoe UI, sans-serif','fontSize':'14px'}}}%%
erDiagram
    direction LR
    CLIENTE ||--o{ PEDIDO : realiza
    PEDIDO ||--|{ ITEM_PEDIDO : contém
    PRODUTO ||--o{ ITEM_PEDIDO : compõe

    CLIENTE {
        int id PK
        string nome
        string email
    }
    PEDIDO {
        int id PK
        int cliente_id FK
        date data
    }
    ITEM_PEDIDO {
        int pedido_id FK
        int produto_id FK
        int quantidade
    }
    PRODUTO {
        int id PK
        string nome
        decimal preco
    }
```

## 🔍 Consultas SQL

> Ranking dos 5 melhores clientes dos últimos 30 dias, com participação no faturamento total.

```sql
WITH faturamento_cliente AS (
    SELECT  c.id,
            c.nome,
            COUNT(DISTINCT p.id)          AS total_pedidos,
            SUM(i.quantidade * pr.preco)  AS faturamento
    FROM        cliente     c
    INNER JOIN  pedido      p  ON p.cliente_id = c.id
    INNER JOIN  item_pedido i  ON i.pedido_id  = p.id
    INNER JOIN  produto     pr ON pr.id        = i.produto_id
    WHERE   p.data >= CURRENT_DATE - INTERVAL '30 days'
    GROUP BY c.id, c.nome
)
SELECT  RANK() OVER (ORDER BY faturamento DESC)               AS posicao,
        nome,
        total_pedidos,
        ROUND(faturamento, 2)                                 AS faturamento,
        ROUND(100 * faturamento / SUM(faturamento) OVER (), 1) AS pct_do_total
FROM    faturamento_cliente
ORDER BY posicao
LIMIT 5;
```

**Resultado** (dados fictícios):

| posição | nome | total_pedidos | faturamento | pct_do_total |
|:---:|---|:---:|---:|:---:|
| 1 | Maria Souza | 12 | 4.820,00 | 23,4 |
| 2 | João Lima | 9 | 3.150,50 | 15,3 |
| 3 | Ana Costa | 7 | 2.740,00 | 13,3 |
| 4 | Pedro Alves | 5 | 1.980,90 | 9,6 |
| 5 | Carla Dias | 4 | 1.455,00 | 7,1 |

<details>
<summary><b>O que essa consulta usa</b></summary>

- **CTE (`WITH`)** para organizar a consulta em etapas
- **`JOIN` entre 4 tabelas** seguindo o modelo acima
- **Agregações** com `COUNT`, `SUM` e `GROUP BY`
- **Funções de janela** com `RANK()` e `SUM() OVER ()`
- **Filtro por período** com `CURRENT_DATE` e `INTERVAL`

</details>

## 📊 GitHub em números

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=diasantonio-dotcom&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117" height="165" alt="Estatísticas" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=diasantonio-dotcom&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117" height="165" alt="Linguagens" />
</p>

<!--
PROJETOS EM DESTAQUE: quando quiser mostrar um projeto, apague as setas deste bloco
e troque NOME-DO-REPO pelo nome exato do repositório:

## 🗂️ Projetos em destaque

<a href="https://github.com/diasantonio-dotcom/NOME-DO-REPO">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=diasantonio-dotcom&repo=NOME-DO-REPO&theme=tokyonight&hide_border=true&bg_color=0d1117" />
</a>
-->

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:3b82f6,100:0d1b3d&height=100&section=footer" width="100%" alt="" />
