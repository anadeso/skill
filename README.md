# Skills de Análise e Revisão de Código

Este repositório contém duas skills especializadas para Claude Code que ajudam na análise de qualidade de documentação e código:

- **Critical Review** - Revisão de documentação técnica e especificações
- **Clean Code Analyzer** - Análise de qualidade de código baseada em Clean Code (17 capítulos, 55+ heurísticas, 21 testes)

## 🎯 Visão Geral do Projeto

Um projeto de desenvolvimento de skills para Claude Code com foco em:
- Análise crítica de documentação técnica
- Avaliação de qualidade de código baseada em Clean Code
- Framework de desenvolvimento de skills (`skill-creator`)
- Testes abrangentes e iteração contínua

---

## 📋 Critical Review Skill

A skill **Critical Review** analisa documentação técnica de forma sistemática para identificar problemas de qualidade que podem causar confusão, má interpretação ou erros de implementação.

### O Que Detecta

#### 1. **Contradições**
Declarações que entram em conflito entre si:
- "A API retorna JSON" vs "respostas são em XML"
- "Campo X é obrigatório" vs schema mostra como opcional
- Diferentes seções descrevem o mesmo comportamento de formas diferentes
- Implementação difere do comportamento documentado

#### 2. **Ambiguidades**
Linguagem vaga, termos não definidos ou múltiplas interpretações:
- Termos indefinidos: "trate erros gracefully" (o que conta como gracioso?)
- Medidas vagas: "deve ser rápido" (qual a latência alvo?)
- Condicionais não claros: "se necessário" (quando?)
- Especificidades faltantes: "use práticas padrão" (quais?)

#### 3. **Inconsistências**
Nomes, formatos ou convenções diferentes para o mesmo conceito:
- Nomes de parâmetros variam: `user_id`, `userId`, `id`
- Formatos de endpoints inconsistentes: `/users/{id}/posts` vs `/user/posts/{id}`
- Formatos de tempo mistos: ISO 8601 vs timestamps Unix
- Convenções de nomenclatura inconsistentes: `getUser()` vs `fetch_user()`

#### 4. **Lacunas Lógicas**
Passos faltantes, explicações incompletas, quebras no raciocínio:
- Fluxo descrito como "Passo 1 → Passo 2 → Passo 4" (Passo 3 faltando)
- Tratamento de erro mencionado mas processo de recuperação não definido
- Pré-requisitos mencionados sem instruções de configuração
- Dependências circulares que não podem ser resolvidas

### Como Usar

Invoque esta skill quando precisar:
- Revisar especificações de API para problemas
- Validar documentação de requisitos
- Analisar guias de implementação
- Verificar documentação de design técnico
- Auditar especificações de projeto

**Exemplos de acionamento:**
```
"Review this API spec for issues"
"Analyze this requirements document for contradictions"
"Check my specification for ambiguities"
"Validate this technical documentation"
```

### Formato de Saída

A análise é estruturada em seções claras:

```markdown
# Critical Review: [Título/Tipo do Documento]

## Summary
[2-3 sentenças descrevendo o documento e seu escopo]

## Contradictions
- **[Termo/Conceito]**: [Descrição do conflito]
  - Location 1: [Onde a primeira declaração aparece]
  - Location 2: [Onde a declaração conflitante aparece]
  - Impact: [Por que essa contradição importa]

## Ambiguities
- **[Termo vago ou conceito]**: [Explicação do que é pouco claro]
  - Issue: [Especificamente o que poderia ser mal interpretado]
  - Questions: [O que precisa de clarificação]

## Inconsistencies
- **[Conceito]**: [Descrição das variações encontradas]
  - Variant 1: [Primeira forma usada]
  - Variant 2: [Forma diferente usada]
  - Locations: [Onde cada variação aparece]

## Logical Gaps
- **[Processo/Seção]**: [Descrição do que está faltando]
  - Missing piece: [O que deveria estar lá]
  - Location: [Onde a lacuna ocorre]
  - Impact: [Por que essa lacuna importa]

## Overall Assessment
[Resumo breve: "Bem estruturado com inconsistências menores" ou "Múltiplas contradições críticas precisam ser resolvidas"]

## Recommendations
[Sugestões específicas e acionáveis para melhorar a documentação]
```

---

## 🧹 Clean Code Analyzer Skill

A skill **Clean Code Analyzer** analisa código para identificar problemas de qualidade e manutenibilidade baseados nos princípios do livro **"Clean Code: A Handbook of Agile Software Craftsmanship"** de Robert C. Martin.

