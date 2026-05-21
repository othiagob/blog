---
title: "CidadãoBot API · Farmácias de Plantãos"
date: 2026-05-21
tags: ["java", "collections", "estrutura de dados", "backend", "SDD", "Thiago Blog Teste"]
---

# SDD — CidadãoBot API · Farmácias de Plantão

> **Versão:** 3.0 Definitiva  
> **Data:** 20/05/2026  
> **Status:** Aprovado – Fonte única de verdade do projeto  
> **Projeto:** CidadãoBot API – Farmácias de Plantão (Ji-Paraná/RO)  
> **Desenvolvedor:** Thiago Borghardt  
> **Objetivos:** Backend profissional + Preparação para mercado + Portfólio técnico

---

## 0. Visão Geral

Este é o **documento soberano e definitivo** do projeto CidadãoBot. Consolidou:

- SDD v1.0 original
- Documento de evolução do ChatGPT (Atualização Geral)
- Verificação real do código-fonte
- Stack tecnológica implementada
- Arquitetura efetivamente funcionando

**Princípio inviolável:**  
> Toda decisão do projeto deve nascer, ser validada e evoluir a partir deste documento.

---

## 1. Finalidade e Autoridade

### 1.1 Escopo oficial

Este SDD define:
- Objetivos técnicos, de aprendizado e profissionais
- Arquitetura macro e micro
- Regras de negócio obrigatórias
- Stack tecnológica
- Convenções de código, commit e estrutura
- Estratégias de persistência, testes e evolução
- Integração com n8n e ecossistema futuro

### 1.2 Ordem de autoridade (em caso de conflito)

1. **Código validado e testado** (verdade de fato)
2. **Migrations Flyway já aplicadas** (história autorizada do banco)
3. **Este SDD**
4. **Documentação oficial (README, OpenAPI)**
5. **Sugestões de IA** (mentora crítica, não dona das regras)
6. **Preferências momentâneas**

### 1.3 Evolução do documento

Este SDD é vivo. Mudanças devem:

- Refletir mudanças reais no código
- Ser documentadas com data e motivo
- Manter histórico de versões
- Passar por validação antes da aplicação

---

## 2. Objetivos do Projeto

### 2.1 Objetivo funcional

Construir uma **API REST profissional** que retorna farmácias de plantão em **Ji-Paraná/RO** com base em:

- **Horário atual** (GET /api/plantoes/atual)
- **Data específica** (GET /api/plantoes?data=AAAA-MM-DD)
- **Filtro por distrito** (parâmetro opcional)

#### Regra temporal (oficial)

O plantão funciona como **ciclo de 24 horas** iniciando às **07:00**:

```text
07:00 de um dia → 07:00 do dia seguinte
```

Exemplos práticos:

| Hora/Data | Data de Referência | Motivo |
|-----------|-------------------|--------|
| 22:00 do dia 10 | 10/05 | Após 07:00 |
| 02:00 do dia 11 | 10/05 | Antes de 07:00 |
| 06:59 do dia 11 | 10/05 | Antes de 07:00 |
| 07:00 do dia 11 | 11/05 | Horário de virada |
| 19:00 do dia 11 | 11/05 | Após 07:00 |

**Implementação:** Toda a lógica temporal fica exclusivamente em `PlantaoService.determinarDataPlantaoAtivo()`.

### 2.2 Objetivo técnico

Construir uma API REST robusta com:

- **Java 17** – linguagem principal
- **Spring Boot 3.5** – framework base
- **PostgreSQL** – banco relacional
- **Flyway** – versionamento de schema
- **Spring Data JPA** – persistência ORM
- **JUnit 5 + Mockito** – testes automatizados
- **Docker + Docker Compose** – containerização
- **OpenAPI/Swagger** – documentação automática
- **GitHub Actions** – CI/CD básico
- **Profiles dev/test/prod** – isolamento de ambientes

A API deve ser:
- **Testada** (todos os comportamentos críticos cobertos)
- **Documentada** (OpenAPI + README + comentários explicativos)
- **Previsível** (sem efeitos colaterais ocultos)
- **Escalável** (arquitetura preparada para crescimento)

### 2.3 Objetivo de aprendizado

Este projeto existe principalmente para desenvolver competência real em:

- **Arquitetura backend moderna**
- **Separação de responsabilidades** (Controller/Service/Repository)
- **Persistência relacional** com JPA
- **Versionamento de banco de dados** com Flyway
- **Testes automatizados** (unitários, JPA, WebMvc)
- **Tratamento de erros** em escala profissional
- **Containerização** com Docker
- **Configuração externalizada** para diferentes ambientes
- **Integração com ferramentas externas** (n8n)
- **Preparação para entrevistas técnicas de backend**

### 2.4 Objetivo profissional

O projeto serve como:

- **Portfólio GitHub** diferenciado
- **Demonstração prática** para recrutadores
- **Conteúdo técnico** para LinkedIn/blog
- **Laboratório pessoal** de aprendizado contínuo
- **Preparação real** para mercado de trabalho

---

## 3. Princípios Fundamentais e Filosofia

### 3.1 Regra central

```text
Não basta funcionar.
O desenvolvedor precisa entender, testar, documentar e conseguir explicar.
```

### 3.2 Filosofia de engenharia

O projeto prioriza:

- **Simplicidade robusta** – cada componente tem exatamente uma responsabilidade
- **Clareza arquitetural** – qualquer desenvolvedor consegue entender o fluxo
- **Separação correta** – Controller, Service, Repository, Entity = funções distintas
- **Previsibilidade** – não há surpresas ocultas no comportamento
- **Testabilidade** – código é naturalmente testável
- **Documentação viva** – SDD, README e código evoluem juntos
- **Baixo acoplamento** – mudanças locais não afetam todo o sistema

### 3.3 Filosofia de aprendizado

