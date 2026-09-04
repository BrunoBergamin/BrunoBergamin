<h1 align="center">Bruno Alves Bergamin</h1>

<p align="center">
  <b>Desenvolvedor back-end:</b> Java · Spring Boot · PostgreSQL · Kafka<br/>
  Também construo produtos web completos: e-commerce, sistemas de gestão e integrações de pagamento, fiscais e logísticas.<br/>
  📍 Boituva · São Paulo · Brasil · disponível para trabalho.
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/bruno-alves-bergamin-6b711a347/">
    <img src="https://img.shields.io/badge/LinkedIn-Bruno%20Alves%20Bergamin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="https://flabeauty.com.br">
    <img src="https://img.shields.io/badge/Em%20produção-FlaBeauty-E11D74?style=for-the-badge&logo=vercel&logoColor=white" alt="FlaBeauty ao vivo"/>
  </a>
</p>

---

## ☕ OrderFlow, sistema de pedidos em Java

Três serviços que formam **um sistema**, não três exercícios soltos.

Trabalho com operação de e-commerce. Os problemas que escolhi resolver aqui são os que eu já
vi acontecer: pedido duplicado, estoque vendido duas vezes, repasse de maquininha que não bate.

| Serviço | O que faz | O problema que resolve |
|---|---|---|
| **[orderflow](https://github.com/BrunoBergamin/orderflow)** | API de pedidos | Cliente clica duas vezes em comprar; duas pessoas disputam a última unidade; o pedido salva mas o evento não sai |
| **[orderflow-fulfillment](https://github.com/BrunoBergamin/orderflow-fulfillment)** | Consumidor dos eventos | A mesma mensagem chega duas vezes; uma mensagem quebrada trava a fila inteira; o parceiro externo cai |
| **[orderflow-reconciliation](https://github.com/BrunoBergamin/orderflow-reconciliation)** | Conciliação financeira em lote | O repasse do adquirente não bate com as vendas, inclusive taxa cobrada acima da contratada |

Como foi construído:

- Arquitetura hexagonal verificada por **ArchUnit**. Se alguém importar JPA dentro da regra de
  negócio, o build quebra.
- **179 testes** no CI, com PostgreSQL, Redis e Kafka de verdade via Testcontainers. Nada de
  banco em memória.
- Transactional Outbox, idempotência, lock otimista, DLQ com reprocessamento, circuit breaker
  e rate limiting.
- Imagens publicadas no GHCR, então roda com um comando, sem compilar.

Cada README explica **por que** cada decisão foi tomada, não só o que foi usado.

---

## 🚀 FlaBeauty, e-commerce em produção

**Loja de moda feminina no ar**, do catálogo ao pós-venda, com automação fiscal, logística e
financeira. É onde os problemas acima deixaram de ser teoria.

### 🔗 Site no ar: **[flabeauty.com.br](https://flabeauty.com.br)**

**Base técnica:** Next.js 15 · React 19 · TypeScript · Tailwind v4 · Supabase (PostgreSQL ·
Auth · Storage · RLS) · Vercel

**Integrações e automações:** pagamentos com Mercado Pago (Pix, cartão e boleto) com webhooks
assinados (HMAC e anti-replay), emissão fiscal, cálculo de frete e painel administrativo com
controle de estoque.

---

## 📦 Outros projetos

| Projeto | O que é | Stack |
|---|---|---|
| **[conveniencia-vendas](https://github.com/BrunoBergamin/conveniencia-vendas)** | Sistema de vendas em **microsserviços**: banco por serviço, JWT, Kubernetes | Java · Spring Boot · Quarkus |
| **gestao-fiscal-postos** 🔒 | Suíte desktop de **gestão fiscal e financeira** de uma rede de postos: consulta de NF-e, conferência de pagamentos (SGA x Sicoob/PagBank/Sipag/PIX), análise de descontos em PDF, clientes a prazo e estoque inteligente | Python · PySide6 · SQL · lxml |
| **[camaragest](https://github.com/BrunoBergamin/camaragest)** | Plataforma de gestão para **câmaras municipais** (demo interativa) | HTML · CSS · JS |
| **[ponto-cego](https://github.com/BrunoBergamin/ponto-cego)** | Diagnóstico interativo com **hero 3D em WebGL** | JavaScript · WebGL |
| **[analise-digital-boituva](https://github.com/BrunoBergamin/analise-digital-boituva)** | **Auditorias digitais** independentes de sites e presença online | HTML · Análise técnica |

Também desenvolvo **sites e redesigns para empresas** (imobiliárias, indústria e comércio
local), com foco em SEO local e Google Meu Negócio.

---

## 🛠️ Tecnologias

<p>
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java"/>
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Quarkus-4695EB?style=for-the-badge&logo=quarkus&logoColor=white" alt="Quarkus"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Apache_Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" alt="Kafka"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis"/>
</p>
<p>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions"/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git"/>
</p>
<p>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase"/>
</p>

---

## 📫 Contato

- 💼 **LinkedIn:** [Bruno Alves Bergamin](https://www.linkedin.com/in/bruno-alves-bergamin-6b711a347/)
- 🌐 **Projeto ao vivo:** [flabeauty.com.br](https://flabeauty.com.br)
- 📍 Boituva / SP · **procurando vaga como desenvolvedor back-end Java**, em Florianópolis ou remoto