**Características:**
- 📚 **17 Capítulos** cobertos completamente
- 📋 **55+ Heurísticas** numeradas e organizadas (G, N, F, C, T rules)
- 🧪 **21 Casos de Teste** em 7+ linguagens de programação
- ✅ **100% Alinhado** com a estrutura original do livro
- 🔍 **12 Categorias** de análise

### Capítulos Cobertos

| Cap. | Título | Status |
|------|--------|--------|
| 2 | Meaningful Names (Nomes Significativos) | ✅ Completo |
| 3 | Functions (Funções) | ✅ Completo |
| 4 | Comments (Comentários) | ✅ Completo |
| 5 | Formatting (Formatação) | ✅ Completo |
| 6 | Classes & Objects (Objetos) | ✅ Completo |
| 7 | Error Handling (Tratamento de Erros) | ✅ Completo |
| 8 | Boundaries (Limites) | ✅ Completo |
| 9 | Unit Tests (Testes Unitários) | ✅ Completo |
| 10 | Classes (Organização de Classes) | ✅ Completo |
| 11 | Systems (Arquitetura de Sistemas) | ✅ Completo |
| 12 | Emergence (Regras de Kent Beck) | ✅ Completo |
| 13 | Concurrency (Concorrência) | ✅ Completo |
| 14-16 | Case Studies (Args, JUnit, SerialDate) | ✅ Referenciados |
| 17 | Heuristics (55+ Heurísticas Numeradas) | ✅ Completo |

### Heurísticas Numeradas

A skill detecta e relata **55+ heurísticas específicas** do Capítulo 17:

**G Rules (Gerais - G1 a G36)**: 36 heurísticas
- **G1-G10**: Organização de código, duplicação, abstração
- **G11-G20**: Nomenclatura, clareza, compreensão
- **G21-G28**: Dependências, polimorfismo, tratamento de erros
- **G29-G36**: Condicionais, efeitos colaterais, acoplamento temporal, convenções, limites, abstração

**N Rules (Nomenclatura - N1 a N7)**: 7 heurísticas de nomenclatura

**F Rules (Funções - F1 a F4)**: 4 heurísticas de design de funções

**C Rules (Comentários - C1 a C5)**: 5 heurísticas de comentários

**T Rules (Testes - T1 a T9)**: 9 heurísticas de testes

### Áreas de Análise

#### 1. **Meaningful Names** (Capítulo 2)
- Variáveis, funções e classes devem ter nomes claros que revelam intenção
- Evitar desinformação, adicionar contexto significativo
- Usar nomes pronunciáveis
- Métodos devem ter nomes de ação (verbos)
- Classes devem ter nomes (substantivos)

**Problemas procurados:**
- Single-letter variable names (exceto índices de loop)
- Nomes ambíguos ou pouco claros
- Magic numbers sem constantes nomeadas
- Convenções de nomenclatura inconsistentes

#### 2. **Functions** (Capítulo 3)
- Funções pequenas (idealmente < 20 linhas)
- Uma única responsabilidade
- Um nível de abstração por função
- Evitar listas de parâmetros longas

**Parâmetros ideais:**
- **Niladic (0)**: Ideal - sem parâmetros
- **Monadic (1)**: Bom - um parâmetro
- **Dyadic (2)**: Aceitável - dois parâmetros
- **Triadic (3+)**: Evitar - difícil de entender
- **4+ parâmetros**: Problemático - refatore!

**Problemas procurados:**
- Funções muito longas
- Funções fazendo múltiplas coisas
- Alta complexidade ciclomática
- Muitos parâmetros
- Funções com efeitos colaterais

#### 3. **Comments** (Capítulo 4)
- Bom código não precisa comentários - deve ser auto-explicativo
- Comentários devem explicar POR QUÊ, não O QUÊ
- Evitar comentários redundantes, enganosos ou desatualizados

**Problemas procurados:**
- Comentários óbvios que apenas repetem código
- Falta de documentação crítica
- TODO/FIXME deixados para trás
- Comentários sobre o que o código faz

#### 4. **Formatting** (Capítulo 5)
- Código bem formatado para legibilidade
- Conceitos relacionados próximos
- Conceitos não-relacionados separados por linhas em branco
- Indentação e espaçamento consistentes

**Problemas procurados:**
- Indentação inconsistente
- Nesting excessivo
- Linhas muito longas
- Organização lógica ruim de membros de classe

#### 5. **Error Handling** (Capítulo 7)
- Usar exceções ao invés de códigos de erro
- Fornecer contexto nas mensagens de exceção
- Evitar retornar null
- Usar padrão Optional em linguagens modernas

