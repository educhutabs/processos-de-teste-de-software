# Processos de Teste de Software

Este documento aborda as cinco atividades centrais que estruturam o processo de teste: planejamento, monitoramento, análise, modelagem e execução. Compreender essas atividades é fundamental para conduzir o esforço de qualidade de forma organizada, previsível e orientada a resultados — e não apenas como uma sequência de execuções pontuais.

---

## O Processo de Teste como Disciplina

O teste de software não se resume à execução de casos de teste. É um processo contínuo que permeia todo o ciclo de vida do desenvolvimento, desde a análise de requisitos até a entrega em produção. Para que esse processo seja eficaz, ele precisa ser planejado, acompanhado e ajustado sistematicamente.

O ISTQB organiza o processo de teste em cinco atividades principais: planejamento, monitoramento e controle, análise, modelagem e execução. Este documento foca nas duas primeiras — planejamento e monitoramento e controle —, que constituem a camada gerencial do processo e determinam a qualidade de tudo que vem depois.

---

## Planejamento de Testes

### O que é

O planejamento de testes é a atividade responsável por definir o escopo, a abordagem, os recursos e o cronograma das atividades de teste. Seu principal artefato é o **Plano de Testes**, um documento que orienta toda a execução e serve como referência para decisões ao longo do projeto.

O planejamento não é uma atividade única realizada no início do projeto. Em metodologias ágeis, ele ocorre de forma iterativa, sendo revisado e refinado a cada ciclo de entrega.

### O que o planejamento define

**Escopo:** quais funcionalidades, módulos e requisitos serão cobertos pelos testes e quais estão explicitamente fora do escopo. A definição de exclusões é tão importante quanto a de inclusões — ela evita expectativas desalinhadas entre o time de QA e os stakeholders.

**Abordagem e estratégia:** quais tipos e níveis de teste serão utilizados, quais técnicas de projeto de casos de teste serão aplicadas e qual será o critério de priorização do esforço (baseado em risco, em criticidade de negócio, em histórico de defeitos, etc.).

**Critérios de entrada e saída:** condições que precisam ser satisfeitas para que o ciclo de testes seja iniciado (critérios de entrada) e condições que indicam que o ciclo foi concluído de forma satisfatória (critérios de saída). Exemplos comuns:

**Critério de entrada:** Build disponível, ambiente configurado, casos de teste revisados
**Critério de saída:** 95% dos casos de teste executados, zero defeitos críticos em aberto

**Recursos:** pessoas, ambientes, ferramentas e dados de teste necessários para a execução. A ausência de planejamento de recursos é uma das causas mais comuns de atrasos em fases de teste.

**Cronograma:** estimativas de esforço e distribuição das atividades de teste ao longo do projeto, alinhadas com as fases de desenvolvimento.

**Riscos:** identificação antecipada de riscos que podem impactar o processo de teste — como dependências externas, ambientes instáveis ou mudanças de escopo frequentes — e definição de estratégias de mitigação.

### Plano de testes

O Plano de Testes é o documento que consolida todas as decisões do planejamento. Ele não precisa ser extenso para ser eficaz, mas precisa ser claro, acordado com os stakeholders e mantido atualizado ao longo do projeto.

Estrutura básica de um Plano de Testes:

1. Objetivo e escopo
2. Itens a serem testados
3. Itens fora do escopo
4. Abordagem e estratégia
5. Critérios de entrada e saída
6. Recursos necessários
7. Cronograma
8. Riscos e mitigações
9. Responsabilidades

---

## Monitoramento e Controle de Testes

### O que é

Monitoramento é a atividade contínua de coleta e análise de informações sobre o andamento do processo de teste. Controle é a tomada de decisão e a execução de ações corretivas com base nessas informações.

As duas atividades são inseparáveis: monitorar sem controlar gera apenas relatórios. Controlar sem monitorar gera decisões baseadas em suposições. Juntas, elas garantem que o processo de teste permaneça alinhado ao plano e que desvios sejam identificados e corrigidos antes de se tornarem problemas maiores.

### Métricas de teste

As métricas são o principal instrumento do monitoramento. Elas transformam o progresso do teste em informação objetiva, permitindo comparar o estado atual com o planejado e comunicar o andamento para stakeholders de forma clara.

Métricas comumente utilizadas:

**Casos de teste planejados vs. executados:** Percentual do ciclo de testes concluído
**Taxa de aprovação:** Percentual de casos de teste que passaram
**Densidade de defeitos:** Número de defeitos por funcionalidade ou módulo
**Defeitos por severidade:** Distribuição de defeitos entre crítico, alto, médio e baixo
**Tempo médio de resolução de defeitos:** Eficiência do processo de correção
**Cobertura de requisitos:** Percentual de requisitos cobertos por pelo menos um caso de teste

### Relatório de progresso

O relatório de progresso é o artefato de comunicação do monitoramento. Deve ser produzido com regularidade — diária ou semanalmente, dependendo do projeto — e apresentar de forma objetiva o estado atual dos testes, os desvios em relação ao plano e os riscos identificados.

Um bom relatório de progresso responde a três perguntas:

1. **Onde estamos?** — percentual de execução, taxa de aprovação, número de defeitos abertos.
2. **Estamos dentro do plano?** — comparação entre o progresso real e o previsto.
3. **O que pode impactar a entrega?** — riscos ativos, bloqueadores e dependências pendentes.

### Controle: quando e como agir

Quando o monitoramento identifica desvios significativos, o controle entra em ação. As decisões mais comuns em situações de desvio incluem:

- Realocar recursos para áreas com maior densidade de defeitos
- Revisar a priorização dos casos de teste restantes com base no risco
- Renegociar escopo ou prazo com os stakeholders quando o desvio é irrecuperável
- Bloquear o avanço para produção quando os critérios de saída não foram atingidos

A decisão de bloquear ou liberar uma entrega com base nos resultados dos testes é uma das responsabilidades mais relevantes do processo de controle. Ela exige critérios claros, definidos durante o planejamento, e comunicação transparente com todas as partes envolvidas.

---

## Análise de Testes

### O que é

A análise de testes é a atividade de examinar a base de testes — requisitos, histórias de usuário, casos de uso, regras de negócio e documentação técnica — para identificar o que deve ser testado. O resultado da análise é um conjunto de **condições de teste**: situações ou características do sistema que precisam ser verificadas.

A qualidade da análise determina diretamente a cobertura dos testes. Uma análise superficial produz casos de teste concentrados nos fluxos mais evidentes, deixando lacunas em fluxos alternativos, condições de contorno e cenários de erro — exatamente onde os defeitos mais críticos costumam se esconder.

### Fontes de análise

A análise pode ser conduzida a partir de diferentes artefatos, dependendo da metodologia e da maturidade do projeto:

**Especificação de requisitos:** Documento formal com requisitos funcionais e não funcionais
**Histórias de usuário:** Descrições curtas de funcionalidades na perspectiva do usuário, comuns em projetos ágeis
**Critérios de aceite:** Condições que definem quando uma história ou requisito está concluído
**Casos de uso:** Descrições de interações entre o usuário e o sistema para atingir um objetivo
**Regras de negócio:** Restrições e políticas que o sistema deve respeitar
**Documentação técnica:** Especificações de APIs, modelos de dados e arquitetura

### Condições de teste

Cada condição de teste identificada na análise representa um aspecto do sistema que precisa ser verificado. Uma condição bem definida é específica o suficiente para orientar a criação de casos de teste, mas abstrata o suficiente para não prescrever a forma exata de testá-la.

Exemplo: para a regra de negócio "o sistema deve rejeitar cartões de crédito expirados", as condições de teste derivadas poderiam ser: cartão com data de validade anterior à data atual, cartão com data de validade igual à data atual e cartão com data de validade futura. Cada condição originará ao menos um caso de teste na etapa de modelagem.

### Análise e qualidade dos requisitos

A análise de testes frequentemente expõe problemas nos próprios requisitos: ambiguidades, contradições, lacunas e condições não especificadas. Identificar esses problemas durante a análise — antes da implementação — é uma das formas mais valiosas de contribuição do time de QA para a qualidade do produto. Quanto mais cedo um requisito incompleto é questionado, menor o custo de correção.

---

## Modelagem de Testes

### O que é

A modelagem é a atividade de projetar os casos de teste a partir das condições identificadas na análise. É nessa etapa que se decide **como** testar cada condição: quais entradas utilizar, qual sequência de ações executar e qual resultado verificar.

