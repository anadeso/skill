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

### Capítulo 10: Classes (Classes)

**Princípios:**
- Mantenha classes pequenas - Single Responsibility Principle (SRP)
- Nome da classe deve descrever seu propósito
- Meça tamanho de classe por número de responsabilidades
- Classes devem ter alta coesão (métodos e campos relacionados)
- Organize métodos apropriadamente (público antes de privado)
- Classes devem ser organizadas para mudança
- Evite "god classes" com muitas responsabilidades
- Variáveis de instância devem ser privadas
- Métodos devem trabalhar com dados da classe
- Dependências devem estar claras no topo

**Antipadrões:**
- Classes muito grandes (múltiplas responsabilidades)
- Baixa coesão - métodos não-relacionados
- Organização ruim de membros
- Variáveis de instância públicas
- Muitas variáveis de instância
- Métodos que não usam dados da classe
- Propósito da classe pouco claro
- Difícil de estender ou modificar
- Métodos espalhados sem agrupamento lógico
- Comentários necessários para explicar organização

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

### Capítulo 11: Systems (Sistemas)

**Princípios:**
- Separe construção de uso de objetos
- Injeção de dependência para gerenciar dependências
- Factories e dependency containers
- Cross-cutting concerns via AOP ou middleware
- Evolução de sistema - design para mudança
- Escale de simples para complexo gradualmente
- Evite otimização prematura
- Use convenções de nomenclatura para revelar intenção
- Mantenha arquitetura do sistema visível no código
- Desacople subsistemas

**Antipadrões:**
- Misturar construção com lógica de negócio
- Dependências hard-wired espalhadas
- Sem injeção de dependência ou IoC
- Factories não usadas para criação complexa
- Cross-cutting concerns espalhados
- Sem clara separação de conceitos
- Módulos acoplados
- Arquitetura difícil de entender
- Configuração misturada com lógica
- Difícil de substituir componentes

### Capítulo 12: Emergence (Emergência)

**As 4 Regras de Kent Beck para Design Simples (em prioridade):**
1. **Todos os testes passam** - Código deve ser funcional e correto
2. **Sem duplicação** - DRY principle, eliminar repetição
3. **Expressa intenção** - Código é claro, auto-documentado
4. **Mínimo de classes/métodos** - Fewest elements possible

Estas regras aplicadas iterativamente levam a design emergente sem over-engineering.

**Antipadrões:**
- Testes falhando ou faltando
- Código duplicado e lógica repetida
- Código que obscurece intenção
- Soluções over-engineered com classes desnecessárias
- Abstração prematura
- Classes/métodos sem propósito claro
- Complexidade que não agrega valor

### Capítulo 17: Heuristics (Heurísticas - 55+ Regras Numeradas)

**Regras G (Gerais - G1 a G36):**
- **G1**: Múltiplas linguagens em um arquivo - use uma por arquivo
- **G2**: Comportamento óbvio não implementado - faça o que é esperado
- **G3**: Comportamento de limite incorreto - trate casos extremos
- **G4**: Segurança/guarda sobrescrita - não desabilite features de segurança
- **G5**: Duplicação - aplique DRY rigorosamente
- **G6**: Código no nível de abstração errado - mantenha consistência
- **G7**: Muitos parâmetros - idealmente 0-1, máximo 2-3, nunca 4+
- **G8**: Código morto - delete imediatamente
- **G9**: Separação vertical - coloque conceitos relacionados juntos
- **G10**: Inconsistência - seja consistente em operações similares
- **G11**: Bagunça - remova variáveis/funções sem propósito
- **G12**: Acoplamento artificial - não acople coisas não-relacionadas
- **G13**: Feature envy - não acesse internals de outro objeto
- **G14**: Argumentos seletores (flags) - divida a função
- **G15**: Intenção obscurecida - torne a intenção clara
- **G16**: Responsabilidade deslocada - coloque código onde é esperado
- **G17**: Static inapropriado - prefira não-static quando possível
- **G18**: Use variáveis explicativas - extraia para variáveis nomeadas
- **G19**: Nomes de função devem explicar o que fazem - nomes descritivos
- **G20**: Entenda o algoritmo - saiba o que o código faz
- **G21**: Torne dependências lógicas físicas - mostre dependências
- **G22**: Prefira polimorfismo a if/else para type checking - não é regra absoluta para todo if/else
- **G23**: Prefira exceções a códigos de retorno - use exceções
- **G24**: Extraia try/catch blocks - mantenha tratamento separado
- **G25**: Não retorne null - lance exceção ou use Optional
- **G26**: Não passe null - evite parâmetros null
- **G27**: Evite encoding - sem notação húngara
- **G28**: Nomes devem expressar intenção - nomes significativos
- **G29**: Evite condicionais negativas - use forma positiva (ex: if valid ao invés de if not invalid)
- **G30**: Funções sem side effects - seja previsível
- **G31**: Acoplamento temporal oculto - revele dependências
- **G32**: Não seja arbitrário - escolha convenções por boas razões
- **G33**: Encapsule condições-limite - centralize tratamento
- **G34**: Funções devem descer um nível de abstração - mantenha coesão
- **G35**: Mantenha dados configuráveis em níveis altos - configuração acima implementação
- **G36**: Evite navegação transitiva - não encadeie chamadas (Lei de Demeter)

**Regras N (Nomes - N1 a N7):**
- **N1**: Escolha nomes descritivos - clareza é essencial
- **N2**: Nomes em nível apropriado de abstração - linguagem do domínio
- **N3**: Use nomenclatura padrão - siga convenções da indústria
- **N4**: Nomes não-ambíguos - sem possibilidade de confusão
- **N5**: Use nomes longos para escopos longos - curtos para curtos
- **N6**: Evite encoding - nomes, não códigos
- **N7**: Nomes devem descrever efeitos colaterais - revele o que faz

**Regras F (Funções - F1 a F4):**
- **F1**: Muitos argumentos - reduza contagem de parâmetros
- **F2**: Argumentos de saída - use valores de retorno
- **F3**: Argumentos flag - divida a função, não use flags booleanas
- **F4**: Funções mortas - delete funções não-usadas

**Regras C (Comentários - C1 a C5):**
- **C1**: Informação inapropriada - comentários para intenção, não fatos
- **C2**: Comentário obsoleto - mantenha comentários atualizados
- **C3**: Comentários redundantes - não explique código óbvio
- **C4**: Comentários mal escritos - escreva claramente ou não escreva
- **C5**: Código comentado - delete, use version control

**Regras T (Testes - T1 a T9):**
- **T1**: Testes insuficientes - cubra todos os caminhos
- **T2**: Use ferramenta de cobertura - conheça percentual de cobertura
- **T3**: Não pule testes triviais - teste tudo
- **T4**: Teste ignorado - corrija ou delete, não ignore
- **T5**: Teste condições-limite - casos extremos importam
- **T6**: Teste exaustivamente perto de bugs - áreas bug-prone
- **T7**: Padrões de falha são reveladores - analise padrões
- **T8**: Padrões de cobertura de teste - cobertura uniforme
- **T9**: Testes devem ser rápidos - testes lentos não são executados

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