**Problemas procurados:**
- Bare except/catch blocks
- Exceções silenciosas
- Retornando null ou códigos de erro
- Mensagens de exceção sem contexto
- Falta de limpeza de recursos

#### 6. **Code Structure & DRY** (Princípio DRY)
- Don't Repeat Yourself (DRY)
- Evitar valores hardcoded
- Manter funções no mesmo nível de abstração
- Minimizar acoplamento entre módulos

**Problemas procurados:**
- Duplicação de código
- Magic strings ou numbers
- Alto acoplamento/baixa coesão
- Violação do Single Responsibility Principle

#### 7. **Classes & Objects** (Capítulo 6)
- Classes pequenas e focadas
- Mais métodos privados que públicos
- Evitar "feature envy" (acessar dados de outros objetos)
- Evitar "data clumps" (dados relacionados dispersos)

**Problemas procurados:**
- Classes muito grandes
- Muitos métodos públicos
- Falta de encapsulamento
- Violação de responsabilidade única

#### 8. **Boundaries** (Capítulo 8)
- Usar padrões wrapper/adapter para dependências externas
- Isolar código de terceiros da lógica de negócio
- Controlar dependências através de interfaces

**Problemas procurados:**
- Dependência direta em bibliotecas externas
- Código de terceiros espalhado
- Sem camada de abstração

#### 9. **Testing** (Capítulo 9)
- Testes são tão importantes quanto código de produção
- Princípio F.I.R.S.T: Fast, Independent, Repeatable, Self-Checking, Timely
- Um conceito por teste
- Nomes de testes que revelam o que está sendo testado

**Problemas procurados:**
- Cobertura de testes faltando
- Testes que dependem um do outro
- Testes lentos
- Múltiplas assertions por teste
- Setup muito complexo

#### 10. **Concurrency** (Capítulo 13)
- Concorrência é difícil - minimize quando possível
- Mantenha código de concorrência separado
- Proteja estado compartilhado com sincronização
- Teste código concorrente minuciosamente

**Problemas procurados:**
- Estado mutável compartilhado desprotegido
- Race conditions
- Deadlocks potenciais
- Falta de primitivas de sincronização

#### 11. **Heuristics** (Capítulo 17)
- Regras avançadas de nomenclatura, funções, comentários e formatação
- Padrões práticos de refatoração

### Como Usar

Invoque esta skill quando precisar:
- Revisar código quanto a problemas de qualidade
- Identificar oportunidades de refatoração
- Verificar conformidade com princípios de Clean Code
- Obter sugestões para melhorar legibilidade
- Analisar débito técnico

**Exemplos de acionamento:**
```
"Review this function for clean code issues"
"Analyze this class for code quality problems"
"Check my code for Clean Code violations"
"Help me identify refactoring opportunities"
"Improve code readability"
```

### Formato de Saída

A análise é estruturada por categorias:

```markdown
### Code Quality Issues

#### Naming Problems
- **Issue**: [Problema específico com nomes]
- **Location**: [arquivo/linha se possível]
- **Severity**: High/Medium/Low
- **Suggestion**: [Como corrigir]

#### Function Issues
- **Issue**: [Problema com design de função]
...

#### [Outras categorias]
...

### Summary
- **Total Issues Found**: [contagem]
- **Critical Issues**: [contagem]
- **Overall Code Quality**: [avaliação]
- **Top Priority Fixes**: [2-3 melhorias mais impactantes]
```

### Referência de Severidade

**Alto (Critical):**
- 4+ parâmetros em funções (devem ter 0-1, máximo 2-3)
- Funções muito grandes (>50 linhas)
- Magic numbers/strings espalhados
- Bare exception handlers
- Retornar/passar null sem padrão
- Race conditions em código concorrente

**Médio (Warning):**
- Nomes ambíguos ou pouco claros
- Comentários óbvios
- Alguma duplicação
- Classes com múltiplas responsabilidades
- Testes lentos ou complexos

**Baixo (Info):**
- Formatação inconsistente
- Nomes que poderiam ser melhores
- Sugestões de padrões de design
- Melhorias de estilo

---

## 📈 Evolução e Fases de Desenvolvimento

### Fase 1: Correções Iniciais
- ✅ Correção de parâmetros: "máximo 4" → "idealmente 0-1, máximo 2-3"
- ✅ Adição dos Capítulos 8, 9, 13 (Boundaries, Testing, Concurrency)
- ✅ Expansão de 10 para 15 testes

