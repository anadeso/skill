# Clean Code - Resumo dos Princípios

## Baseado em "Clean Code: A Handbook of Agile Software Craftsmanship" por Robert C. Martin

Este documento resume os principais princípios do livro "Código Limpo" utilizados para análise de qualidade de código.

### Capítulo 2: Meaningful Names (Nomes Significativos)

**Princípios:**
- Use nomes que revelam intenção
- Evite desinformação
- Use nomes pronunciáveis
- Use nomes que podem ser pesquisados
- Evite notação (prefixos/sufixos desnecessários)
- Evite confusion mental (usar nomes claros)
- Use nomes para classes (substantivos): `Customer`, `WikiPage`, `Account`
- Use nomes de ação para métodos (verbos): `postPayment()`, `deletePage()`, `save()`
- Não seja fofo - use nomes sérios

**Antipadrões:**
- Single-letter variables (exceto índices de loop)
- Nomes ambíguos como `data`, `obj`, `temp`, `foo`
- Nomes muito similares que confundem
- Magic numbers sem explicação
- Abreviações não padronizadas

### Capítulo 3: Functions (Funções)

**Princípios:**
- Funções devem ser pequenas (idealmente < 20 linhas)
- Uma única responsabilidade (fazer uma coisa bem)
- Um nível de abstração por função
- Leitura top-down: código deve ler como narrativa
- Use nomes descritivos
- Parâmetros em ordem de preferência:
  - **Niladic (0)**: Ideal - sem parâmetros
  - **Monadic (1)**: Bom - um parâmetro
  - **Dyadic (2)**: Aceitável - dois parâmetros
  - **Triadic (3+)**: Evitar - difícil de entender
  - **4+ parâmetros**: Problemático - considere refatorar
- Sem parâmetros de saída
- Sem efeitos colaterais
- Use exceções ao invés de códigos de erro
- DRY - Don't Repeat Yourself

**Antipadrões:**
- Funções muito longas
- Flag parameters
- Muitos parâmetros
- Funções fazendo múltiplas coisas
- Efeitos colaterais escondidos
- Complexidade ciclomática alta

### Capítulo 4: Comments (Comentários)

**Princípios:**
- Bom código não precisa de comentários
- O código deve ser auto-explicativo
- Comentários devem explicar o POR QUÊ, não o QUÊ
- Use comentários apenas quando necessário
- Mantenha comentários atualizados
- Evite comentários óbvios

**Antipadrões:**
- Comentários que apenas repetem o código
- Comentários obsoletos ou conflitantes
- TODO/FIXME deixados para trás
- Comentários de região
- Comentários de Javadoc desnecessários

### Capítulo 5: Formatting (Formatação)

**Princípios:**
- Código deve ser bem formatado
- Conceitos relacionados próximos
- Conceitos não-relacionados separados
- Linhas não muito longas (80-120 caracteres)
- Indentação consistente
- Espaçamento inteligente
- Quebras de linha estratégicas
- Organização lógica de membros de classe

**Antipadrões:**
- Indentação inconsistente
- Nesting excessivo
- Linhas muito longas
- Falta de espaçamento
- Organização ilógica

### Capítulo 6: Objects and Data Structures (Objetos e Estruturas de Dados)

**Princípios:**
- Classes devem ser pequenas e focadas
- Separação entre classes com dados públicos vs métodos
- Evitar feature envy (acessar dados de outros objetos)
- Evitar data clumps (dados relacionados que devem estar juntos)
- Preferir objetos que escondem implementação
- Objects: hide data, expose behavior
- Data structures: expose data, minimal behavior

**Antipadrões:**
- Classes muito grandes
- Muitos métodos públicos
- Data classes sem comportamento
- Feature envy
- Violação de encapsulamento

### Capítulo 7: Error Handling (Tratamento de Erros)

**Princípios:**
- Use exceções, não códigos de erro
- Forneça contexto nas exceções
- Defina exceções de acordo com como você quer capturá-las
- Não retorne `null`
- Não passe `null` como parâmetro
- Use o padrão Optional em linguagens modernas
- Limpe recursos (finally, try-with-resources)
- Exceções específicas são melhores que genéricas

**Antipadrões:**
- Bare except/catch
- Retornar null
- Passar null como parâmetro
- Silent exception swallowing
- Logging e retorno de erro
- Exceções muito genéricas

### Princípios Gerais (ao longo do livro)

**DRY - Don't Repeat Yourself**
- Evite duplicação de código
- Extraia abstrações comuns
- Reutilize componentes

**SOLID Principles:**
- Single Responsibility: uma classe, uma razão para mudar
- Open/Closed: aberta para extensão, fechada para modificação
- Liskov Substitution: subtipas devem ser substituíveis
- Interface Segregation: interfaces específicas para clientes
- Dependency Inversion: dependa de abstrações, não de concreções

**Emergent Design:**
- Deixe o design emergir através de TDD
- Refatore constantemente
- Mantenha o código simples

### Capítulo 8: Boundaries (Limites)

**Princípios:**
- Use padrões wrapper/adapter para dependências externas
- Testes de aprendizado para entender código de terceiros
- Isole código de terceiros da lógica de negócio
- Controle dependências através de interfaces
- Evite vazar código de terceiros no seu domínio

**Antipadrões:**
- Dependência direta em bibliotecas externas espalhadas
- Código de terceiros misturado com lógica do negócio
- Difícil de substituir ou atualizar dependências
- Sem camada de abstração sobre código externo

### Capítulo 9: Unit Tests (Testes Unitários)

