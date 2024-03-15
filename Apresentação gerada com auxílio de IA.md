---
share: "true"
---

Esta apresentação é baseada nos guias de engenharia de prompt da Open AI e no artigo da Coursera. 

E recebeu um tratamento para abordar o tema dentro de um contexto específico.

----

## Introdução: O Poder do Prompt Engineering

- **Maximize a eficiência**: Aprenda a comunicar suas necessidades de forma eficaz ao modelo, economizando tempo e recursos.
- **Melhore a precisão das respostas**: Ajustando suas perguntas, você pode guiar o modelo para fornecer exatamente o que você precisa.
- **Inovação no trabalho**: Descubra como o prompt engineering pode ser um aliado poderoso para secretárias executivas, transformando a maneira como você organiza, planeja e comunica na Telefónica.

---
- **Exemplo**: Imagine solicitar um resumo de uma reunião complexa. Sem técnicas de prompt engineering, você pode receber um texto longo e genérico. Com prompt engineering, você especifica o formato, os pontos de foco, e o comprimento desejado, resultando em um resumo conciso e informativo, pronto para ser usado em comunicações internas.
---

## 1. Escreva Instruções Claras

- **Claridade é chave**: Seja específico para evitar ambiguidade.
- **Personalize a saída**: Peça respostas breves, escrita em nível de especialista, ou um formato específico.
- **Exemplo**:
  - Em vez disso: "Organize minha agenda."
  - Faça isso: "Organize minha agenda para a próxima semana focando em reuniões de projeto e deixando blocos de 2 horas livres para trabalho focado."

---

## 1.1 Detalhes Importam

- **Forneça contexto e detalhes** para respostas mais relevantes.
- **Comparação**: Exemplos de perguntas **pobres** vs **melhores** demonstram o impacto dos detalhes.
- **Exemplo**:
  - Em vez disso: "Como faço para agendar uma reunião?"
  - Faça isso: "Como faço para agendar uma reunião com participantes em diferentes fusos horários, garantindo que todos recebam um convite ajustado ao seu horário local?"

---

## 1.2 Adote uma Persona

- **Persona específica**: Instrua o modelo a adotar uma persona para respostas mais personalizadas.
- **Exemplo**:
  - Em vez disso: "Escreva um e-mail para um cliente."
  - Faça isso: "Escreva um e-mail para um cliente importante explicando um breve atraso na entrega do projeto, assegurando o compromisso com a qualidade."

---

## 1.3 Uso de Delimitadores

- **Clarifique a entrada**: Utilize delimitadores para separar claramente diferentes partes da entrada.
- **Exemplo**:
  - Em vez disso: "Resuma a reunião e escreva as ações."
  - Faça isso: "Use ### para separar o resumo da reunião dos itens de ação e *** para destacar os prazos."

---

## 1.4 Sequência de Passos

- **Instruções passo a passo**: Especifique uma sequência de ações para facilitar o entendimento do modelo.
- **Exemplo**:
  - Em vez disso: "Prepare a documentação do projeto."
  - Faça isso: "Passo 1: Resuma os objetivos do projeto. Passo 2: Liste as principais entregas. Passo 3: Anexe os perfis das partes interessadas."

---

## 1.5 Fornecendo Exemplos

- **"Few-shot" prompting**: Exemplos podem ser mais fáceis do que descrever todas as permutações de uma tarefa.
- **Exemplo**:
  - Em vez disso: "Como faço para melhorar minha escrita de e-mails?"
  - Faça isso: "Para escrever e-mails mais eficazes, inicie com um resumo claro do objetivo. Exemplo: 'O propósito deste e-mail é atualizar a equipe sobre o progresso do projeto X e discutir os próximos passos.'"

---

## 1.6 Comprimento da Saída

- **Especifique o comprimento alvo**: Peça por um número específico de palavras, parágrafos ou pontos de bala.
- **Exemplo**:
  - Em vez disso: "Faça um resumo."
  - Faça isso: "Faça um resumo da conferência de ontem em no máximo 100 palavras, destacando decisões principais."

---

## 2. Texto de Referência

- **Minimize fabricações**: Fornecer texto de referência pode levar a respostas mais precisas e menos inventadas.
- **Exemplo**:
  - Em vez disso: "Qual é a política de home office?"
  - Faça isso: Fornecer o documento da política de home office da Telefónica para responder a uma pergunta sobre os requisitos para trabalho remoto.

---

## 2.1 Responder com Texto de Referência

- **Use informações confiáveis**: Instrua o modelo a responder com base no texto de referência fornecido.
- **Exemplo**:
  - Em vez disso: "Como faço para solicitar férias?"
  - Faça isso: "Usando o manual do funcionário da Telefónica fornecido, explique o processo para solicitar férias."