### Fase 2: Cobertura Expandida
- ✅ Capítulo 11 (Systems) - Dependência de injeção, arquitetura
- ✅ Capítulo 12 (Emergence) - Regras de Kent Beck
- ✅ Capítulo 17 (Heuristics) - 55+ heurísticas numeradas (G, N, F, C, T rules)
- ✅ Expansão para 20 testes
- ✅ Documentação em português

### Fase 3: Precisão e Refinamento Final
- ✅ Reorganização de G29-G36 (heurísticas de testes removidas, regras gerais adicionadas)
- ✅ Refinamento de G22 para contexto de type checking
- ✅ Capítulo 10 completamente integrado (Classes, SRP, Coesão)
- ✅ Expansão para 21 testes
- ✅ 100% alinhado com estrutura original do livro
- ✅ Pronto para produção

**Status**: ✅ **COMPLETO E VERIFICADO**

## 📁 Estrutura do Repositório

```
6.1-criando-skills/
├── README.md                                  # Este arquivo
├── CLAUDE.md                                  # Instruções do projeto
├── prompt.md                                  # Requisitos originais da skill
├── skills-lock.json                           # Dependências do projeto (skill-creator)
│
├── .claude/
│   └── skills/
│       ├── critical-review/                   # Skill de revisão crítica
│       │   └── SKILL.md                       # Definição e instruções
│       │
│       └── skill-creator/                     # Framework de desenvolvimento de skills
│           ├── SKILL.md                       # Workflow de 4 fases
│           ├── scripts/                       # Ferramentas de desenvolvimento
│           │   ├── run_eval.py                # Runner de testes
│           │   ├── quick_validate.py          # Validação rápida
│           │   └── ...                        # Outras ferramentas
│           ├── eval-viewer/                   # Visualizador HTML de testes
│           ├── agents/                        # Agentes de avaliação especializados
│           └── references/                    # Schemas e documentação
│
├── clean-code-skill/                          # Skill de análise de código
│   ├── SKILL.md                               # Definição da skill (17 caps)
│   ├── README.md                              # Documentação da skill
│   ├── IMPROVEMENTS_LOG.md                    # Log de melhorias (fases 1-2)
│   ├── FINAL_ADJUSTMENTS.md                   # Ajustes finais (fase 3)
│   │
│   ├── evals/
│   │   └── evals.json                         # 21 casos de teste
│   │
│   └── references/
│       └── clean_code_summary.md              # Resumo dos 17 capítulos
│                                              # (em português)
│
└── [espaço para novos skills]
```

---

## 🚀 Começando

### Para Usar Critical Review

1. **Prepare sua documentação** em um arquivo ou no prompt
2. **Solicite uma revisão crítica**:
   ```
   "Review this API specification for quality issues"
   ```
3. **Analise o relatório estruturado** com as quatro categorias de problemas
4. **Implemente as recomendações** identificadas

### Para Usar Clean Code Analyzer

1. **Prepare seu código** (colar no prompt ou fornecer arquivo)
2. **Solicite análise de qualidade**:
   ```
   "Analyze this code for Clean Code violations"
   ```
3. **Revise os problemas identificados** por categoria e severidade
4. **Implemente as sugestões** começando pelos problemas críticos

---

## 📚 Referências Detalhadas

### Critical Review
**Arquivo**: `.claude/skills/critical-review/SKILL.md`
- Baseada em padrões sistemáticos de revisão de documentação
- Focada em 4 tipos principais de problemas
- Orientada para documentação técnica, especificações, requisitos, design docs

### Clean Code Analyzer
**Arquivo Principal**: `clean-code-skill/SKILL.md`
**Referência**: `clean-code-skill/references/clean_code_summary.md` (PT-BR)
**Log de Melhorias**: `clean-code-skill/IMPROVEMENTS_LOG.md`
**Ajustes Finais**: `clean-code-skill/FINAL_ADJUSTMENTS.md`
**Testes**: `clean-code-skill/evals/evals.json` (21 casos)

**Baseada em**: "Clean Code: A Handbook of Agile Software Craftsmanship" por Robert C. Martin

**Todos 17 Capítulos Cobertos**:
- Capítulos 2-13: Princípios principais
- Capítulos 14-16: Case studies (Args, JUnit, SerialDate)
- Capítulo 17: 55+ heurísticas numeradas (G, N, F, C, T rules)

**Teste Coverage**: 21 casos em 7+ linguagens de programação

### Estrutura de Testes