Antes de implementar qualquer coisa, o desenvolvedor deve:

1. **Entender** o problema completamente
2. **Modelar** a solução mentalmente
3. **Prever** riscos e casos extremos
4. **Implementar** em passos pequenos
5. **Testar** cada passo
6. **Explicar** o raciocínio (em comentários ou documentação)
7. **Documentar** o aprendizado
8. **Commitar** de forma atômica

### 3.4 Papel da IA no projeto

A IA atua como **mentora técnica crítica**, não como dona das decisões.

**Ela deve:**
- Corrigir hipóteses incorretas com fundamento técnico
- Seguir este SDD sem desvios
- Explicar conceitos antes do código
- Conectar teoria e prática
- Questionar complexidade prematura
- Ajudar na preparação para entrevistas
- Justificar decisões técnicas

**Ela NÃO deve:**
- Concordar automaticamente
- Inventar regras fora do SDD
- Gerar código sem explicação
- Quebrar separação de camadas
- Adicionar tecnologia sem justificativa
- Duplicar regra de negócio

---

## 4. Arquitetura Geral

### 4.1 Arquitetura macro (ecossistema completo)

```text
┌──────────────────────────────────────────────────────────────────┐
│                    FASE ATUAL (Implementada)                     │
│                                                                   │
│  Usuário (aplicação)                                             │
│        ↓                                                          │
│  Interface (WhatsApp / n8n / Web)                                │
│        ↓                                                          │
│  n8n (orquestração de fluxo)                                     │
│  ├─ Recebe mensagem                                              │
│  ├─ Passa para IA (interpretação)                                │
│  └─ Chama API baseado em intenção                                │
│        ↓                                                          │
│  API Spring Boot (CORAÇÃO DO SISTEMA)                            │
│  ├─ Controller (HTTP)                                            │
│  ├─ Service (Regra de negócio)                                   │
│  ├─ Repository (Persistência)                                    │
│  └─ Entity (Modelo de dados)                                     │
│        ↓                                                          │
│  PostgreSQL (banco de dados oficial)                             │
│        ↓                                                          │
│  Flyway (versionamento de schema)                                │
└──────────────────────────────────────────────────────────────────┘
```

### 4.2 Separação de responsabilidades

| Camada | Responsabilidade | Tecnologia |
|--------|------------------|------------|
| **Usuário/Interface** | Interação com usuário | WhatsApp, n8n UI |
| **n8n** | Orquestração de workflow | n8n (Docker) |
| **IA** | Interpretação de intenção | LLM ou prompts |
| **API REST** | Regra de negócio | Spring Boot |
| **Persistência** | Acesso ao banco | Spring Data JPA |
| **Banco de dados** | Armazenamento oficial | PostgreSQL |

### 4.3 Regra absoluta (critical)

```text
A API Spring Boot é a ÚNICA fonte de verdade do sistema.
```

**Nunca fazer:**
- Regra de negócio no n8n
- Cálculos no WhatsApp
- Decisões de plantão fora da API
- Duplicar lógica em múltiplos lugares
- Retornar entidades JPA diretamente

---

## 5. Arquitetura Interna da API

### 5.1 Fluxo de requisição

```text
Requisição HTTP
    ↓
PlantaoController (HTTP)
    ↓
PlantaoService (Regra de negócio)
    ↓
EscalaPlantaoRepository (Acesso ao banco)
    ↓
PostgreSQL (Dados oficiais)
    ↓
Resposta DTO (JSON)
```

### 5.2 Responsabilidades por camada

#### **Controller** (`PlantaoController`)

**Responsável por:**
- Receber requisições HTTP
- Validar parâmetros básicos
- Converter parâmetros em tipos Java
- Chamar Service
- Formatar resposta em DTO
- Retornar status HTTP correto

**NÃO deve:**
- Conter lógica de negócio
- Acessar banco diretamente
- Calcular datas ou horários
- Tomar decisões de domínio
- Retornar Entity diretamente

**Exemplo:**
```java
@GetMapping("/atual")
public ResponseEntity<RespostaApiDTO> consultarPlantaoAtual(
    @RequestParam(required = false) String distrito) {
  ConsultaPlantaoAtualRespostaDTO resultado = 
    plantaoService.consultarPlantaoAtual(distrito);
  return ResponseEntity.ok(
    new RespostaApiDTO(true, "OK", resultado, LocalDateTime.now())
  );
}
```

#### **Service** (`PlantaoService`)

**Responsável por:**
- **Toda regra de negócio** do domínio
- Determinar data de referência do plantão (REGRA TEMPORAL)
- Orquestração de chamadas ao repositório
- Validações de domínio
- Transformação de Entity em DTO
- Decisões sobre o que retornar

**Jamais deve:**
- Acessar HTTP diretamente
- Manipular banco (apenas via Repository)
- Saber sobre DTOs (apenas converte no final)
- Conter regra temporal fora de `determinarDataPlantaoAtivo()`

**Método crítico:**
```java
public Optional<LocalDate> determinarDataPlantaoAtivo(LocalDateTime momento) {
  LocalDate dataAtual = momento.toLocalDate();
  LocalTime horarioAtual = momento.toLocalTime();
  
  if (horarioAtual.isBefore(HORARIO_INICIO_PLANTAO)) { // 07:00
    return Optional.of(dataAtual.minusDays(1));
  }
  
  return Optional.of(dataAtual);
}
```

#### **Repository** (`EscalaPlantaoRepository`)

**Responsável por:**
- Persistência (salvar/atualizar/deletar)
- Queries ao banco
- Acesso via Spring Data JPA
- Retornar Entity

**Jamais deve:**
- Conter regra de negócio
- Tomar decisões de domínio
- Manipular datas ou lógica temporal
- Validar regras de negócio

