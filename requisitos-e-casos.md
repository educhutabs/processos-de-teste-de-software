# Requisitos e Casos de Teste

Este documento aborda as etapas de análise e modelagem de testes, seguidas da implementação, execução e conclusão do ciclo de testes. São as atividades que transformam o planejamento em prática: é aqui que os requisitos se tornam casos de teste, e os casos de teste se tornam evidências de qualidade.

---

## Análise e Modelagem de Testes

### O que é a análise de testes

A análise de testes é a atividade de examinar a base de testes — requisitos, histórias de usuário, casos de uso, regras de negócio, documentação técnica — para identificar o que deve ser testado. O resultado da análise é um conjunto de **condições de teste**: situações ou características do sistema que precisam ser verificadas.

A qualidade da análise determina diretamente a cobertura dos testes. Uma análise superficial produz casos de teste que cobrem apenas os fluxos óbvios, deixando lacunas em fluxos alternativos, condições de contorno e cenários de erro — exatamente onde os bugs mais críticos costumam se esconder.

### Fontes de análise

A análise pode ser conduzida a partir de diferentes artefatos, dependendo da metodologia e da maturidade do projeto:

**Especificação de requisitos:** Documento formal com requisitos funcionais e não funcionais
**Histórias de usuário:** Descrições curtas de funcionalidades na perspectiva do usuário, comuns em projetos ágeis
**Critérios de aceite:** Condições que definem quando uma história ou requisito está concluído
**Casos de uso:** Descrições de interações entre o usuário e o sistema para atingir um objetivo
**Regras de negócio:** Restrições e políticas que o sistema deve respeitar
**Documentação técnica:** Especificações de APIs, modelos de dados e arquitetura

### O que é a modelagem de testes

A modelagem é a atividade de projetar os casos de teste a partir das condições identificadas na análise. É nessa etapa que se decide **como** testar cada condição: quais entradas usar, qual sequência de ações executar e qual resultado verificar.

A modelagem utiliza **técnicas de projeto de casos de teste** para garantir que o esforço de teste seja eficiente e sistemático, cobrindo as situações mais relevantes sem desperdiçar recursos em redundâncias. As técnicas mais utilizadas — partição de equivalência, análise de valor limite e matriz de decisão — são detalhadas no documento `tecnicas-e-identificacao.md`.

### Estrutura de um caso de teste

Um caso de teste bem estruturado deve conter, no mínimo:

```
ID              : Identificador único
Título          : Descrição objetiva do que está sendo testado
Pré-condição    : Estado do sistema antes da execução
Passos          : Sequência de ações a executar
Dados de entrada: Valores específicos utilizados na execução
Resultado esperado: Comportamento esperado do sistema após os passos
Pós-condição    : Estado do sistema após a execução (quando relevante)
```

A clareza dos passos e a objetividade do resultado esperado são os critérios mais importantes para um caso de teste de qualidade. Um caso de teste ambíguo gera resultados inconsistentes: dois executores diferentes podem chegar a conclusões opostas sobre o mesmo comportamento do sistema.

### Rastreabilidade

A rastreabilidade é a capacidade de vincular cada caso de teste ao requisito ou condição de teste que o originou. Ela garante que nenhum requisito fique sem cobertura e permite avaliar o impacto de mudanças de escopo sobre a suíte de testes.

Em ferramentas de gestão de testes (como Jira, TestRail ou Azure DevOps), a rastreabilidade é implementada por meio de vínculos entre itens de backlog ou requisitos e os casos de teste correspondentes.

---

## Implementação de Testes

### O que é

A implementação é a atividade de preparar tudo que é necessário para a execução dos testes: organizar e priorizar os casos de teste, preparar os dados de teste, configurar os ambientes e, quando aplicável, desenvolver os scripts de automação.

### Organização dos casos de teste

Os casos de teste são agrupados em **suítes de teste**, que organizam a execução por funcionalidade, nível de teste, prioridade ou ciclo de entrega. A organização em suítes facilita a gestão da execução e permite reutilizar conjuntos de testes em diferentes ciclos.

### Dados de teste