---

## 2.2 Citar Texto de Referência
- **Adicione citações**: Solicite que o modelo inclua citações de textos fornecidos para verificar a precisão.
- **Exemplo**:
  - Em vez disso: "Informe sobre a política de viagens."
  - Faça isso: "Cite a seção do manual do funcionário sobre viagens de negócios para explicar os limites de despesas."

---

## 3. Dividindo Tarefas Complexas

- **Simplifique tarefas**: Divida tarefas complexas em sub-tarefas mais gerenciáveis.
- **Exemplo**:
  - Em vez disso: "Organize o evento corporativo."
  - Faça isso: Divida em "Determinar o orçamento", "Selecionar o local", "Enviar convites", "Organizar catering".

---

## 3.1 Classificação de Intenção

- **Identifique instruções relevantes**: Classifique consultas para determinar a melhor abordagem de resposta.
- **Exemplo**:
  - Em vez disso: "Estou tendo problemas para acessar o sistema."
  - Faça isso: Perguntas de suporte técnico classificadas em "problemas de acesso ao sistema", "falhas de software", "solicitações de atualização de hardware".

---

## 3.4 Resumindo Diálogos

- **Gerencie conversas longas**: Resuma ou filtre diálogos anteriores para manter a relevância.
- **Exemplo**:
  - Em vez disso: "Atualize a equipe sobre a reunião."
  - Faça isso: "Resuma os principais pontos discutidos na reunião de hoje em um e-mail, focando em decisões tomadas e tarefas atribuídas."

---

## 3.5 Resumindo Documentos Longos

- **Resumos recursivos**: Use uma abordagem passo a passo para resumir documentos extensos.
- **Exemplo**:
  - Em vez disso: "Leia este relatório."
  - Faça isso: "Resuma cada seção do relatório de análise de mercado e depois crie um resumo executivo destacando as principais descobertas."

---

## 4. Dê Tempo ao Modelo

- **Raciocínio aprofundado**: Permita que o modelo "pense" para chegar a conclusões mais precisas.
- **Exemplo**:
  - Em vez disso: "Responda rapidamente."
  - Faça isso: "Antes de responder ao e-mail do cliente, liste possíveis soluções para o problema apresentado, considerando as políticas da Telefónica."

---

## 4.1 Solução Própria Primeiro

- **Evite conclusões precipitadas**: Instrua o modelo a calcular sua própria solução antes de avaliar a do usuário.
- **Exemplo**:
  - Em vez disso: "Qual é a resposta para o cliente?"
  - Faça isso: "Considere as políticas de atendimento ao cliente da Telefónica e as informações do caso antes de redigir uma proposta de solução para o problema do cliente."

---

## 4.2 Monólogo Interno

- **Oculte o processo de raciocínio**: Use o monólogo interno para esconder a lógica do usuário final.
- **Exemplo**:
  - Em vez disso: "Diga ao cliente que estamos trabalhando nisso."
  - Faça isso: "Internamente, revise os passos necessários para resolver o problema do cliente e depois comunique de forma clara e concisa que estamos tomando medidas para uma solução."

---

## 4.3 Verificação Adicional

- **Busque por omissões**: Pergunte ao modelo se algo foi perdido em revisões anteriores.
- **Exemplo**:
  - Em vez disso: "Isso cobre tudo?"
  - Faça isso: "Revise a lista de verificação de organização do evento para garantir que todos os elementos foram considerados antes de finalizar o planejamento."

---
## Conclusão: Ampliando Seus Conhecimentos em Prompt Engineering

- **Prática constante**: A habilidade em prompt engineering melhora com a prática. Experimente diferentes abordagens e refine suas técnicas.
- **Recursos Recomendados**:
	- [Prompt engineering - OpenAI API](https://platform.openai.com/docs/guides/prompt-engineering/strategy-write-clear-instructions)
	- [Examples - OpenAI API](https://platform.openai.com/examples)
	- [Best practices for prompt engineering with the OpenAI API | OpenAI Help Center](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api)
- **Experimente e Aprenda**: Não há uma fórmula única; o que funciona para uma tarefa pode não ser ideal para outra. Esteja aberto a experimentar.

---

Com conhecimento em aprimorar pedidos ao ChatGPT, você pode aumentar sua produtividade e eficácia. Tornar-se mestre em prompt engineering exige prática e experimentação. Aprofunde seus conhecimentos usando recursos recomendados e conecte-se com profissionais na área. Continue aprendendo e inovando!

---

![](Prompt%20Engineering/estudando.png)