**Exemplo:**
```java
public interface EscalaPlantaoRepository extends JpaRepository<EscalaPlantao, Long> {
  List<EscalaPlantao> findByDataPlantao(LocalDate data);
  List<EscalaPlantao> findByDataPlantaoAndFarmaciaDistritoIgnoreCase(
    LocalDate data, String distrito);
}
```

#### **Entity** (JPA Models)

**Responsável por:**
- Representar dados na memória
- Mapeamento para tabelas
- Validações simples (anotações JPA)

**Nunca deve:**
- Conter lógica de negócio complexa
- Ser retornada diretamente na API
- Fazer queries por si mesma

### 5.3 Fluxo de dados

```text
Requisição HTTP
    ↓
Controller (parâmetros)
    ↓
Service (lógica)
    ↓
Repository (Entity)
    ↓
PostgreSQL (armazenamento)
    ↓
Entity → DTO (conversão)
    ↓
Response JSON
```

---

## 6. Stack Tecnológica Oficial

| Camada | Tecnologia | Versão | Motivo |
|--------|-----------|--------|--------|
| **Linguagem** | Java | 17 | Estável, enterprise |
| **Framework** | Spring Boot | 3.5 | REST, configuração automática |
| **Web** | Spring Web | (Boot) | Endpoints REST |
| **Persistência** | Spring Data JPA | (Boot) | ORM moderno |
| **Banco** | PostgreSQL | 15 | Relacional, confiável |
| **Migration** | Flyway | (Boot) | Versionamento de schema |
| **Testes** | JUnit 5 | (Boot) | Framework de testes |
| **Mock** | Mockito | (Boot) | Mocks em testes |
| **Banco teste** | H2 | (test) | Em memória, rápido |
| **Validation** | Spring Validation | (Boot) | Validação de beans |
| **API Docs** | SpringDoc OpenAPI | 2.8.9 | Swagger automático |
| **Build** | Maven | Wrapper | Reproducível |
| **Containers** | Docker | Latest | Empacotamento |
| **Orquestração** | Docker Compose | Latest | Ambiente local |
| **IDE** | IntelliJ / Neovim | Latest | Desenvolvimento |
| **SO** | Manjaro Linux | Latest | Sistema operacional |

### 6.1 Dependências críticas não negociáveis

```xml
<!-- Spring Boot base -->
spring-boot-starter-web
spring-boot-starter-data-jpa
spring-boot-starter-validation

<!-- Banco de dados -->
postgresql (runtime)
flyway-core + flyway-database-postgresql

<!-- Testes -->
spring-boot-starter-test
junit-jupiter
mockito

<!-- Documentação -->
springdoc-openapi-starter-webmvc-ui (v2.8.9+)

<!-- Utilidades -->
lombok (opcional, mas recomendado)
```

### 6.2 Tecnologias **proibidas** sem justificativa

- Graphql (REST é suficiente)
- Cache (não é prioridade atual)
- Elasticsearch (sem requisito)
- Kafka (sem necessidade de eventos)
- Multithreading complexo (sem requisito)
- ORM diferente de JPA (padrão Java)

---

## 7. Convenções Obrigatórias

### 7.1 Linguagem de domínio

**Tudo em português brasileiro:**

```text
✓ Farmacia, EscalaPlantao, PlantaoService
✓ buscarPlantaoPorData, determinarDataPlantaoAtivo
✓ ErroRespostaDTO, TratadorGlobalDeErros

✗ Farm, Schedule, PlantaoScheduleManager
✗ findByDate, getActiveSchedule
```

### 7.2 Convenções SQL

| Elemento | Convenção | Exemplo |
|----------|-----------|---------|
| **Tabelas** | snake_case | `escalas_plantao`, `farmacias` |
| **Colunas** | snake_case | `data_plantao`, `inicia_as` |
| **Entidades Java** | PascalCase | `EscalaPlantao`, `Farmacia` |
| **Campos Java** | camelCase | `dataPlantao`, `iniciaAs` |

### 7.3 Padrão de commits

```text
<tipo>: <descrição em português, modo imperativo>

Tipos obrigatórios:
- feat:  nova funcionalidade
- fix:   correção de bug
- test:  testes (novos ou melhorados)
- docs:  documentação
- style: formatação (sem lógica)
- refactor: refatoração (sem mudança de comportamento)
- ci:    CI/CD
- chore: dependências, configuração

Exemplos:
feat: cria endpoint GET /api/plantoes/atual
fix: corrige regra temporal para 07:00
test: adiciona testes de madrugada
docs: atualiza SDD com regra de 24 horas
refactor: extrai método determinarDataPlantaoAtivo
ci: configura GitHub Actions
```

### 7.4 Naming de métodos

```text
Service:
- buscar* (retorna List ou Entity)
- consultar* (retorna DTO)
- determinar* (calcula algo, retorna Optional ou valor)
- validar* (valida, lança exceção se inválido)

Controller:
- @GetMapping("/{recurso}") para consultas
- @PostMapping("/{recurso}") para criação
- @PutMapping("/{recurso}/{id}") para atualização
- @DeleteMapping("/{recurso}/{id}") para deleção

Repository:
- findBy* (queries simples)
- findAllBy* (retorna List)
```

### 7.5 Estrutura oficial de pacotes

```text
br.com.othiagob.cidadaobot
├── CidadaobotApplication.java
├── configuracao/
│   ├── OpenApiConfig.java
│   ├── WebConfig.java
│   └── [outras configs]
├── dto/
│   └── RespostaApiDTO.java
├── erro/
│   ├── ErroRespostaDTO.java
│   └── TratadorGlobalDeErros.java
├── farmacia/
│   ├── Farmacia.java
│   └── FarmaciaRepository.java
└── plantao/
    ├── EscalaPlantao.java
    ├── EscalaPlantaoRepository.java
    ├── PlantaoController.java
    ├── PlantaoService.java
    └── dto/
        ├── ConsultaPlantaoAtualRespostaDTO.java
        ├── FarmaciaRespostaDTO.java
        └── PlantaoRespostaDTO.java
```

