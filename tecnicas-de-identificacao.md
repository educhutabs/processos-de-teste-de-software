# Técnicas de Identificação de Testes

Este documento detalha três técnicas fundamentais de projeto de casos de teste: partição de equivalência, análise de valor limite e matriz de decisão. Cada uma dessas técnicas oferece uma abordagem sistemática para selecionar entradas e condições de teste, reduzindo a subjetividade no processo de identificação e aumentando a efetividade da cobertura sem multiplicar desnecessariamente o número de casos de teste.

---

## Por que usar técnicas de projeto de testes

Sem uma técnica estruturada, a seleção de casos de teste tende a ser guiada pela intuição ou pela experiência individual do testador. Isso gera dois problemas recorrentes: cobertura concentrada nos fluxos mais óbvios e lacunas em condições de contorno e combinações de entradas menos evidentes — exatamente onde os defeitos mais críticos costumam estar.

As técnicas de projeto de testes oferecem critérios objetivos para decidir o que testar e com quais dados, tornando o processo reproduzível, rastreável e independente do perfil de quem o executa.

---

## Partição de equivalência

### O que é

A partição de equivalência é uma técnica que divide o domínio de entradas de um sistema em grupos — as partições — cujos elementos se comportam de maneira equivalente do ponto de vista do software. A premissa é que, se o sistema trata corretamente um valor de uma partição, ele deve tratar corretamente qualquer outro valor da mesma partição. Portanto, basta testar um representante de cada grupo.

Essa técnica reduz significativamente o número de casos de teste necessários sem comprometer a cobertura lógica, pois elimina a redundância de testar múltiplos valores que exercitam exatamente o mesmo caminho de código.

### Partições válidas e inválidas

Para cada campo ou condição de entrada, as partições são classificadas em:

**Partições válidas:** conjuntos de valores que o sistema deve aceitar e processar corretamente.

**Partições inválidas:** conjuntos de valores que o sistema deve rejeitar, tratando com mensagem de erro adequada.

Ambos os tipos precisam ser testados. Ignorar as partições inválidas é um erro comum que deixa descobertos os comportamentos de tratamento de erro do sistema.

### Quando aplicar

A partição de equivalência é especialmente útil em campos de formulário, parâmetros de API, filtros de busca e qualquer situação em que o domínio de entradas possa ser agrupado em categorias com comportamento homogêneo. É frequentemente combinada com a análise de valor limite para aumentar a efetividade da cobertura.

---

## Análise de valor limite

### O que é

A análise de valor limite é uma técnica complementar à partição de equivalência, focada nos extremos de cada partição. A premissa é empírica: defeitos tendem a se concentrar nas fronteiras entre partições, onde a lógica de comparação e validação é mais propensa a erros de implementação — como o uso de `>` em vez de `>=`, ou `<` em vez de `<=`.

Em vez de testar apenas um valor representativo do interior de cada partição, a análise de valor limite testa os valores exatamente na fronteira e imediatamente adjacentes a ela.

### Como identificar os valores limite

Para cada fronteira entre partições, são selecionados:

- O valor exatamente no limite

- O valor imediatamente abaixo do limite

- O valor imediatamente acima do limite

Em sistemas com domínios discretos (números inteiros, por exemplo), "imediatamente abaixo" e "imediatamente acima" significam o valor anterior e o valor seguinte. Em domínios contínuos, a granularidade depende do tipo de dado utilizado.

### Quando aplicar

A análise de valor limite é aplicável sempre que existirem intervalos numéricos, datas, tamanhos de campo, quantidades ou qualquer condição com fronteiras explícitas. É uma das técnicas com melhor custo-benefício em termos de defeitos encontrados por caso de teste executado.

---

## Matriz de decisão

### O que é

A matriz de decisão — também chamada de tabela de decisão — é uma técnica utilizada para testar sistemas cujo comportamento depende de combinações de condições. Enquanto a partição de equivalência e a análise de valor limite tratam cada entrada de forma independente, a matriz de decisão é indicada para situações em que o resultado do sistema depende do estado conjunto de múltiplas condições simultaneamente.

A técnica organiza todas as combinações possíveis de condições e seus respectivos resultados em uma tabela estruturada, garantindo que nenhuma combinação relevante seja esquecida.

### Estrutura da matriz

Uma matriz de decisão é composta por:

**Condições:** as entradas ou estados que influenciam o comportamento do sistema. Cada condição ocupa uma linha na parte superior da tabela.

**Regras:** cada coluna representa uma combinação específica de condições. O número máximo de regras para _n_ condições binárias é 2ⁿ.

**Ações:** os resultados ou comportamentos esperados para cada combinação de condições.

### Simplificação da matriz

Em sistemas com muitas condições, o número de combinações cresce exponencialmente. Nesses casos, é possível simplificar a matriz eliminando combinações impossíveis ou irrelevantes para o negócio, e agrupando regras que produzem o mesmo resultado e diferem em condições que não afetam esse resultado.

### Quando aplicar

A matriz de decisão é especialmente útil em regras de negócio complexas, fluxos de aprovação, cálculos com múltiplos critérios e qualquer situação em que o resultado do sistema dependa de mais de uma condição combinada. É uma das técnicas mais eficazes para revelar defeitos em lógica condicional, que tendem a se esconder em combinações de condições pouco exercitadas nos testes exploratórios.

---

## Referências

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.

- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.

- PRESSMAN, Roger S. *Engenharia de Software: Uma Abordagem Profissional*. 8. ed. McGraw-Hill, 2016.

- CRAIG, Rick D.; JASKIEL, Stefan P. *Systematic Software Testing*. Artech House, 2002.

- BEIZER, Boris. *Software Testing Techniques*. 2. ed. Van Nostrand Reinhold, 1990.
