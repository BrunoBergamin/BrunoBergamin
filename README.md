<h1 align="center">Bruno Alves Bergamin</h1>

<p align="center">
  <b>Desenvolvedor back-end Java</b> · Spring Boot · PostgreSQL · Kafka · Docker<br/>
  Construo sistemas para operação de verdade: pedidos, estoque, caixa, conciliação financeira e fiscal.<br/>
  📍 Boituva · São Paulo · Brasil · disponível para trabalho.
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/bruno-alves-bergamin-6b711a347/">
    <img src="https://img.shields.io/badge/LinkedIn-Bruno%20Alves%20Bergamin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="https://github.com/BrunoBergamin/orderflow">
    <img src="https://img.shields.io/badge/Projeto%20principal-OrderFlow-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="OrderFlow"/>
  </a>
  <a href="https://flabeauty.com.br">
    <img src="https://img.shields.io/badge/Em%20produção-FlaBeauty-E11D74?style=for-the-badge&logo=vercel&logoColor=white" alt="FlaBeauty ao vivo"/>
  </a>
</p>

---

## ☕ Projetos Java

### OrderFlow · pedidos, pós-venda e conciliação orientados a eventos

**[orderflow](https://github.com/BrunoBergamin/orderflow)** · Java 21 · Spring Boot 3.5 · Kafka · PostgreSQL · Redis · Spring Batch

Três serviços que formam **um sistema**, não três exercícios soltos. Trabalho com operação de
e-commerce, e os problemas que escolhi resolver aqui são os que eu já vi acontecer.

| Serviço | O problema que resolve |
|---|---|
| **[API de pedidos](https://github.com/BrunoBergamin/orderflow/tree/main/api)** | Cliente clica duas vezes em comprar; duas pessoas disputam a última unidade; o pedido salva mas o evento não sai |
| **[Fulfillment](https://github.com/BrunoBergamin/orderflow/tree/main/fulfillment)** | A mesma mensagem chega duas vezes; uma mensagem quebrada trava a fila inteira; o parceiro externo cai |
| **[Reconciliation](https://github.com/BrunoBergamin/orderflow/tree/main/reconciliation)** | O repasse da maquininha não bate com as vendas, inclusive taxa cobrada acima da contratada |

- Arquitetura hexagonal verificada por **ArchUnit**: importar JPA dentro da regra de negócio quebra o build.
- **184 testes**, com PostgreSQL e Redis de verdade via Testcontainers. Um deles põe 20 threads
  disputando 5 unidades de estoque.
- Transactional Outbox, idempotência, lock otimista, DLQ com reprocessamento, circuit breaker e
  rate limiting.
- Imagens publicadas no GHCR: um `docker compose up -d` sobe os três, sem compilar nada.

### Lumi · assistente financeira por voz com Spring AI

**[desafio-dio-spring-ai-budgeting](https://github.com/BrunoBergamin/desafio-dio-spring-ai-budgeting)** · Java 25 · Spring Boot 4.1 · Spring AI 2.0 · Spring Security 7 · React 19

Você fala "gastei 85 reais no mercado": o áudio vira texto, o modelo escolhe uma ferramenta
(**Tool Calling**), o service grava no banco, confere o orçamento do mês e a Lumi responde.
Funciona pelo site e pelo **WhatsApp**.

- O usuário chega à ferramenta pelo `ToolContext`, fora do JSON Schema: o modelo **não consegue**
  escolher de quem são os dados, e um teste prova isso.
- O REST e a IA passam pelo **mesmo service, com as mesmas regras**. A IA nunca toca no banco.
- 119 testes, mais 9 de ponta a ponta com IA real. JWT, Flyway, Docker em um comando e custo zero
  para rodar.

### Motor de checkout com 12 padrões de projeto

**[lab-padroes-projeto](https://github.com/BrunoBergamin/lab-padroes-projeto)** · Java 21 · Spring Boot 3.5 · JPA · Swagger

O mesmo motor escrito **duas vezes**: em Java puro, montando a corrente e o barramento de eventos
na mão, e em Spring Boot, onde o framework faz metade do trabalho. Comparar os dois é o ponto:
o padrão não some com o Spring, só muda de forma.

Strategy, Chain of Responsibility, Decorator, State, Observer, Facade, Factory Method, Builder,
Template Method, Adapter, Proxy e Singleton, cada um resolvendo um problema real do checkout.
62 testes, e cada um diz no nome qual padrão está exercitando.

### Conveniência Vendas · microsserviços com Spring Boot e Quarkus

**[conveniencia-vendas](https://github.com/BrunoBergamin/conveniencia-vendas)** · Java 21 · Spring Boot 3.3 · Quarkus 3.15 · PostgreSQL · Kubernetes · React

Dois serviços com stacks diferentes de propósito, cada um dono do próprio banco. A venda valida e
baixa o estoque no outro serviço com **idempotência e saga com compensação**: se algo falha no
meio, a baixa é estornada. JWT compartilhado, fault tolerance e manifests para Kubernetes.

---

## 🏭 Java em produção e em construção

Sistemas de clientes reais, por isso o código é privado.

| Projeto | O que faz | Stack | Situação |
|---|---|---|---|
| **controle-estoque-postos** 🔒 | Monitor de estoque de uma rede de postos. Lê o ERP em modo somente leitura, gera todo dia uma contagem às cegas com rodízio por loja, manda o link ao gerente pelo WhatsApp, confere o resultado e audita o kardex a cada 5 minutos: movimento apagado, alterado ou lançado com data retroativa | Java 21 · Spring Boot 4.1 · JPA · Flyway · PostgreSQL · React | Em uso |
| **pdv-conveniencia** 🔒 | Frente de caixa para substituir o sistema de uma loja de conveniência: venda com pagamento múltiplo, caixa com sangria e conferência de fechamento, estoque com kardex. Próximos passos: NFC-e direto na SEFAZ e conciliação das maquininhas | Java 21 · Spring Boot 3.3 · MySQL · Flyway | Em desenvolvimento |

---

## 🚀 FlaBeauty · e-commerce em produção

**Loja de moda feminina no ar**, do catálogo ao pós-venda, com automação fiscal, logística e
financeira. É onde os problemas do OrderFlow deixaram de ser teoria.

🔗 **[flabeauty.com.br](https://flabeauty.com.br)** · Next.js 15 · React 19 · TypeScript · Supabase (PostgreSQL, Auth, RLS) · Vercel

Pagamentos com Mercado Pago (Pix, cartão e boleto) e webhooks assinados (HMAC e anti-replay),
emissão fiscal, cálculo de frete e painel administrativo com controle de estoque.

---

## 📦 Outros projetos

| Projeto | O que é | Stack |
|---|---|---|
| **gestao-fiscal-postos** 🔒 | Suíte desktop de **gestão fiscal e financeira** de uma rede de postos: consulta de NF-e, conferência de pagamentos (ERP x Sicoob, PagBank, Sipag e PIX), análise de descontos em PDF, clientes a prazo e estoque | Python · PySide6 · SQL |
| **camaragest** 🔒 | Plataforma de gestão de gabinete e demandas do cidadão para **câmaras municipais**, em produção | JavaScript · Supabase |
| **[ponto-cego](https://github.com/BrunoBergamin/ponto-cego)** | Diagnóstico interativo com **hero 3D em WebGL** | JavaScript · WebGL |
| **analises-digitais** 🔒 | **Auditorias digitais** de sites e presença online de empresas | HTML · Análise técnica |
| **[estudos](https://github.com/BrunoBergamin/estudos)** | Exercícios e cursos de Java, SQL, Python e Git, com o histórico preservado | Java · SQL · Python |

Estou na **trilha Itaú Java com IA, da DIO**: o motor de checkout e a Lumi saíram dos desafios
dela.

---

## 🛠️ Tecnologias

**Back-end**
<p>
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java"/>
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Spring_AI-6DB33F?style=for-the-badge&logo=spring&logoColor=white" alt="Spring AI"/>
  <img src="https://img.shields.io/badge/Quarkus-4695EB?style=for-the-badge&logo=quarkus&logoColor=white" alt="Quarkus"/>
  <img src="https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white" alt="Hibernate"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"/>
  <img src="https://img.shields.io/badge/Apache_Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" alt="Kafka"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis"/>
</p>

**Testes e entrega**
<p>
  <img src="https://img.shields.io/badge/JUnit_5-25A162?style=for-the-badge&logo=junit5&logoColor=white" alt="JUnit 5"/>
  <img src="https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white" alt="Maven"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions"/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git"/>
</p>

**Web e dados**
<p>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase"/>
</p>

---

## 📫 Contato

- 💼 **LinkedIn:** [Bruno Alves Bergamin](https://www.linkedin.com/in/bruno-alves-bergamin-6b711a347/)
- 🌐 **Em produção:** [flabeauty.com.br](https://flabeauty.com.br)
- 📍 Boituva / SP · **aberto a vagas de desenvolvedor back-end Java**