**Regra:** Cada domínio (farmacia, plantao, erro, etc.) tem seu pacote. DTOs ficam próximos do seu contexto.

---

## 8. Modelo de Domínio Oficial

### 8.1 Entidade `Farmacia`

Representa dados permanentes de uma farmácia.

```java
@Entity
@Table(name = "farmacias")
public class Farmacia {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;
  
  @Column(nullable = false)
  private String nome;
  
  @Column(nullable = false)
  private String endereco;
  
  @Column(nullable = false)
  private String bairro;
  
  @Column(nullable = false)
  private String distrito;
  
  @Column(nullable = false)
  private String telefone;
  
  @Column(name = "criada_em", nullable = false)
  private LocalDateTime criadaEm;
  
  @OneToMany(mappedBy = "farmacia")
  private List<EscalaPlantao> escalas;
}
```

**Campos:**
- `id`: Identificador único
- `nome`: Nome comercial (ex: "FARMACIA REAL")
- `endereco`: Endereço completo
- `bairro`: Bairro (ex: "CENTRO")
- `distrito`: Distrito (ex: "Primeiro Distrito")
- `telefone`: Para contato (ex: "3422-3491")
- `criadaEm`: Timestamp de criação

### 8.2 Entidade `EscalaPlantao`

Representa qual farmácia atende em determinada data.

```java
@Entity
@Table(name = "escalas_plantao")
public class EscalaPlantao {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;
  
  @ManyToOne
  @JoinColumn(name = "farmacia_id", nullable = false)
  private Farmacia farmacia;
  
  @Column(name = "data_plantao", nullable = false)
  private LocalDate dataPlantao;
  
  @Column(name = "inicia_as", nullable = false)
  private LocalTime iniciaAs;
  
  @Column(name = "termina_as", nullable = false)
  private LocalTime terminaAs;
  
  @Column(name = "criada_em", nullable = false)
  private LocalDateTime criadaEm;
}
```

**Campos:**
- `id`: Identificador único
- `farmacia`: Relacionamento com Farmacia
- `dataPlantao`: Data do plantão (ex: 2026-05-20)
- `iniciaAs`: Hora de início (ex: 07:00)
- `terminaAs`: Hora de término (ex: 07:00)
- `criadaEm`: Timestamp de criação

**Relacionamento:**
```text
Farmacia 1:N EscalaPlantao

Uma farmácia pode ter múltiplas escalas (dias diferentes).
Uma escala pertence a exatamente uma farmácia.
```

---

## 9. Regras de Negócio Oficiais

### 9.1 Regra temporal do plantão (CRÍTICA)

**Definição oficial:**

O plantão funciona como um ciclo de **24 horas consecutivas** que inicia às **07:00** de um dia e termina às **07:00** do dia seguinte.

**Cálculo da data de referência:**

```
Se horário_atual < 07:00 → data_referência = data_hoje - 1
Senão                    → data_referência = data_hoje
```

**Tabela de decisão:**

| Momento | Data de Referência | Motivo |
|---------|-------------------|--------|
| 22:00 dia 10 | 10 | Depois de 07:00 |
| 00:00 dia 11 | 10 | Antes de 07:00 |
| 06:59 dia 11 | 10 | Ainda antes de 07:00 |
| 07:00 dia 11 | 11 | Horário de virada |
| 19:00 dia 11 | 11 | Depois de 07:00 |

**Implementação obrigatória:**

Está **exclusivamente** em `PlantaoService.determinarDataPlantaoAtivo()`:

```java
public Optional<LocalDate> determinarDataPlantaoAtivo(LocalDateTime momento) {
  if (momento == null) {
    throw new IllegalArgumentException("Momento não pode ser nulo.");
  }
  
  LocalDate dataAtual = momento.toLocalDate();
  LocalTime horarioAtual = momento.toLocalTime();
  
  // Se está antes das 07:00, refere-se ao plantão do dia anterior
  if (horarioAtual.isBefore(HORARIO_INICIO_PLANTAO)) { // 07:00
    return Optional.of(dataAtual.minusDays(1));
  }
  
  // Senão, refere-se ao plantão do dia atual
  return Optional.of(dataAtual);
}
```

### 9.2 Regra de inexistência de plantão

Se não houver escala cadastrada para a data consultada:

```json
{
  "sucesso": true,
  "mensagem": "Plantão encontrado para a data informada.",
  "dados": {
    "dataReferencia": "2026-05-20",
    "plantaoAtivo": true,
    "mensagem": "Não encontrei escala de plantão cadastrada para esta data no sistema.",
    "plantoes": []
  }
}
```

**Regra:**
- A API **nunca inventa** farmácia
- Retorna lista vazia
- Status HTTP é sempre 200 (sucesso funcional)
- Mensagem informa claramente que não há dados

### 9.3 Filtro por distrito

Se fornecido parâmetro `?distrito=Primeiro%20Distrito`:

- Filtra escalas apenas daquele distrito
- Valida que o distrito não é vazio
- Ignora case (case-insensitive)
- Se nenhuma escala existe, retorna lista vazia

---

## 10. Contrato REST Oficial

### 10.1 Endpoint principal: Plantão atual

```http
GET /api/plantoes/atual
GET /api/plantoes/atual?distrito=Primeiro%20Distrito
```

**Parâmetros:**
- `distrito` (opcional): Filtra por distrito específico

