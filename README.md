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

## 📐 Como eu modelo dados

Exemplo de DER (loja com clientes, pedidos e produtos):

```mermaid
erDiagram
    CLIENTE ||--o{ PEDIDO : realiza
    PEDIDO ||--|{ ITEM_PEDIDO : contem
    PRODUTO ||--o{ ITEM_PEDIDO : compoe

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
    PRODUTO {
        int id PK
        string nome
        decimal preco
    }
    ITEM_PEDIDO {
        int pedido_id FK
        int produto_id FK
        int quantidade
    }
```

## 🔍 Como eu escrevo SQL

```sql
-- Top 5 clientes por faturamento nos últimos 30 dias
SELECT c.nome,
       COUNT(DISTINCT p.id)              AS total_pedidos,
       SUM(i.quantidade * pr.preco)      AS faturamento
FROM   cliente c
JOIN   pedido p        ON p.cliente_id = c.id
JOIN   item_pedido i   ON i.pedido_id  = p.id
JOIN   produto pr      ON pr.id        = i.produto_id
WHERE  p.data >= CURRENT_DATE - INTERVAL '30 days'
GROUP  BY c.nome
ORDER  BY faturamento DESC
LIMIT  5;
```

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