**Princípios:**
- Testes são tão importantes quanto código de produção
- Princípio F.I.R.S.T:
  - **Fast** (Rápido): Testes devem rodar rapidamente
  - **Independent** (Independente): Sem dependências entre testes
  - **Repeatable** (Repetível): Roda em qualquer ambiente
  - **Self-Checking** (Auto-verificável): Passa ou falha claramente
  - **Timely** (Oportuno): Escrito perto do código de produção
- Três Leis do TDD:
  - Não escreva código de produção sem teste falhando
  - Não escreva mais teste que o necessário para falhar
  - Não escreva mais código que o necessário para passar
- Um conceito por teste
- Nomes de teste revelando o que está sendo testado
- Evite poluição entre testes e setup complexo

**Antipadrões:**
- Testes faltando
- Testes que dependem uns dos outros
- Testes lentos
- Nomes de testes pouco claros
- Muitas assertions por teste
- Setup de testes muito complexo
- Testes que não verificam comportamento real

### Capítulo 13: Concurrency (Concorrência)

**Princípios:**
- Concorrência é difícil - minimize quando possível
- Mantenha código de concorrência separado da lógica
- Entenda mecanismos: threading, locks, semaphores
- Proteja dados compartilhados com sincronização
- Conheça riscos: race conditions, deadlocks, starvation
- Use coleções thread-safe e padrões modernos
- Teste código concorrente minuciosamente

**Antipadrões:**
- Estado mutável compartilhado desprotegido
- Concorrência misturada com lógica de negócio
- Primitivas de sincronização faltando
- Potencial para deadlocks
- Race conditions
- Thread pools sem gerenciamento apropriado
- Testes inadequados de código concorrente

### Capítulo 17: Heuristics (Heurísticas)

**Regras de Nomenclatura:**
- Use nomes do domínio do problema
- Evite desinformação em nomes
- Use distinções significativas
- Use nomes pronunciáveis
- Evite codificação em nomes (notação húngara)
- Evite mapeamento mental
- Uma palavra por conceito
- Adicione contexto significativo
- Não adicione contexto gratuito

**Regras de Função:**
- Evite side effects
- Não passe flags para funções
- Use exceções ao invés de códigos de retorno
- Extraia try/catch em funções separadas
- Tratamento de erro é uma coisa

**Regras de Comentários:**
- Evite comentários redundantes
- Não comente código ruim - reescreva-o
- Não comente código óbvio
- Não use comentários em chaves de fechamento
- Não comente código não-utilizado - delete-o
- Use comentários para explicar regras de negócio
- Use comentários para avisos

**Regras de Formatação:**
- Mantenha linhas curtas
- Use espaçamento significativamente
- Não quebre indentação
- Espaço ao redor de operadores
- Sem espaços em branco no final
- Alinhe itens similares

**Regras de Objetos & Estruturas:**
- Esconda estrutura interna
- Prefira objetos sobre dados primitivos
- Evite feature envy
- Evite data clumps
- Mantenha dados relacionados juntos
- Separe dados não-relacionados

### Capítulos 14-16: Estudos de Caso Práticos

- **Capítulo 14 - Args**: Parsing de argumentos de linha de comando - demonstra refatoração para claridade
- **Capítulo 15 - JUnit**: Refatoração de framework de testes - exemplo real de refatoração
- **Capítulo 16 - SerialDate**: Melhoria de código de produção - estudo de caso abrangente

Estes capítulos ilustram como aplicar princípios de Código Limpo através de refatoração abrangente em código real de produção.

## Como Usar Este Guia

Ao analisar código, procure por violações destes princípios:
1. Verifique naming - são nomes significativos e reveladores de intenção?
2. Analise tamanho de funções - estão muito grandes ou complexas?
3. Revise comentários - são necessários ou óbvios?
4. Avalie formatação - é consistente e legível?
5. Verifique tratamento de erros - usa exceções apropriadamente?
6. Procure duplication - há código repetido que deveria ser abstraído?
7. Analise estrutura de classes - responsabilidade única? Bem encapsuladas?

## Referência Rápida de Severidade

**Alto (Critical):**
- Códigos de erro ao invés de exceções
- **4+ parâmetros em funções** (devem ter idealmente 0-1, máximo 2-3)
- Funções muito grandes (>50 linhas)
- Magic numbers/strings espalhados
- Bare exception handlers
- Retornar/passar null sem pattern
- Race conditions em código concorrente
- Acoplamento direto a dependências externas (sem abstração)
- Código de terceiros espalhado na lógica de negócio
- Testes com múltiplas assertions ou dependências

**Médio (Warning):**
- Nomes ambíguos ou pouco claros
- Comentários óbvios
- Alguma duplicação
- Classes com múltiplas responsabilidades
- Alguns efeitos colaterais
- Testes lentos ou complexos
- Falta de sincronização em código concorrente
- Flag parameters em funções
- Feature envy (acessar dados de outro objeto)

**Baixo (Info):**
- Formatação inconsistente
- Nomes poderiam ser melhores
- Refatoração oportunista
- Melhorias de estilo
- Melhor organização de membros de classe
- Sugestões de usar padrões de design

## Parâmetros Ideais por Função

```
Niladic (0 params):      ████████████ ← Ideal
Monadic (1 param):       ████████     ← Bom
Dyadic (2 params):       ███████      ← Aceitável
Triadic (3+ params):     ████         ← Evitar
4+ params:               ██           ← Problemático - refatore
```

A regra: quanto menos parâmetros, melhor a testabilidade e legibilidade.