**Retorno:**
```json
{
  "sucesso": true,
  "mensagem": "Plantão ativo encontrado.",
  "dados": {
    "dataReferencia": "2026-05-20",
    "plantaoAtivo": true,
    "mensagem": "Plantão ativo encontrado.",
    "plantoes": [
      {
        "dataPlantao": "2026-05-20",
        "iniciaAs": "07:00:00",
        "terminaAs": "07:00:00",
        "farmacia": {
          "nome": "FARMACIA REAL",
          "endereco": "RUA DOS MINEIROS, 298",
          "bairro": "CENTRO",
          "distrito": "Primeiro Distrito",
          "telefone": "3422-3491"
        },
        "mensagem": "FARMACIA REAL está de plantão das 07:00 às 07:00."
      }
    ]
  },
  "timestamp": "2026-05-20T10:30:00"
}
```

**Status HTTP:** 200 OK

### 10.2 Endpoint: Plantão por data

```http
GET /api/plantoes?data=2026-05-20
GET /api/plantoes?data=2026-05-20&distrito=Segundo%20Distrito
```

**Parâmetros:**
- `data` (obrigatório): Data no formato AAAA-MM-DD
- `distrito` (opcional): Filtra por distrito

**Retorno:** Similar ao plantão atual, mas com `dataReferencia` igual à data consultada.

**Status HTTP:** 200 OK

### 10.3 DTO obrigatório

A API **NUNCA** expõe Entity diretamente.

**DTOs obrigatórios:**

1. **RespostaApiDTO** – Envelope padrão de todas as respostas
   ```java
   {
     "sucesso": boolean,
     "mensagem": String,
     "dados": Object,
     "timestamp": LocalDateTime
   }
   ```

2. **ConsultaPlantaoAtualRespostaDTO** – Dados da consulta
   ```java
   {
     "dataReferencia": LocalDate,
     "plantaoAtivo": boolean,
     "mensagem": String,
     "plantoes": List<PlantaoRespostaDTO>
   }
   ```

3. **PlantaoRespostaDTO** – Escala individual
   ```java
   {
     "dataPlantao": LocalDate,
     "iniciaAs": LocalTime,
     "terminaAs": LocalTime,
     "farmacia": FarmaciaRespostaDTO,
     "mensagem": String
   }
   ```

4. **FarmaciaRespostaDTO** – Dados da farmácia
   ```java
   {
     "nome": String,
     "endereco": String,
     "bairro": String,
     "distrito": String,
     "telefone": String
   }
   ```

### 10.4 Tratamento de erros

Todos os erros retornam **RespostaApiDTO** com `sucesso: false`:

```json
{
  "sucesso": false,
  "mensagem": "Data inválida. Formato esperado: AAAA-MM-DD",
  "dados": null,
  "timestamp": "2026-05-20T10:30:00"
}
```

**Erros possíveis:**
- 400 Bad Request – Parâmetro inválido
- 404 Not Found – Recurso não existe (raramente usado)
- 500 Internal Server Error – Erro interno (nunca deve acontecer)

---

## 11. Estratégia de Persistência

### 11.1 Regra oficial

```text
Flyway controla schema.
Hibernate apenas valida.
```

### 11.2 Configuração obrigatória

```properties
# Ambiente dev/prod
spring.jpa.hibernate.ddl-auto=validate

# Ambiente test (H2)
spring.jpa.hibernate.ddl-auto=create-drop

# Nunca:
# spring.jpa.hibernate.ddl-auto=update ou create ou create-drop (em prod)
```

### 11.3 Migrations Flyway (histórico oficial)

As migrations vivem em `src/main/resources/db/migration/`:

| Migration | Descrição |
|-----------|-----------|
| V1__criar_tabela_farmacias.sql | Tabela de farmácias |
| V2__criar_tabela_escala_plantao.sql | Tabela de escalas |
| V3__adicionar_restricoes_escala_plantao.sql | Constrains |
| V4__adicionar_restricao_farmacia.sql | Foreign keys |
| V5__inserir_farmacias_iniciais.sql | Dados iniciais |
| V6__inserir_escalas_maio_junho_2026.sql | Escalas exemplo |
| V7__ajustar_horario_padrao_plantao.sql | Ajustes |

**Regra crítica:**

```text
Nunca editar migration já aplicada.
Toda correção deve ser uma nova migration.
```

Se descobrir erro em V3, crie V8 para corrigir, nunca altere V3.

### 11.4 Profile de persistência

```properties
# application.properties (base)
spring.jpa.open-in-view=false
spring.jpa.show-sql=false

# application-dev.properties
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

# application-test.properties
spring.jpa.hibernate.ddl-auto=create-drop
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver

# application-prod.properties
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.show-sql=false
```

---

## 12. Estratégia de Testes

### 12.1 Princípio fundamental

```text
Código sem teste não é considerado validado.
```

Antes de commitar, deve haver testes cobrindo o comportamento.

### 12.2 Tipos de teste obrigatórios

| Tipo | Objetivo | Framework | Onde |
|------|----------|-----------|------|
| **Unitário** | Regra de negócio isolada | JUnit 5 + Mockito | PlantaoServiceTest |
| **JPA** | Persistência e queries | @DataJpaTest + H2 | EscalaPlantaoRepositoryTest |
| **WebMvc** | Endpoints REST | @WebMvcTest | PlantaoControllerTest |
| **Integração** | Fluxo real completo | @SpringBootTest | (futuro) |

### 12.3 Cobertura prioritária

**Máxima prioridade:** `PlantaoService`

Porque contém:
- Regra temporal (coração do sistema)
- Decisões de domínio
- Transformações de dados

Testes obrigatórios:

