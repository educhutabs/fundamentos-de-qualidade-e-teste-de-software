# Erro, Defeito e Falha em Software

Este documento apresenta a distinção entre erro, defeito e falha no contexto da engenharia de software e da gestão da qualidade. Embora esses termos sejam frequentemente usados como sinônimos em conversas informais, eles representam conceitos distintos e complementares, fundamentais para análise técnica, rastreabilidade e melhoria contínua.

---

## Visão geral

Em ambientes de desenvolvimento e operação, expressões como “o sistema deu erro”, “foi encontrado um bug” ou “a aplicação falhou” costumam aparecer como equivalentes. Apesar de comuns no uso cotidiano, essas formulações podem gerar ambiguidade quando utilizadas em análise de incidentes, triagem de defeitos, auditorias, investigações de causa raiz e documentação técnica.

Do ponto de vista da engenharia de qualidade, erro, defeito e falha fazem parte de uma cadeia causal. Em termos simples:

**Erro humano -> Defeito no artefato -> Falha no comportamento do sistema**

Essa diferenciação permite identificar com maior precisão:
- A origem do problema.
- O artefato impactado.
- A manifestação observável.
- As ações corretivas e preventivas mais adequadas.

---

## Erro

Erro é a ação humana que produz um resultado incorreto. Ele representa a origem da cadeia causal e está associado a uma decisão equivocada, interpretação inadequada, omissão, descuido ou aplicação incorreta de conhecimento durante alguma etapa do ciclo de desenvolvimento.

O erro não reside no software em si, mas na atividade humana que levou à introdução de um problema. Por isso, ele pode ocorrer antes mesmo de existir código implementado, por exemplo na especificação de requisitos, na modelagem de solução, na configuração de ambientes ou na elaboração de testes.

### Exemplos de ocorrência

- Interpretação incorreta de uma regra de negócio.
- Entendimento incompleto de um requisito funcional ou não funcional.
- Uso inadequado de linguagem, framework, biblioteca ou API.
- Falha de comunicação entre áreas de negócio, desenvolvimento e qualidade.
- Decisões apressadas sob pressão de prazo ou contexto operacional adverso.

---

## Defeito

Defeito é a materialização de um erro em algum artefato do ciclo de vida de software. Em outras palavras, trata-se da incorreção incorporada ao produto ou a seus artefatos associados, como código-fonte, documentação, scripts, configurações, dados estruturais ou até casos de teste.

O defeito existe independentemente de já ter sido executado ou percebido em produção. Ele pode permanecer latente por longos períodos, especialmente quando o trecho afetado não é exercitado, quando as condições de ativação ainda não ocorreram ou quando não há cobertura de revisão e teste suficiente para evidenciá-lo.

### Características do defeito

- Pode existir em múltiplos tipos de artefato, não apenas em código.
- Pode ser identificado por técnicas estáticas, sem execução do sistema.
- Nem todo defeito gera falha perceptível imediatamente.
- Um único erro pode originar um ou mais defeitos.

### Exemplos de defeito

- Regra de cálculo implementada com operador incorreto.
- Script de banco com condição errada de atualização.
- Configuração equivocada de timeout ou permissão.
- Critério de aceite documentado de forma ambígua.
- Caso de teste construído com premissa inválida.

---

## Falha

Falha é a manifestação observável de um comportamento incorreto do software durante sua execução. Ela ocorre quando um defeito é ativado em determinadas condições e faz com que o sistema produza um resultado diferente do esperado.

Em termos operacionais, a falha é aquilo que o usuário, o testador, o analista de suporte ou o sistema de monitoramento percebe. É o sintoma visível do problema em tempo de execução.

### Exemplos de falha

- A aplicação retorna valor incorreto em um cálculo.
- Um serviço encerra inesperadamente.
- Um campo obrigatório deixa de ser validado.
- A interface trava após determinada sequência de ações.
- O sistema não responde dentro do tempo esperado.

### Condições de ativação

Nem todo defeito se converte imediatamente em falha. Para que a falha aconteça, geralmente é necessário que determinadas condições estejam presentes, como:
- Entrada específica.
- Estado particular do sistema.
- Sequência exata de operações.
- Volume de dados incomum.
- Contexto técnico ou ambiente de execução específico.

Essa relação explica por que um sistema pode conter defeitos sem apresentar falhas visíveis por um longo período. Também explica por que certos problemas aparecem apenas em produção, com combinação real de dados, integrações e carga operacional.

---

## Relação entre os conceitos

A distinção entre erro, defeito e falha fica mais clara quando observada como uma sequência lógica de causa e efeito:

1. Uma pessoa interpreta ou executa algo de forma incorreta.
2. Essa ação introduz uma incorreção em um artefato.
3. Quando o artefato é executado sob certas condições, o comportamento incorreto se manifesta.

### Exemplo ilustrativo

Considere a implementação de um desconto comercial:
- O analista interpreta de forma equivocada a regra de negócio, entendendo que o desconto máximo é 20%, quando o correto seria 12%.
- Essa interpretação incorreta leva o desenvolvedor a implementar a validação com limite de 20%.
- Em produção, um pedido recebe desconto acima do permitido e o faturamento é processado com valor incorreto.

Nesse cenário:
- A interpretação incorreta é o **erro**.
- A validação implementada com limite indevido é o **defeito**.
- O cálculo aceito com valor incorreto em execução é a **falha**.

---

## Implicações para a qualidade

A clareza conceitual entre erro, defeito e falha melhora a capacidade do time de diagnosticar, corrigir e prevenir problemas. Essa precisão é especialmente importante em organizações que tratam qualidade como disciplina de engenharia e não apenas como etapa operacional de teste.

### Detecção antecipada

Quanto mais cedo a cadeia é interrompida, menor tende a ser o custo de correção e menor o risco de propagação do problema. Práticas como refinamento de requisitos, revisão por pares, análise estática, inspeção documental e validação antecipada ajudam a detectar erros e defeitos antes que eles se convertam em falhas observáveis.

### Análise de causa raiz

Quando uma falha é encontrada, o trabalho técnico não deve se encerrar na correção do sintoma. O caminho mais eficaz é investigar a cadeia inversa:
- Qual falha foi observada.
- Qual defeito a produziu.
- Qual erro humano, lacuna processual ou falha de comunicação permitiu sua introdução.

Essa abordagem fortalece práticas de Root Cause Analysis, aprendizado organizacional e prevenção sistêmica.

### Comunicação e rastreabilidade

Em registros de incidentes e defeitos, o uso preciso da terminologia melhora a comunicação entre QA, desenvolvimento, produto, suporte e gestão. Também aumenta a qualidade da rastreabilidade, porque separa claramente:
- O que foi percebido.
- Onde está o problema.
- Qual foi a causa provável.

---

## Registro adequado de ocorrências

Em ferramentas como Jira, Azure DevOps ou YouTrack, um registro de qualidade tende a ser mais útil quando descreve de maneira estruturada os elementos essenciais do problema. Um bom registro deve deixar explícito:

- A falha observada, ou seja, o que ocorreu em execução.
- O comportamento esperado, isto é, o resultado correto.
- As condições de reprodução, incluindo dados, contexto e passos executados.
- O artefato comprometido, quando identificado.
- Evidências técnicas que ajudem na análise e na priorização.

Essa disciplina reduz ambiguidades, acelera a triagem e favorece correções mais assertivas.

---

## Diretrizes conceituais

Para fins de padronização terminológica neste repositório, adotam-se as seguintes diretrizes:

- **Erro** deve ser tratado como ação humana incorreta.
- **Defeito** deve ser tratado como a incorreção presente em um artefato.
- **Falha** deve ser tratada como a manifestação observável em tempo de execução.
- O termo **bug** pode ser utilizado em contexto informal, mas em documentação formal recomenda-se preferir “defeito” ou “falha”, conforme o caso.
- Investigações de qualidade devem buscar a cadeia completa, e não apenas a correção do efeito observado.

---

## Encerramento

A distinção entre erro, defeito e falha não é apenas terminológica. Ela sustenta análises mais precisas, registros mais úteis, investigações mais maduras e ações preventivas mais eficazes dentro da engenharia de software.

Quando o time incorpora esses conceitos ao vocabulário e ao processo, a qualidade deixa de ser apenas reação a incidentes e passa a funcionar como mecanismo estruturado de aprendizado e redução de risco.

## Referências

- ASTQB. *ISTQB Foundation Level – Seven Testing Principles*. 
- ISTQB. *Certified Tester Foundation Level Syllabus v4.0.1*.
- ISTQB. *Certified Tester Foundation Level (CTFL) v4.0 Overview*. 
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Hoboken: Wiley, 2011.
- PRESSMAN, Roger S.; MAXIM, Bruce R. *Software Engineering: A Practitioner’s Approach*. 9. ed. New York: McGraw-Hill, 2019.
- KANER, Cem; BACH, James; PETTICHORD, Bret. *Lessons Learned in Software Testing*. New York: Wiley, 2001.