**clean-code-skill/evals/evals.json**:
- 21 casos de teste abrangentes
- Cobre todos os 17 capítulos
- Múltiplas linguagens (Python, JavaScript, Java, TypeScript, Go, C#, Ruby)
- Inclui testes de:
  - Nomes significativos
  - Design de funções
  - Comentários
  - Formatação
  - Tratamento de erros
  - Estrutura de código (DRY)
  - Design de classes
  - Limites e dependências externas
  - Testes
  - Concorrência
  - Heurísticas avançadas
  - Sistemas e emergence

---

## 🔧 Desenvolvimento e Framework

Este projeto usa o **skill-creator**, um framework de desenvolvimento de skills com as seguintes características:

### Workflow de 4 Fases (skill-creator)

1. **Capture Intent & Draft** - Definir objetivo e criar SKILL.md
2. **Test & Evaluate** - Criar testes e avaliar com/sem skill
3. **Improve Based on Feedback** - Iterar baseado em resultados
4. **Optimize Description** - Otimizar para melhor detecção automática

### Iterações do Clean Code Analyzer

O **clean-code-skill** passou por 3 fases de desenvolvimento:

**Fase 1** - Correções iniciais com feedback de usuário
- Ver: `IMPROVEMENTS_LOG.md` (Fases 1 e 2)
- Correções factuais e expansão de cobertura

**Fase 2** - Cobertura expandida (capítulos 11-12, 55+ heurísticas)
- Ver: `IMPROVEMENTS_LOG.md` (Fases 1 e 2)
- Documentação em português adicionada

**Fase 3** - Precisão final e refinamento
- Ver: `FINAL_ADJUSTMENTS.md`
- 100% alinhado com livro original
- Status: ✅ Pronto para produção

### Para Trabalhar com as Skills

1. **Revisar SKILL.md** - Definição e instruções
2. **Consultar logs** - `IMPROVEMENTS_LOG.md` e `FINAL_ADJUSTMENTS.md`
3. **Executar testes** - `evals/evals.json` (21 testes para Clean Code)
4. **Usar referências** - `references/clean_code_summary.md` (resumo completo)

Veja `CLAUDE.md` para instruções completas do projeto.

---

## 📧 Contato & Feedback

Desenvolvido como parte do MBA IA - Desenvolvimento de Aplicação IA
Email: anadeso90@gmail.com

Para melhorias ou sugestões, considere:
- Revisar a estrutura de skills
- Adicionar novos casos de teste
- Expandir cobertura de análise
- Otimizar descrições para melhor detecção automática

---

## 📊 Status do Projeto

| Componente | Status | Detalhes |
|-----------|--------|----------|
| **Critical Review** | ✅ Completo | 1 skill, 4 tipos de problemas |
| **Clean Code Analyzer** | ✅ Completo | 17 capítulos, 55+ heurísticas, 21 testes |
| **Framework (skill-creator)** | ✅ Integrado | 4 fases de desenvolvimento |
| **Documentação** | ✅ Bilíngue | PT-BR e EN-US |
| **Cobertura de Testes** | ✅ Abrangente | 7+ linguagens, 12+ categorias |
| **Alinhamento com Livro** | ✅ 100% | Verificado contra original |

## 📝 Notas Importantes

- **Critical Review** é otimizado para documentação técnica, especificações, requisitos e design docs
- **Clean Code Analyzer** é específico para análise de código fonte em múltiplas linguagens
- Ambas podem ser usadas em complementação para ciclo completo de QA
- As skills usam descritores detalhados e exemplos concretos para máxima precisão
- O framework skill-creator permite iteração contínua e melhoria baseada em feedback

## 🚀 Próximos Passos

1. **Avaliação em Produção** - Testar skills com usuários reais
2. **Otimização de Triggers** - Melhorar detecção automática via skill-creator
3. **Expansão de Skills** - Desenvolver novos skills usando o framework
4. **Integração** - Conectar com outros sistemas de QA

## 🔗 Arquivos Principais para Referência

| Arquivo | Propósito |
|---------|-----------|
| `CLAUDE.md` | Instruções e contexto do projeto |
| `prompt.md` | Requisitos originais |
| `clean-code-skill/SKILL.md` | Definição completa da skill |
| `clean-code-skill/IMPROVEMENTS_LOG.md` | Histórico de melhorias |
| `clean-code-skill/FINAL_ADJUSTMENTS.md` | Ajustes finais e verificação |
| `clean-code-skill/references/clean_code_summary.md` | Referência completa em PT-BR |
| `.claude/skills/critical-review/SKILL.md` | Definição do critical review |

---

**Última atualização**: 17 de maio de 2026  
**Status Geral**: ✅ Pronto para uso e avaliação  
**Desenvolvido por**: MBA IA - Desenvolvimento de Aplicação IA