```java
@Test
void testDeterminarDataPlantaoAntes07h() {
  LocalDateTime momento = LocalDateTime.of(2026, 5, 11, 6, 59);
  Optional<LocalDate> data = service.determinarDataPlantaoAtivo(momento);
  assertEquals(LocalDate.of(2026, 5, 10), data.orElse(null));
}

@Test
void testDeterminarDataPlantaoApos07h() {
  LocalDateTime momento = LocalDateTime.of(2026, 5, 11, 7, 0);
  Optional<LocalDate> data = service.determinarDataPlantaoAtivo(momento);
  assertEquals(LocalDate.of(2026, 5, 11), data.orElse(null));
}

@Test
void testConsultarPlantaoAtualSemDados() {
  ConsultaPlantaoAtualRespostaDTO resultado = 
    service.consultarPlantaoAtual(null);
  assertTrue(resultado.getPlantoes().isEmpty());
}
```

### 12.4 Executar testes

```bash
# Todos os testes
./mvnw test

# Teste específico
./mvnw test -Dtest=PlantaoServiceTest

# Com saída detalhada
./mvnw test -X

# Antes de todo commit obrigatório
./mvnw clean test
```

---

## 13. Infraestrutura e DevOps

### 13.1 Docker e Containerização

**Dockerfile:**
```dockerfile
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

COPY target/cidadaobot-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
```

**docker-compose.yml:**
```yaml
services:
  postgres:
    image: postgres:15
    environment:
      POSTGRES_DB: ${POSTGRES_DB}
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
    ports:
      - "5432:5432"
    volumes:
      - cidadaobot-postgres-data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER}"]
      interval: 5s
      timeout: 5s
      retries: 5

  api:
    build: .
    depends_on:
      postgres:
        condition: service_healthy
    environment:
      SPRING_PROFILES_ACTIVE: prod
      DATABASE_URL: jdbc:postgresql://postgres:5432/${POSTGRES_DB}
      DATABASE_USERNAME: ${POSTGRES_USER}
      DATABASE_PASSWORD: ${POSTGRES_PASSWORD}
    ports:
      - "8080:8080"

volumes:
  cidadaobot-postgres-data:
```

### 13.2 Profiles da aplicação

| Profile | Ambiente | Banco | Porta | Hibernate | Uso |
|---------|----------|-------|-------|-----------|-----|
| **dev** | Local | PostgreSQL | 8081 | validate | Desenvolvimento |
| **test** | Testes | H2 em memória | - | create-drop | Testes JUnit |
| **prod** | Docker/Cloud | PostgreSQL | 8080 | validate | Production |

**Ativar:**
```bash
# Dev
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev

# Test (automático com mvnw test)
./mvnw test

# Prod (Docker)
docker compose up
```

### 13.3 Variáveis de ambiente

**`.env.example`:**
```env
POSTGRES_DB=cidadaobot
POSTGRES_USER=postgres
POSTGRES_PASSWORD=senha_segura
DATABASE_URL=jdbc:postgresql://postgres:5432/cidadaobot
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=senha_segura
SPRING_PROFILES_ACTIVE=prod
```

**Nunca commitar `.env` com valores reais.**

### 13.4 GitHub Actions (CI)

**`.github/workflows/build.yml`:**
```yaml
name: Build e Testes

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-java@v3
        with:
          java-version: 17
      - run: ./mvnw clean test
      - run: ./mvnw package
```

**Objetivo:**
- Executar testes em todo push
- Validar build
- Impedir merge de código quebrado

---

## 14. Documentação

### 14.1 Documentação obrigatória

| Documento | Localização | Responsabilidade |
|-----------|------------|-----------------|
| **SDD** | `SDD_CIDADAOBOT_V3_DEFINITIVO.md` | Decisões de arquitetura |
| **README** | `README.md` | Como usar a API |
| **OpenAPI** | `http://localhost:8080/swagger-ui.html` | Documentação automática de endpoints |
| **Comentários** | Código-fonte | Explicação de decisões técnicas |
| **Commits** | Git history | Rastreamento de mudanças |

### 14.2 OpenAPI/Swagger

Configurado em `OpenApiConfig.java`:

```java
@Configuration
public class OpenApiConfig {
  @Bean
  public OpenAPI customOpenAPI() {
    return new OpenAPI()
      .info(new Info()
        .title("CidadãoBot API")
        .version("1.0.0")
        .description("API de consulta de farmácias de plantão"));
  }
}
```

**Acessar:**
```
Dev: http://localhost:8081/swagger-ui.html
Prod: http://localhost:8080/swagger-ui.html
```

### 14.3 Comentários no código

```java
// Breve explicação do QUE faz
public List<EscalaPlantao> buscarPlantoesAtivos(LocalDateTime momento) {
  // Se antes de 07:00, consulta plantão do dia anterior
  // (ver determinarDataPlantaoAtivo para entender a regra temporal)
  LocalDate dataPlantaoAtivo = determinarDataPlantaoAtivo(momento).orElseThrow();
  
  return escalaPlantaoRepository.findByDataPlantao(dataPlantaoAtivo);
}
```

---

## 15. Desenvolvimento e Fluxo de Trabalho

### 15.1 Ciclo de desenvolvimento

```text
1. Entender o requisito completamente
   ↓
2. Revisar este SDD (aplicável?)
   ↓
3. Escrever teste (test-first)
   ↓
4. Implementar funcionalidade
   ↓
5. Passar em todos os testes
   ↓
6. Documentar (comentário ou SDD)
   ↓
7. Commitar de forma atômica
   ↓
8. Atualizar documentação (README, etc)
```

### 15.2 Checklist antes de commit

```bash
# Executar testes
./mvnw clean test

# Verificar status
git status
git diff --stat

# Perguntas obrigatórias:
# - Tudo está funcionando?
# - Entendo o que implementei?
# - Consigo explicar em entrevista?
# - O SDD continua válido?
# - Há código duplicado?
# - Há comentário explicativo?
# - Há teste cobrindo?
```

### 15.3 Padrão de commits