Os dados de teste são um dos aspectos mais frequentemente negligenciados da implementação. Dados inadequados ou insuficientes invalidam a execução: um caso de teste correto com dados errados não gera evidência confiável.

Boas práticas para dados de teste:

- Criar dados independentes por caso de teste, evitando dependências que causem falhas em cascata
- Utilizar dados representativos das condições reais de uso do sistema
- Garantir que dados sensíveis (CPF, cartão de crédito, e-mail) sejam anonimizados em ambientes de teste
- Documentar o estado esperado do ambiente antes e após cada execução

### Ambiente de teste

O ambiente de teste deve ser isolado do ambiente de produção e configurado de forma controlada. Diferenças entre o ambiente de teste e o de produção são uma fonte recorrente de bugs que só se manifestam após o deploy — o que torna o controle do ambiente parte essencial da implementação.

---

## Execução de Testes

### O que é

A execução é a atividade de rodar os casos de teste, registrar os resultados e reportar os bugs encontrados. É a etapa mais visível do processo, mas seu sucesso depende inteiramente da qualidade das etapas anteriores.

### Registro de resultados

Cada caso de teste executado deve ter seu resultado registrado de forma objetiva. Os status mais comuns são:

**Passou:** O comportamento observado corresponde ao resultado esperado
**Falhou:** O comportamento observado diverge do resultado esperado
**Bloqueado:** A execução não pôde ser concluída por impedimento externo
**Não executado:** O caso de teste ainda não foi executado no ciclo atual

### Reporte de bugs

Quando um caso de teste falha, um bug deve ser registrado na ferramenta de gestão. Um bom reporte de bug deve conter:

- **Título objetivo:** o que falhou, em que contexto
- **Passos para reprodução:** sequência exata que leva à falha
- **Resultado obtido:** o que o sistema fez
- **Resultado esperado:** o que o sistema deveria ter feito
- **Severidade:** impacto do bug no funcionamento do sistema (crítico, alto, médio, baixo)
- **Prioridade:** urgência de correção em relação ao contexto do projeto
- **Evidências:** capturas de tela, logs, vídeos — qualquer artefato que facilite a reprodução e a correção

A distinção entre severidade e prioridade é importante e frequentemente confundida. Um bug pode ter alta severidade técnica (como uma falha de segurança em funcionalidade pouco usada) e prioridade de correção mais baixa do que um bug de severidade média em um fluxo crítico de negócio.

---

## Conclusão de Testes

### O que é

A conclusão do ciclo de testes é a atividade de verificar se os critérios de saída foram atingidos, consolidar as lições aprendidas e produzir o relatório final de testes.

### Critérios de saída

Os critérios de saída, definidos durante o planejamento, determinam quando o ciclo de testes pode ser encerrado. Exemplos:

- Percentual mínimo de casos de teste executados (ex.: 100% dos críticos e 90% dos demais)
- Zero bugs abertos com severidade crítica
- Todos os bugs de alta severidade corrigidos e retestados com sucesso
- Cobertura mínima de requisitos atingida

### Relatório final de testes

O relatório final consolida os resultados do ciclo e serve como evidência formal da qualidade do sistema entregue. Deve conter, no mínimo:

- Resumo executivo do ciclo de testes
- Métricas de execução (casos planejados, executados, aprovados, falhos, bloqueados)
- Resumo dos bugs por severidade e status
- Avaliação de riscos residuais
- Recomendação de liberação ou retenção da entrega

### Lições aprendidas

Ao final de cada ciclo, o time deve registrar as lições aprendidas: o que funcionou bem no processo, o que pode ser melhorado e quais ajustes devem ser feitos no planejamento do próximo ciclo. Essa prática é o que transforma execução em aprendizado organizacional.

---

## Referências

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- IEEE Std 829. *Standard for Software and System Test Documentation*. IEEE, 2008.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- CRISPIN, Lisa; GREGORY, Janet. *Agile Testing: A Practical Guide for Testers and Agile Teams*. Addison-Wesley, 2009.
- WHITTAKER, James A. *How to Break Software*. Addison-Wesley, 2002.