A modelagem utiliza **técnicas de projeto de casos de teste** para garantir que o esforço seja eficiente e sistemático, cobrindo as situações mais relevantes sem desperdiçar recursos em redundâncias. As três técnicas mais utilizadas são a partição de equivalência, a análise de valor limite e a matriz de decisão.

### Estrutura de um caso de teste

Um caso de teste bem estruturado deve conter, no mínimo:


ID: Identificador único

Título: Descrição objetiva do que está sendo testado

Pré-condição: Estado do sistema antes da execução

Passos: Sequência de ações a executar

Dados de entrada: Valores específicos utilizados na execução

Resultado esperado: Comportamento esperado do sistema após os passos

Pós-condição: Estado do sistema após a execução (quando relevante)

A clareza dos passos e a objetividade do resultado esperado são os critérios mais importantes para um caso de teste de qualidade. Um caso ambíguo gera resultados inconsistentes: dois executores diferentes podem chegar a conclusões opostas sobre o mesmo comportamento do sistema.

### Rastreabilidade

A rastreabilidade é a capacidade de vincular cada caso de teste ao requisito ou condição de teste que o originou. Ela garante que nenhum requisito fique sem cobertura e permite avaliar o impacto de mudanças de escopo sobre a suíte de testes. Em ferramentas de gestão como Jira, TestRail e Azure DevOps, a rastreabilidade é implementada por meio de vínculos entre requisitos e os casos de teste correspondentes.

### Organização em suítes de teste

Os casos de teste produzidos na modelagem são agrupados em **suítes de teste**, organizadas por funcionalidade, nível de teste, prioridade ou ciclo de entrega. Essa organização facilita a gestão da execução e permite reutilizar conjuntos de testes em diferentes ciclos sem retrabalho.

---

## Execução de Testes

### O que é

A execução é a atividade de rodar os casos de teste, registrar os resultados e reportar os defeitos encontrados. É a etapa mais visível do processo, mas seu sucesso depende inteiramente da qualidade das atividades anteriores: um ciclo de execução bem-sucedido começa muito antes do primeiro caso de teste ser rodado.

### Registro de resultados

Cada caso de teste executado deve ter seu resultado registrado de forma objetiva. Os status mais comuns são:

**Passou:** O comportamento observado corresponde ao resultado esperado
**Falhou:** O comportamento observado diverge do resultado esperado
**Bloqueado:** A execução não pôde ser concluída por impedimento externo
**Não executado:** O caso de teste ainda não foi executado no ciclo atual

### Reporte de defeitos

Quando um caso de teste falha, um defeito deve ser registrado na ferramenta de gestão. Um bom reporte de defeito deve conter:

- **Título objetivo:** o que falhou e em que contexto
- **Passos para reprodução:** sequência exata que leva à falha
- **Resultado obtido:** o que o sistema fez
- **Resultado esperado:** o que o sistema deveria ter feito
- **Severidade:** impacto do defeito no funcionamento do sistema (crítico, alto, médio, baixo)
- **Prioridade:** urgência de correção em relação ao contexto do projeto
- **Evidências:** capturas de tela, logs e vídeos que facilitem a reprodução e a correção

A distinção entre severidade e prioridade é frequentemente confundida. Um defeito pode ter alta severidade técnica e prioridade de correção mais baixa do que um defeito de severidade média em um fluxo crítico de negócio. As duas dimensões precisam ser avaliadas de forma independente.

### Conclusão do ciclo de execução

O ciclo de execução é encerrado quando os critérios de saída definidos no planejamento são atingidos. Ao final, um relatório de testes consolida os resultados, documenta os defeitos em aberto, registra as lições aprendidas e emite uma recomendação formal de liberação ou retenção da entrega.

## Referências

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- IEEE Std 829. *Standard for Software and System Test Documentation*. IEEE, 2008.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- PRESSMAN, Roger S. *Engenharia de Software: Uma Abordagem Profissional*. 8. ed. McGraw-Hill, 2016.
- CRAIG, Rick D.; JASKIEL, Stefan P. *Systematic Software Testing*. Artech House, 2002.
- CRISPIN, Lisa; GREGORY, Janet. *Agile Testing: A Practical Guide for Testers and Agile Teams*. Addison-Wesley, 2009.