```bash
# Boa estrutura:
git commit -m "feat: cria regra temporal para determinar plantão ativo

Implementa PlantaoService.determinarDataPlantaoAtivo() que:
- Recebe LocalDateTime da consulta
- Se horário < 07:00, retorna dia anterior
- Senão, retorna dia atual

Justificativa: Plantão funciona como ciclo de 24h iniciando às 07:00.

Testes: PlantaoServiceTest com casos de madrugada e manhã."
```

---

## 16. Integração com n8n e Ecossistema

### 16.1 Arquitetura de integração

```text
┌──────────────────────┐
│   Usuário (WhatsApp) │
└──────────┬───────────┘
           │ Mensagem
           ▼
┌──────────────────────┐
│      n8n (IA)        │
│  - Interpreta texto  │
│  - Decide ação       │
└──────────┬───────────┘
           │ HTTP Request
           ▼
┌──────────────────────────────┐
│  CidadãoBot API Spring Boot  │
│  - Executa regra de negócio  │
│  - Retorna dados oficiais    │
└──────────┬──────────────────┘
           │ Resposta DTO
           ▼
┌──────────────────────┐
│    n8n (Formatação)  │
│  - Formata resposta  │
│  - Devolve ao usuário│
└──────────────────────┘
```

### 16.2 Contrato entre n8n e API

**n8n envia:**
```json
{
  "intencao": "consultar_plantao_atual",
  "parametros": {
    "distrito": "Primeiro Distrito" // opcional
  }
}
```

**API retorna:**
```json
{
  "sucesso": true,
  "mensagem": "Plantão ativo encontrado.",
  "dados": { ... },
  "timestamp": "2026-05-20T10:30:00"
}
```

### 16.3 Responsabilidades

| Camada | Faz | Não faz |
|--------|-----|---------|
| **n8n** | Orquestra fluxo | Calcula regra temporal |
| **IA** | Interpreta intenção | Decide qual farmácia está de plantão |
| **API** | Executa regra, retorna dados | Formata resposta para usuário |
| **WhatsApp** | Recebe/envia mensagens | Nada de lógica |

---

## 17. Estratégia de Aprendizado

### 17.1 Toda implementação deve responder

Antes de terminar, responder:

```text
1. O que foi feito? (descrição clara)
2. Por que foi feito? (motivo técnico)
3. Como funciona? (explicação do fluxo)
4. Como foi testado? (testes cobrindo)
5. Qual problema resolve? (valor agregado)
6. Como explicar em entrevista? (discurso pronto)
7. Relaciona-se com qual parte do SDD? (documentação)
```

### 17.2 Regra de entendimento

O desenvolvedor **não deve avançar** sem entender:

- O fluxo completo da requisição
- O motivo de cada decisão
- O impacto das mudanças
- A responsabilidade arquitetural de cada camada
- Como explicar para alguém em entrevista técnica

### 17.3 Tópicos de entrevista técnica preparados

O projeto deve preparar para responder:

```text
Por que usar DTOs em vez de Entities?
→ Desacoplamento, contrato público, evolução

Por que usar Service Layer?
→ Separação de responsabilidades, reutilização

Por que Flyway em vez de Hibernate DDL?
→ Controle de versão, determinismo, rollback

Por que PostgreSQL?
→ Relacional confiável, ACID, índices

Por que regra temporal fica em Service?
→ É lógica de negócio, não acesso a dados

Por que não retornar Entity?
→ Segurança, contrato, evolução

Por que Docker?
→ Reproduzibilidade, deployment consistente

Por que JUnit 5 + Mockito?
→ Testes isolados, framework moderno

Como você estruturaria para adicionar cache?
→ Spring Cache, annotations, invalidação

O que melhoraria em produção?
→ Logging, monitoramento, CI/CD, observabilidade
```

---

## 18. Anti-patterns Proibidos

Estas práticas são **proibidas** sem exceção:

| Prática | Por quê | Alternativa |
|---------|---------|------------|
| Regra no Controller | Viola separação | Mover para Service |
| Regra no n8n | Duplica lógica | Chamar API corretamente |
| Lógica SQL em Java | Difícil de manter | Usar Repository |
| Entity exposta na API | Inseguro e inflexível | Usar DTO |
| Código sem teste | Sem validação | Escrever teste antes |
| Migration alterada | Quebra determinismo | Criar nova migration |
| Duplicação de regra | Inconsistência | Extrair método |
| Tecnologia sem motivo | Complexidade | Justificar no SDD |
| Abstração prematura | Desnecessária | YAGNI |
| Hardcode de dados | Inflexível | Config externalizada |

---

## 19. Roadmap Oficial (Fases)

### Fases já concluídas

| Fase | Status | Descrição |
|------|--------|-----------|
| 1 | ✓ Concluída | Base Spring Boot + PostgreSQL + Flyway |
| 2 | ✓ Concluída | Relacionamentos JPA |
| 3 | ✓ Concluída | Service Layer + regra temporal |
| 4 | ✓ Concluída | API REST + DTOs |
| 5 | ✓ Concluída | Tratamento global de erros |
| 6 | ✓ Concluída | Refatoração e robustez |
| 7 | ✓ Concluída | Dados reais |
| 8 | ✓ Concluída | Consulta por data |
| 9 | ✓ Concluída | Docker + Docker Compose |
| 10 | ✓ Concluída | Integração arquitetural com n8n |
| 11 | ✓ Concluída | README profissional |
| 12 | ✓ Concluída | OpenAPI/Swagger |
| 13 | ▶ Em progresso | GitHub Actions / CI |

### Próximas fases planejadas

