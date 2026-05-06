# Tech Challenge Fase 1 — Case NPS Preditivo

## 1. Visão Geral do Projeto

Este projeto foi desenvolvido para o **Tech Challenge — Fase 1**, com foco na análise da satisfação de clientes em um cenário de e-commerce.

A empresa analisada possui dados de pedidos, entregas, atendimento e recompra. A partir dessas informações, o objetivo foi entender quais fatores da jornada do cliente mais influenciam o **NPS — Net Promoter Score** e como esses dados podem apoiar decisões de negócio.

O foco principal do projeto é transformar dados operacionais em uma leitura clara para áreas como logística, atendimento, experiência do cliente e estratégia.

---

## 2. Link do Repositório

Repositório público do projeto:

```text
https://github.com/acorrea79/IASTTechChallenge
```

---

## 3. Problema de Negócio

O problema de negócio analisado é:

> Quais fatores da jornada de compra mais impactam a satisfação do cliente em um e-commerce?

Atualmente, o NPS é coletado após a conclusão da experiência de compra. Isso significa que, quando a empresa recebe a nota, o cliente já passou por toda a jornada: pedido, entrega, atendimento e possível resolução de problemas.

Com esta análise, buscamos identificar quais fatores estão mais associados à queda ou melhora do NPS, permitindo que a empresa atue de forma mais preventiva e estratégica.

---

## 4. Pergunta Orientadora

A principal pergunta que orienta este trabalho é:

> O que mais influencia a satisfação do cliente: preço, entrega, atendimento ou problemas na jornada?

A análise foi direcionada para entender se o NPS está mais relacionado a fatores financeiros, como preço, desconto e frete, ou a fatores operacionais, como atraso, reclamações e atendimento.

---

## 5. Por que o NPS é importante para um e-commerce?

O NPS é importante porque mede a tendência de o cliente recomendar a empresa para outras pessoas.

Em um e-commerce, essa métrica é estratégica porque pode impactar diretamente:

### Recompra

Clientes satisfeitos tendem a comprar novamente. Uma boa experiência aumenta a confiança na marca e favorece a fidelização.

### Boca a boca

Clientes promotores podem divulgar a empresa espontaneamente. Já clientes insatisfeitos podem gerar avaliações negativas e prejudicar a reputação da marca.

### Competitividade

Empresas com melhor experiência do cliente tendem a reter consumidores, atrair novos compradores e fortalecer sua posição no mercado.

---

## 6. Áreas que podem se beneficiar da análise

| Área | Como pode usar os insights |
|---|---|
| Logística | Reduzir atrasos, acompanhar falhas e melhorar prazos de entrega |
| Atendimento | Reduzir retrabalho, melhorar resolução no primeiro contato e diminuir reclamações |
| Experiência do Cliente | Identificar clientes em risco e priorizar ações preventivas |
| Pricing | Avaliar se preço, desconto e frete realmente influenciam a satisfação |
| Produto | Entender se problemas da jornada impactam a percepção do cliente |
| Estratégia | Apoiar decisões para melhorar NPS, recompra e retenção |

---

## 7. Base de Dados

A base utilizada contém dados históricos de pedidos, entregas, atendimento e indicadores de satisfação.

Principais grupos de informação:

### Dados do cliente

- `customer_id`: identificador do cliente;
- `customer_age`: idade do cliente;
- `customer_region`: região geográfica;
- `customer_tenure_months`: tempo de relacionamento com a empresa.

### Dados do pedido

- `order_id`: identificador do pedido;
- `order_value`: valor do pedido;
- `items_quantity`: quantidade de itens;
- `discount_value`: desconto aplicado;
- `payment_installments`: número de parcelas;
- `freight_value`: valor do frete.

### Dados logísticos

- `delivery_time_days`: tempo total de entrega;
- `delivery_delay_days`: dias de atraso;
- `delivery_attempts`: número de tentativas de entrega.

### Dados de atendimento