| Fase | Estimativa | Descrição |
|------|-----------|-----------|
| 14 | Q2 2026 | Testes de integração E2E |
| 15 | Q2 2026 | Persistência de conversa (histórico no DB) |
| 16 | Q3 2026 | Cache com Redis (opcional) |
| 17 | Q3 2026 | Observabilidade (logs estruturados) |
| 18 | Q3 2026 | Deploy em cloud (AWS/Azure/GCP) |
| 19 | Q4 2026 | Integração oficial com WhatsApp Cloud |
| 20 | Q4 2026 | Monitoramento e alertas |

---

## 20. Estratégia de Portfólio

Este projeto demonstra:

### Técnico

- ✓ Arquitetura em camadas profissional
- ✓ Separação de responsabilidades clara
- ✓ Testes automatizados em múltiplas camadas
- ✓ Persistência relacional com JPA
- ✓ Versionamento de banco com Flyway
- ✓ Tratamento de erros global
- ✓ Documentação automática (OpenAPI/Swagger)
- ✓ Containerização com Docker
- ✓ CI/CD básico com GitHub Actions
- ✓ Configuração externalizada por ambiente

### Prático

- ✓ Código que funciona em produção
- ✓ Ambiente reproduzível com docker compose
- ✓ README profissional e completo
- ✓ Decisões justificadas tecnicamente
- ✓ Git history limpo com commits atômicos

### Comunicação

- ✓ README claro
- ✓ SDD documentando decisões
- ✓ Código com comentários explicativos
- ✓ Swagger para demonstração interativa
- ✓ Capacidade de explicar em entrevista

---

## 21. Definição de Projeto Saudável

Um projeto **CidadãoBot saudável** é aquele onde:

- ✓ Arquitetura está clara e documentada
- ✓ Responsabilidades estão bem separadas
- ✓ Testes validam comportamentos críticos
- ✓ Documentação acompanha o código
- ✓ IA consegue seguir regras sem ambiguidade
- ✓ Desenvolvedor entende o que construiu
- ✓ Código é preparado para crescimento
- ✓ Decisões são rastreáveis (SDD + Git)
- ✓ Ambiente é reproduzível (Docker)
- ✓ Qualidade é medida (testes + CI)

---

## 22. Mudanças Importantes no SDD V3.0

**Em relação à V1.0:**

| Aspecto | V1.0 | V3.0 |
|---------|------|------|
| Docker | Futuro | Implementado |
| Profiles | Mencionado | Oficializado (dev/test/prod) |
| OpenAPI | Futuro | Implementado |
| GitHub Actions | Futuro | Em progresso |
| Regra temporal | 19:00-07:00 | Corrigido para 07:00-07:00 |
| n8n | Mencionado | Integração arquitetural definida |
| DTOs | Mencionado | Obrigatório em toda API |
| Swagger | Futuro | Implementado |

**Em relação à V2.0:**

- V2.0 foi revisão intermediária
- V3.0 consolida tudo em um documento único
- Mantém correções de V2.0 (07:00-07:00)
- Adiciona verificação real do código-fonte
- Documenta stack exatamente como está

---

## 23. Regra Final do Projeto

```text
O objetivo não é apenas terminar uma API.

O objetivo é se transformar em um desenvolvedor backend sólido
através da construção consciente, documentada e testada desta API.

Cada linha de código deve:
- Resolver um problema real
- Ser testada
- Ser entendida
- Ser explicável
- Ser rastreável

A API é o laboratório.
O aprendizado é o produto final.
```

---

## 24. Histórico de Revisões

| Versão | Data | Autor | Mudanças |
|--------|------|-------|----------|
| 1.0 | 14/05/2026 | Thiago Borghardt | Criação inicial |
| 2.0 | 20/05/2026 | Thiago Borghardt (c/ IA) | Correção regra temporal 07:00-07:00 + chat web n8n |
| 3.0 | 20/05/2026 | Thiago Borghardt (consolidado) | Versão definitiva: consolida V1 + V2 + código real + verificação do projeto |

---

## 25. Como Usar Este SDD

### Para implementar nova funcionalidade

1. Leia a seção relevante (Arquitetura, Contrato REST, Regras)
2. Verfique se há anti-pattern
3. Escreva teste primeiro
4. Implemente
5. Atualize documentação se necessário
6. Faça commit com referência ao SDD

### Para responder em entrevista

1. Cite este SDD como base de decisões
2. Explique a separação de camadas
3. Descreva a regra temporal como exemplo
4. Mostre como testes validam
5. Fale sobre evolução do projeto

### Para revisar código

1. Verifique conformidade com SDD
2. Procure anti-patterns proibidos
3. Valide separação de responsabilidades
4. Confirme presença de testes
5. Revise documentação

---

## 26. Contato e Feedback

Este é um documento vivo. Mudanças propostas devem:

1. Documentar motivo da mudança
2. Validar com testes
3. Atualizar este SDD
4. Commitar tudo junto

**Autor:** Thiago Borghardt  
**GitHub:** https://github.com/othiagob/cidadaobot  
**Último atualizado:** 20/05/2026

---

## Apêndice: Resumo de Comandos Essenciais

### Desenvolvimento

```bash
# Rodar em dev (porta 8081, PostgreSQL)
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev

# Rodar testes
./mvnw clean test

# Build completo
./mvnw clean package

# Verificar estrutura
tree -I 'target|.git' -L 3
```

### Docker

```bash
# Subir stack completa
docker compose up -d

# Ver logs da API
docker compose logs -f api

# Parar
docker compose down

# Limpar volumes
docker compose down -v
```

### API (exemplos)

```bash
# Plantão atual (dev)
curl -s "http://localhost:8081/api/plantoes/atual" | jq

# Com distrito
curl -s "http://localhost:8081/api/plantoes/atual?distrito=Primeiro%20Distrito" | jq

# Por data
curl -s "http://localhost:8081/api/plantoes?data=2026-05-20" | jq

# Swagger (dev)
open http://localhost:8081/swagger-ui.html
```

---

**Fim do SDD V3.0 Definitivo**