- `customer_service_contacts`: quantidade de contatos com atendimento;
- `resolution_time_days`: tempo de resolução;
- `complaints_count`: número de reclamações.

### Indicadores de satisfação e recompra

- `nps_score`: nota de NPS, de 0 a 10;
- `csat_internal_score`: score interno de satisfação;
- `repeat_purchase_30d`: indica se houve recompra em até 30 dias.

---

## 8. Definição da Target

A variável alvo escolhida para representar a satisfação do cliente foi:

```python
nps_score
```

Essa variável foi escolhida porque representa a nota de satisfação e recomendação do cliente após a experiência de compra.

Também foi criada uma classificação auxiliar chamada:

```python
nps_class
```

Com a seguinte regra:

| Faixa de nota | Classificação |
|---|---|
| 0 a 6 | Detrator |
| 7 a 8 | Neutro |
| 9 a 10 | Promotor |

### Por que essa variável foi escolhida?

Porque o NPS resume a percepção final do cliente sobre a jornada de compra. Ele ajuda a identificar clientes satisfeitos, neutros e insatisfeitos.

### Em que momento essa informação é coletada?

O NPS é coletado após a conclusão da jornada de compra, ou seja, depois que o cliente já passou pela experiência de pedido, entrega e atendimento, quando aplicável.

### Risco de uso inadequado da variável

Existe um ponto de atenção: o NPS é uma informação coletada após a experiência do cliente. Portanto, em um modelo preditivo futuro, é necessário garantir que as variáveis usadas estejam disponíveis antes da coleta do NPS.

Caso contrário, o modelo pode utilizar informações que só existem depois do problema ocorrido, gerando uma previsão artificial e pouco útil para ação preventiva.

---

## 9. Metodologia Utilizada

O projeto foi dividido em duas etapas principais:

### 9.1 Tratamento dos Dados

Notebook utilizado:

```text
notebooks/TratamentoDados.ipynb
```

Principais etapas realizadas:

- Carregamento da base original;
- Verificação da estrutura dos dados;
- Identificação de valores nulos;
- Tratamento de valores ausentes;
- Padronização de textos;
- Criação da classificação de NPS;
- Remoção de duplicidades;
- Geração da base tratada para análise.

Arquivo gerado:

```text
Data/dataset_tratado.csv
```

### 9.2 Análise Exploratória dos Dados — EDA

Notebook utilizado:

```text
notebooks/EDA.ipynb
```

Principais análises realizadas:

- Distribuição geral do NPS;
- Distribuição por classe de NPS;
- Matriz geral de relacionamento entre variáveis;
- Análise entre logística, problemas e NPS;
- Análise entre atendimento, resolução e satisfação;
- Análise entre logística e atendimento;
- Análise entre preço e experiência;
- Análise entre satisfação e recompra.

O foco da análise exploratória foi traduzir os dados em uma leitura de negócio, priorizando a compreensão dos fatores que impactam a experiência do cliente.

---

## 10. Estrutura do Projeto, Instalação e Execução

Esta seção consolida a estrutura do projeto com os passos necessários para executar a análise.

### 10.1 Estrutura atual do projeto

```text
IASTTechChallenge/
│
├── Data/
│   └── dataset_tratado.csv
│
├── notebooks/
│   ├── EDA.ipynb
│   └── TratamentoDados.ipynb
│
└── README.md
```

### 10.2 Tecnologias utilizadas

- Python;
- Pandas;
- NumPy;
- Matplotlib;
- Seaborn;
- Jupyter Notebook;
- Google Colab ou ambiente local com Jupyter.

### 10.3 Clonar o repositório

```bash
git clone https://github.com/acorrea79/IASTTechChallenge
```

### 10.4 Acessar a pasta do projeto

```bash
cd IASTTechChallenge
```

### 10.5 Instalar as dependências

Caso utilize ambiente local, instale as principais bibliotecas:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 10.6 Executar os notebooks

Execute os notebooks nesta ordem:

```text
1. notebooks/TratamentoDados.ipynb
2. notebooks/EDA.ipynb
```

O primeiro notebook realiza o tratamento da base e gera o arquivo tratado.

O segundo notebook realiza a análise exploratória e apresenta os principais gráficos e conclusões do projeto.

---

## 11. Apresentação Padronizada dos Resultados

Para facilitar a leitura do resultado, os achados foram organizados no padrão:

> **Dimensão analisada → Principal conclusão → Impacto para o negócio → Ação recomendada**

| Dimensão analisada | Principal conclusão | Impacto para o negócio | Ação recomendada |
|---|---|---|---|
| Logística, problemas e NPS | Atrasos na entrega estão ligados à queda do NPS | O cliente percebe quebra de promessa quando o pedido atrasa | Monitorar pedidos com risco de atraso e agir preventivamente |
| Atendimento, resolução e satisfação | Mais contatos com atendimento estão ligados a mais reclamações | O cliente precisa se esforçar mais para resolver problemas | Melhorar a resolução no primeiro contato |
| Logística e atendimento | Reclamações aumentam quando há falhas na jornada | Problemas operacionais sobrecarregam o suporte | Reduzir falhas de entrega e melhorar comunicação ativa |
| Preço e experiência | Valor do pedido, desconto e frete têm baixa influência direta no NPS | A satisfação depende mais da experiência do que do preço | Priorizar qualidade da jornada, não apenas promoções |
| Satisfação e recompra | Clientes mais satisfeitos tendem a comprar novamente | Melhor experiência aumenta fidelização e recorrência | Usar NPS como indicador estratégico de retenção |

---

## 12. Principais Insights da Análise

### 12.1 A satisfação está mais ligada à experiência do que ao preço

A análise mostra que fatores financeiros, como valor do pedido, desconto e frete, apresentaram baixa relação com o NPS.

Isso indica que a satisfação do cliente depende mais da qualidade da entrega, do atendimento e da resolução de problemas do que de promoções ou preços menores.

### 12.2 Atrasos na entrega reduzem a satisfação

O atraso na entrega foi um dos fatores mais relevantes na queda do NPS.

Clientes que enfrentam atraso tendem a avaliar pior a experiência, o que pode reduzir a chance de recomendação e recompra.

### 12.3 Reclamações são forte sinal de risco

O aumento de reclamações está diretamente ligado à pior percepção do cliente.

Clientes que registram mais reclamações tendem a ter menor NPS, menor satisfação e maior risco de não voltar a comprar.

### 12.4 Muitos contatos com atendimento indicam falha na jornada

A quantidade de contatos com o atendimento apresentou forte relação com o número de reclamações.

Isso sugere que, quando o cliente precisa procurar a empresa muitas vezes, a experiência se torna mais desgastante.

O ideal é reduzir a necessidade de múltiplos contatos e aumentar a resolução no primeiro atendimento.

### 12.5 Clientes satisfeitos tendem a comprar novamente

A análise mostrou relação positiva entre NPS, satisfação interna e recompra em até 30 dias.

Isso reforça que melhorar a experiência do cliente não é apenas uma ação de relacionamento, mas também uma estratégia comercial para aumentar retenção e recorrência.

---

## 13. Fatores que mais impactam a satisfação do cliente

Com base nas análises, os fatores mais críticos para a satisfação são:

| Fator | Impacto observado |
|---|---|
| Atraso na entrega | Reduz o NPS e prejudica a experiência |
| Reclamações | Forte sinal de insatisfação |
| Contatos com atendimento | Indicam esforço do cliente para resolver problemas |
| Tempo de resolução | Pode piorar a percepção quando a solução demora |
| Recompra | Aumenta entre clientes mais satisfeitos |

---

## 14. O que mais gera clientes detratores?

Os clientes detratores estão mais associados a experiências com falhas na jornada.

Os principais sinais de risco são:

- Pedido entregue com atraso;
- Cliente com reclamação registrada;
- Cliente que precisou entrar em contato várias vezes;
- Problema com resolução demorada;
- Experiência com alto esforço para o consumidor.

Em resumo, o detrator parece surgir menos por causa de preço e mais por causa de problemas operacionais e atendimento ineficiente.

---

## 15. Ponto de Ruptura da Experiência

Nesta análise, o ponto de ruptura não foi tratado como um único número exato, mas como um conjunto de sinais que indicam piora clara na experiência do cliente.

| Sinal | Interpretação de negócio |
|---|---|
| Presença de atraso na entrega | O cliente começa a perceber quebra de promessa |
| Registro de reclamação | A experiência já gerou insatisfação formal |
| Múltiplos contatos com atendimento | O cliente precisou se esforçar para resolver o problema |
| Demora na resolução | O problema permaneceu por mais tempo do que o aceitável |
| Queda do NPS | A percepção final da jornada foi prejudicada |

Do ponto de vista comercial, a ruptura acontece quando o cliente deixa de ter uma jornada simples e passa a precisar cobrar, reclamar ou insistir para resolver um problema.

---

## 16. Perfil de cliente com NPS mais alto ou mais baixo

A análise não indicou forte influência de características como idade, valor do pedido ou desconto sobre o NPS.

O perfil de cliente com maior tendência de NPS alto está mais ligado a uma boa experiência operacional:

- Entrega sem atraso;
- Pouca ou nenhuma reclamação;
- Baixa necessidade de contato com atendimento;
- Resolução rápida quando há problema;
- Maior chance de recompra.

Já o perfil de cliente com maior tendência de NPS baixo apresenta sinais como:

- Atraso na entrega;
- Reclamações registradas;
- Muitos contatos com atendimento;
- Experiência com esforço elevado;
- Menor chance de recompra.

---

## 17. Conclusão Executiva da Análise

A análise consolidada demonstra que a experiência do cliente está muito mais ligada à qualidade operacional e ao atendimento do que a fatores financeiros, como preço, desconto ou valor da compra.

Os resultados mostram que os maiores impactos negativos na satisfação acontecem quando há atrasos na entrega, aumento de reclamações e necessidade frequente de contato com o atendimento.

Esses fatores reduzem a percepção positiva do cliente, diminuem a chance de recomendação e podem comprometer a recompra.

Por outro lado, clientes mais satisfeitos apresentam maior tendência de comprar novamente em até 30 dias, reforçando que a melhoria da experiência tem impacto direto na fidelização e no resultado comercial.

A principal recomendação é que a empresa priorize ações de melhoria em logística e atendimento, com foco em reduzir atrasos, diminuir reclamações, evitar múltiplos contatos e resolver problemas com mais rapidez.

---

## 18. Recomendações para o Negócio

### 18.1 Reduzir atrasos na entrega

- Monitorar pedidos com risco de atraso;
- Criar alertas preventivos para a operação logística;
- Melhorar a comunicação com o cliente antes do prazo ser descumprido.

### 18.2 Diminuir reclamações

- Identificar os principais motivos de reclamação;
- Criar planos de ação para os problemas mais recorrentes;
- Acompanhar clientes com histórico de insatisfação.

### 18.3 Melhorar o atendimento

- Reduzir o número de contatos necessários para resolver um problema;
- Priorizar resolução no primeiro atendimento;
- Criar indicadores de acompanhamento por tipo de problema.

### 18.4 Acelerar a resolução de problemas

- Definir prazos internos de resposta;
- Acompanhar chamados críticos;
- Dar prioridade a clientes com maior risco de baixa satisfação.

### 18.5 Usar o NPS como indicador estratégico

- Acompanhar NPS por tipo de problema;
- Cruzar NPS com recompra;
- Monitorar evolução do NPS após ações corretivas.

---

## 19. Indicadores de mercado que poderiam complementar a análise

| Indicador | Utilidade |
|---|---|
| Benchmark de NPS do setor | Comparar a empresa com concorrentes |
| SLA logístico | Avaliar cumprimento de prazos de entrega |
| Taxa de reclamação por pedido | Medir eficiência da jornada |
| Tempo médio de atendimento | Avaliar desempenho do suporte |
| Taxa de recompra | Medir fidelização |
| Avaliações públicas | Comparar percepção interna e externa da marca |
| Reclamações em canais externos | Medir reputação fora da base interna |

---

## 20. Limitações e Riscos da Análise

### 20.1 Relação não significa causa direta

A análise mostra relações entre variáveis, mas não prova causalidade absoluta.

Por exemplo, atrasos estão associados à queda no NPS, mas outros fatores também podem influenciar a nota do cliente.

### 20.2 Algumas variáveis podem ocorrer após o problema

Variáveis como reclamações, tempo de resolução e contatos com atendimento podem surgir depois que o cliente já teve uma experiência ruim.

Por isso, em um modelo preditivo futuro, será necessário avaliar quais dados estão disponíveis antes da coleta do NPS.

### 20.3 O perfil do cliente apresentou pouca influência

Idade, tempo de relacionamento e valor do pedido não mostraram impacto forte na satisfação. Isso não significa que sejam irrelevantes, mas sim que, nesta base, os fatores operacionais foram mais explicativos.

### 20.4 A análise depende da qualidade da base

Resultados podem ser afetados por dados ausentes, registros incorretos, baixa granularidade ou ausência de variáveis importantes, como motivo da reclamação, transportadora, categoria do produto ou canal de atendimento.

---

## 21. Proposta de Evolução com Inteligência Artificial

Como evolução futura, a empresa poderia construir um modelo preditivo para estimar o risco de baixa satisfação antes da aplicação da pesquisa de NPS.

### Estratégia recomendada

A estratégia mais adequada seria iniciar com um modelo de classificação, separando clientes em grupos como:

- Cliente com risco de baixa satisfação;
- Cliente neutro;
- Cliente com alta chance de satisfação.

### Possível variável alvo

A variável `nps_class` poderia ser usada como alvo, classificando os clientes em:

- Detrator;
- Neutro;
- Promotor.

Outra opção seria transformar o problema em classificação binária:

- Satisfeito;
- Insatisfeito.

### Variáveis de entrada possíveis

- Atraso na entrega;
- Tempo total de entrega;
- Número de tentativas de entrega;
- Contatos com atendimento;
- Reclamações;
- Tempo de resolução;
- Valor do pedido;
- Valor do frete;
- Desconto;
- Tempo de relacionamento do cliente.

### Uso prático do modelo

O modelo poderia apoiar a empresa a:

- Identificar clientes em risco antes da nota final de NPS;
- Priorizar atendimento preventivo;
- Acionar logística em pedidos críticos;
- Reduzir reclamações;
- Melhorar recompra;
- Direcionar ações de retenção.

---

## 22. Entregáveis do Projeto

Este repositório contém:

- Tratamento e preparação da base de dados;
- Base tratada em formato CSV;
- Análise exploratória dos dados;
- Interpretação dos resultados com foco em negócio;
- Conclusões executivas;
- Recomendações práticas;
- Proposta conceitual de evolução com modelo preditivo.

---

## 23. Resumo Final

A análise mostrou que a satisfação do cliente no e-commerce é mais impactada pela experiência operacional do que por preço ou desconto.

Os principais fatores associados à queda do NPS são:

- Atrasos na entrega;
- Reclamações;
- Múltiplos contatos com atendimento;
- Demora na resolução de problemas.

Já clientes com melhor experiência apresentam maior tendência de recompra, reforçando que investir em logística, atendimento e resolução rápida pode gerar impacto direto na fidelização.

A principal conclusão é que a empresa deve priorizar uma jornada simples, confiável e com menos atrito para o cliente.

Mais do que oferecer descontos, o diferencial competitivo está em cumprir prazos, resolver problemas rapidamente e reduzir a necessidade de esforço por parte do consumidor.
