---
share: "true"
---
---
# Seis estratégias para obter melhores resultados

Este texto foi traduzido e adaptado da seguinte fonte original:
[Prompt engineering - OpenAI API](https://platform.openai.com/docs/guides/prompt-engineering/prompt-engineering)

---
## 1. Escreva instruções claras

Estes modelos não podem ler sua mente. Se as saídas forem longas demais, peça respostas breves. Se as saídas forem simples demais, peça escrita em nível de especialista. Se você não gostar do formato, demonstre o formato que gostaria de ver. Quanto menos o modelo tiver que adivinhar o que você quer, mais provável você obterá.

### 1.1 - Tática: Incluir detalhes na sua consulta para obter respostas mais relevantes

Para obter uma resposta altamente relevante, certifique-se de que as solicitações forneçam detalhes ou contexto importantes. Caso contrário, você está deixando ao modelo a tarefa de adivinhar o que você quer.


| **Pior**                                                  | **Melhor**                                                                                                                                                                                                                       |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Como eu adiciono números no Excel?                        | Como eu somo uma linha de valores em dólares no Excel? Quero fazer isso automaticamente para uma folha inteira de linhas, com todos os totais aparecendo à direita em uma coluna chamada "Total".                                |
| Quem é o presidente?                                      | Quem era o presidente do México em 2021, e com que frequência as eleições são realizadas?                                                                                                                                        |
| Escreva um código para calcular a sequência de Fibonacci. | Escreva uma função em TypeScript para calcular a sequência de Fibonacci de forma eficiente. Comente o código liberalmente para explicar o que cada parte faz e por que está escrita dessa maneira.                               |
| Resuma as notas da reunião.                               | Resuma as notas da reunião em um único parágrafo. Em seguida, escreva uma lista em markdown dos oradores e cada um de seus pontos-chave. Por fim, liste os próximos passos ou itens de ação sugeridos pelos oradores, se houver. |


### 1.2 - Tática: Peça ao modelo para adotar uma persona

A mensagem do sistema pode ser usada para especificar a persona usada pelo modelo em suas respostas.

SISTEMA

Quando eu pedir ajuda para escrever algo, você responderá com um documento que contém pelo menos uma piada ou comentário divertido em cada parágrafo.

USUÁRIO

Escreva uma nota de agradecimento ao meu fornecedor de parafusos de aço por conseguir a entrega a tempo e em curto prazo. Isso nos permitiu entregar um pedido importante.


### 1.3 - Tática: Use delimitadores para indicar claramente partes distintas da entrada

Delimitadores como aspas triplas, tags XML, títulos de seções, etc., podem ajudar a demarcar seções de texto a serem tratadas de forma diferente.


USUÁRIO

Resuma o texto delimitado por aspas triplas em um haiku. """inserir texto aqui"""


SISTEMA

Você receberá um par de artigos (delimitados com tags XML) sobre o mesmo tópico. Primeiro, resuma os argumentos de cada artigo. Depois, indique qual deles faz um argumento melhor e explique por quê.

USUÁRIO

<article> insira o primeiro artigo aqui </article> <article> insira o segundo artigo aqui </article>


SISTEMA

Você receberá um resumo de tese e um título sugerido para ela. O título da tese deve dar ao leitor uma boa ideia do tópico da tese, mas também deve ser atraente. Se o título não atender a esses critérios, sugira 5 alternativas.

USUÁRIO

Resumo: insira o resumo aqui Título: insira o título aqui


Para tarefas simples como essas, o uso de delimitadores pode não fazer diferença na qualidade da saída. No entanto, quanto mais complexa for a tarefa, mais importante é desambiguar os detalhes da tarefa. Não faça o modelo trabalhar para entender exatamente o que você está pedindo.



### 1.4 - Tática: Especifique as etapas necessárias para completar uma tarefa

Algumas tarefas são melhor especificadas como uma sequência de passos. Escrever os passos explicitamente pode facilitar para o modelo segui-los.

SISTEMA

Use as seguintes instruções passo a passo para responder às entradas do usuário. Passo 1 - O usuário fornecerá texto entre aspas triplas. Resuma este texto em uma frase com um prefixo que diz "Resumo: ". Passo 2 - Traduza o resumo do Passo 1 para espanhol, com um prefixo que diz "Tradução: ".

USUÁRIO

"""inserir texto aqui"""


### 1.5 - Tática: Fornecer exemplos

Fornecer instruções gerais que se aplicam a todos os exemplos geralmente é mais eficiente do que demonstrar todas as permutações de uma tarefa por exemplo, mas em alguns casos fornecer exemplos pode ser mais fácil. Por exemplo, se você pretende que o modelo copie um estilo particular de responder a consultas de usuários que é difícil de descrever explicitamente. Isso é conhecido como "few-shot" prompting.

SISTEMA

Responda em um estilo consistente.

USUÁRIO

Ensine-me sobre paciência.

ASSISTENTE

O rio que esculpe o vale mais profundo flui de uma modesta nascente; a mais grandiosa sinfonia origina-se de uma única nota; o mais intrincado tapeçaria começa com um fio solitário.

USUÁRIO

Ensine-me sobre o oceano.


### 1.6 - Tática: Especifique o comprimento desejado da saída

Você pode pedir ao modelo para produzir saídas que tenham um comprimento alvo específico. O comprimento de saída alvo pode ser especificado em termos da contagem de palavras, frases, parágrafos, pontos de bala, etc. No entanto, instruir o modelo para gerar um número específico de palavras não funciona com alta precisão. O modelo pode gerar saídas com um número específico de parágrafos ou pontos de bala mais confiavelmente.

USUÁRIO

Resuma o texto delimitado por aspas triplas em cerca de 50 palavras. """inserir texto aqui"""

USUÁRIO

Resuma o texto delimitado por aspas triplas em 2 parágrafos. """inserir texto aqui"""

USUÁRIO

Resuma o texto delimitado por aspas triplas em 3 pontos de bala. """inserir texto aqui"""




## 2. Fornecer texto de referência

Modelos de linguagem podem inventar respostas falsas com confiança, especialmente quando questionados sobre tópicos esotéricos ou por citações e URLs. Da mesma maneira que um conjunto de notas pode ajudar um estudante a se sair melhor em um teste, fornecer texto de referência a esses modelos pode ajudar a responder com menos fabulações.


### 2.1 - Tática: Instruir o modelo a responder usando um texto de referência

Se pudermos fornecer um modelo com informações confiáveis que são relevantes para a consulta atual, então podemos instruir o modelo a usar as informações fornecidas para compor sua resposta.

SISTEMA
Use os artigos fornecidos, delimitados por aspas triplas, para responder às perguntas. Se a resposta não puder ser encontrada nos artigos, escreva "Não consegui encontrar uma resposta."

USUÁRIO
insira artigos, cada um delimitado por aspas triplas
Pergunta: insira a pergunta aqui


### 2.2 - Tática: Instruir o modelo a responder com citações de um texto de referência

Se a entrada foi complementada com conhecimento relevante, é simples solicitar que o modelo adicione citações às suas respostas, referenciando passagens dos documentos fornecidos. Note que as citações na saída podem então ser verificadas programaticamente por correspondência de strings dentro dos documentos fornecidos.


SISTEMA
Você receberá um documento delimitado por aspas triplas e uma pergunta. Sua tarefa é responder à pergunta usando apenas o documento fornecido e citar a(s) passagem(ns) do documento usadas para responder à pergunta. Se o documento não contiver as informações necessárias para responder a esta pergunta, simplesmente escreva: "Informação insuficiente". Se uma resposta à pergunta for fornecida, ela deve ser anotada com uma citação. Use o seguinte formato para citar passagens relevantes ({"citação": …}).

USUÁRIO

"""\<insira o documento aqui>""" Pergunta: \<insira a pergunta aqui>


##  3. Divida tarefas complexas em sub-tarefas mais simples

Assim como é uma boa prática em engenharia de software decompor um sistema complexo em um conjunto de componentes modulares, o mesmo é verdadeiro para tarefas submetidas a um modelo de linguagem. Tarefas complexas tendem a ter taxas de erro mais altas do que tarefas mais simples. Além disso, tarefas complexas muitas vezes podem ser redefinidas como um fluxo de trabalho de tarefas mais simples nas quais as saídas de tarefas anteriores são usadas para construir as entradas para tarefas posteriores.

### 3.1 - Tática: Use a classificação de intenção para identificar as instruções mais relevantes para uma consulta de usuário

Para tarefas nas quais muitos conjuntos independentes de instruções são necessários para lidar com diferentes casos, pode ser benéfico primeiro classificar o tipo de consulta e usar essa classificação para determinar quais instruções são necessárias. Isso pode ser alcançado definindo categorias fixas e codificando instruções que são relevantes para lidar com tarefas em uma determinada categoria. Este processo também pode ser aplicado recursivamente para decompor uma tarefa em uma sequência de estágios. A vantagem dessa abordagem é que cada consulta conterá apenas aquelas instruções que são necessárias para realizar o próximo estágio de uma tarefa, o que pode resultar em taxas de erro menores em comparação ao uso de uma única consulta para realizar toda a tarefa. Isso também pode resultar em custos menores, já que prompts maiores custam mais para serem executados.

Suponha, por exemplo, que para uma aplicação de serviço ao cliente, as consultas pudessem ser classificadas da seguinte maneira:

SISTEMA

Você receberá consultas de serviço ao cliente. Classifique cada consulta em uma categoria primária e uma secundária. Forneça sua saída em formato json com as chaves: primária e secundária. Categorias primárias: Cobrança, Suporte Técnico, Gerenciamento de Conta ou Consulta Geral. Categorias secundárias de Cobrança: - Cancelar assinatura ou fazer upgrade - Adicionar um método de pagamento - Explicação para cobrança - Disputar uma cobrança Categorias secundárias de Suporte Técnico: - Solução de problemas - Compatibilidade de dispositivo - Atualizações de software Categorias secundárias de Gerenciamento de Conta: - Redefinição de senha - Atualizar informações pessoais - Fechar conta - Segurança da conta Categorias secundárias de Consulta Geral: - Informações do produto - Preços - Feedback - Falar com um humano

USUÁRIO

Eu preciso fazer minha internet funcionar novamente.

Com base na classificação da consulta do cliente, um conjunto de instruções mais específicas pode ser fornecido a um modelo para que ele possa lidar com os próximos passos. Por exemplo, suponha que o cliente precise de ajuda com "solução de problemas".

SISTEMA

Você receberá consultas de serviço ao cliente que requerem solução de problemas em um contexto de suporte técnico. Ajude o usuário: - Peça-lhes para verificar se todos os cabos do/para o roteador estão conectados. Note que é comum os cabos se soltarem com o tempo. - Se todos os cabos estiverem conectados e o problema persistir, pergunte-lhes qual é o modelo do roteador que estão usando - Agora você os aconselhará sobre como reiniciar o dispositivo: -- Se o número do modelo for MTD-327J, aconselhe-os a pressionar o botão vermelho e segurá-lo por 5 segundos, depois esperar 5 minutos antes de testar a conexão. -- Se o número do modelo for MTD-327S, aconselhe-os a desligar e ligar novamente, depois esperar 5 minutos antes de testar a conexão. - Se o problema do cliente persistir após reiniciar o dispositivo e esperar 5 minutos, conecte-os ao suporte de TI emitindo {"Suporte de TI solicitado"}. - Se o usuário começar a fazer perguntas não relacionadas a este tópico, confirme se eles gostariam de encerrar o bate-papo atual sobre solução de problemas e classifique seu pedido de acordo com o esquema de classificação primária/secundária acima.

USUÁRIO

Eu preciso fazer minha internet funcionar novamente.

Perceba que o modelo foi instruído a emitir strings especiais para indicar quando o estado da conversa muda. Isso nos permite transformar nosso sistema em uma máquina de estado onde o estado determina quais instruções são injetadas. Ao acompanhar o estado, quais instruções são relevantes nesse estado e também, opcionalmente, quais transições de estado são permitidas a partir desse estado, podemos colocar guardas em torno da experiência do usuário que seriam difíceis de alcançar com uma abordagem menos estruturada.



### 3.4 - Tática: Para aplicações de diálogo que requerem conversas muito longas, resuma ou filtre diálogos anteriores

Como os modelos têm um comprimento de contexto fixo, o diálogo entre um usuário e um assistente no qual toda a conversa é incluída na janela de contexto não pode continuar indefinidamente.

Existem várias soluções para este problema, uma delas é resumir turnos anteriores na conversa. Uma vez que o tamanho da entrada atinge um comprimento limite predeterminado, isso pode acionar uma consulta que resume parte da conversa e o resumo da conversa anterior pode ser incluído como parte da mensagem do sistema. Alternativamente, a conversa anterior pode ser resumida de forma assíncrona ao longo de toda a conversa.



### 3.5 - Tática: Resuma documentos longos por partes e construa um resumo completo recursivamente

Como os modelos têm um comprimento de contexto fixo, eles não podem ser usados para resumir um texto mais longo do que o comprimento do contexto menos o comprimento do resumo gerado em uma única consulta.

Para resumir um documento muito longo, como um livro, podemos usar uma sequência de consultas para resumir cada seção do documento. Resumos de seções podem ser concatenados e resumidos produzindo resumos de resumos. Esse processo pode prosseguir recursivamente até que um documento inteiro seja resumido. Se for necessário usar informações sobre seções anteriores para fazer sentido de seções posteriores, então um truque adicional que pode ser útil é incluir um resumo em execução do texto que precede qualquer ponto dado no livro enquanto se resume o conteúdo nesse ponto. A eficácia deste procedimento para resumir livros foi estudada em pesquisas anteriores da OpenAI usando variantes do GPT-3.


Tradução completa do texto solicitado:

## 4. Dê tempo ao modelo para "pensar"

Se for pedido para multiplicar 17 por 28, você pode não saber instantaneamente, mas ainda pode calcular com tempo. Da mesma forma, os modelos cometem mais erros de raciocínio ao tentar responder imediatamente, em vez de tomar tempo para calcular uma resposta. Pedir por uma "cadeia de raciocínio" antes de uma resposta pode ajudar o modelo a raciocinar de forma mais confiável em direção a respostas corretas.

### 4.1 - Tática: Instrua o modelo a calcular sua própria solução antes de chegar a uma conclusão

Às vezes, obtemos melhores resultados quando instruímos explicitamente o modelo a raciocinar a partir de primeiros princípios antes de chegar a uma conclusão. Suponha, por exemplo, que queremos que um modelo avalie a solução de um aluno para um problema de matemática. A maneira mais óbvia de abordar isso é simplesmente perguntar ao modelo se a solução do aluno está correta ou não.

SISTEMA

Determine se a solução do aluno está correta ou não.

USUÁRIO

Declaração do Problema: Estou construindo uma instalação de energia solar e preciso de ajuda para calcular as finanças. - O terreno custa $100 por pé quadrado - Posso comprar painéis solares por $250 por pé quadrado - Negociei um contrato de manutenção que custará $100k fixos por ano, e um adicional de $10 por pé quadrado Qual é o custo total para o primeiro ano de operações como função do número de pés quadrados. Solução do Aluno: Seja x o tamanho da instalação em pés quadrados. 1. Custo do terreno: 100x 2. Custo do painel solar: 250x 3. Custo de manutenção: 100,000 + 100x Custo total: 100x + 250x + 100,000 + 100x = 450x + 100,000

ASSISTENTE

A solução do aluno está correta.


Mas a solução do aluno na verdade não está correta! Podemos fazer com que o modelo perceba isso instruindo o modelo a gerar sua própria solução primeiro.

SISTEMA

Primeiro, calcule sua própria solução para o problema. Em seguida, compare sua solução com a solução do aluno e avalie se a solução do aluno está correta ou não. Não decida se a solução do aluno está correta até que você tenha feito o problema por conta própria.

USUÁRIO

Declaração do Problema: Estou construindo uma instalação de energia solar e preciso de ajuda para calcular as finanças. - O terreno custa $100 por pé quadrado - Posso comprar painéis solares por $250 por pé quadrado - Negociei um contrato de manutenção que custará $100k fixos por ano, e um adicional de $10 por pé quadrado Qual é o custo total para o primeiro ano de operações como função do número de pés quadrados. Solução do Aluno: Seja x o tamanho da instalação em pés quadrados. 1. Custo do terreno: 100x 2. Custo do painel solar: 250x 3. Custo de manutenção: 100,000 + 100x Custo total: 100x + 250x + 100,000 + 100x = 450x + 100,000

ASSISTENTE

Seja x o tamanho da instalação em pés quadrados. 1. Custo do terreno: 100x 2. Custo do painel solar: 250x 3. Custo de manutenção: 100,000 + 10x Custo total: 100x + 250x + 100,000 + 10x = 360x + 100,000 A solução do aluno está incorreta. Eles cometeram um erro no cálculo do custo de manutenção, usando 100x em vez de 10x. O custo total correto para o primeiro ano de operações é 360x + 100,000.


### 4.2 - Tática: Use monólogo interno ou uma sequência de consultas para ocultar o processo de raciocínio do modelo

A tática anterior demonstra que às vezes é importante para o modelo raciocinar em detalhes sobre um problema antes de responder a uma pergunta específica. Para algumas aplicações, o processo de raciocínio que um modelo usa para chegar a uma resposta final seria inadequado para compartilhar com o usuário. Por exemplo, em aplicações de tutoria, podemos querer encorajar os alunos a trabalharem em suas próprias soluções, mas o processo de raciocínio do modelo sobre a solução do aluno poderia revelar a resposta ao aluno.

Monólogo interno é uma tática que pode ser usada para mitigar isso. A ideia do monólogo interno é instruir o modelo a colocar partes da saída que devem ser ocultadas do usuário em um formato estruturado que torne fácil a sua análise. Então, antes de apresentar a saída ao usuário, a saída é analisada e apenas parte da saída é tornada visível.

SISTEMA

Siga estes passos para responder às consultas do usuário. Passo 1 - Primeiro, calcule sua própria solução para o problema. Não confie na solução do aluno, pois ela pode estar incorreta. Encapsule todo o seu trabalho para esta etapa entre aspas triplas ("""). Passo 2 - Compare sua solução com a solução do aluno e avalie se a solução do aluno está correta ou não. Encapsule todo o seu trabalho para esta etapa entre aspas triplas ("""). Passo 3 - Se o aluno cometeu um erro, determine que dica você poderia dar ao aluno sem revelar a resposta. Encapsule todo o seu trabalho para esta etapa entre aspas triplas ("""). Passo 4 - Se o aluno cometeu um erro, forneça a dica da etapa anterior ao aluno (fora das aspas triplas). Em vez de escrever "Passo 4 - ..." escreva "Dica:".

USUÁRIO

Declaração do Problema: \<inserir declaração do problema> Solução do Aluno: \<inserir solução do aluno>



Alternativamente, isso pode ser alcançado com uma sequência de consultas nas quais todas, exceto a última, têm sua saída ocultada do usuário final.

Primeiro, podemos pedir ao modelo para resolver o problema por conta própria. Como essa consulta inicial não requer a solução do aluno, ela pode ser omitida. Isso oferece a vantagem adicional de não haver chance de a solução do modelo ser influenciada pela tentativa de solução do aluno.

USUÁRIO

\<inserir declaração do problema\>



Em seguida, podemos fazer com que o modelo use todas as informações disponíveis para avaliar a correção da solução do aluno.

SISTEMA

Compare sua solução com a solução do aluno e avalie se a solução do aluno está correta ou não.

USUÁRIO

Declaração do problema: """\<inserir declaração do problema>""" Sua solução: """\<inserir solução gerada pelo modelo>""" Solução do Aluno: """<inserir solução do aluno>"""



Finalmente, podemos deixar o modelo usar sua própria análise para construir uma resposta na persona de um tutor útil.

SISTEMA

Você é um tutor de matemática. Se o aluno cometeu um erro, ofereça uma dica ao aluno de uma maneira que não revele a resposta. Se o aluno não cometeu um erro, simplesmente ofereça um comentário encorajador.

USUÁRIO

Declaração do problema: """\<inserir declaração do problema>""" Sua solução: """\<inserir solução gerada pelo modelo>""" Solução do Aluno: """<inserir solução do aluno>""" Análise: """\<inserir análise gerada pelo modelo da etapa anterior>"""



### 4.3 - Tática: Pergunte ao modelo se ele perdeu alguma coisa em passagens anteriores

Suponha que estamos usando um modelo para listar trechos de uma fonte que são relevantes para uma pergunta específica. Após listar cada trecho, o modelo precisa determinar se deve começar a escrever outro ou se deve parar. Se o documento-fonte for grande, é comum que o modelo pare cedo demais e falhe em listar todos os trechos relevantes. Nesse caso, um desempenho melhor pode ser frequentemente obtido solicitando ao modelo consultas de acompanhamento para encontrar quaisquer trechos que tenha perdido em passagens anteriores.

SISTEMA

Você receberá um documento delimitado por aspas triplas. Sua tarefa é selecionar trechos que se relacionem com a seguinte pergunta: "Quais mudanças de paradigma significativas ocorreram na história da inteligência artificial." Garanta que os trechos contenham todo o contexto relevante necessário para interpretá-los - em outras palavras, não extraia pequenos trechos que estejam faltando contexto importante. Forneça a saída no formato JSON da seguinte forma: \[{"trecho": "..."}, ... {"trecho": "..."}]

USUÁRIO

"""\<inserir documento aqui>"""

ASSISTENTE

\[{"trecho": "o modelo escreve um trecho aqui"}, ... {"trecho": "o modelo escreve outro trecho aqui"}]

USUÁRIO

Existem mais trechos relevantes? Tenha cuidado para não repetir trechos. Também garanta que os trechos contenham todo o contexto relevante necessário para interpretá-los - em outras palavras, não extraia pequenos trechos que estejam faltando contexto importante.


## 5. Use ferramentas externas

Compense as fraquezas do modelo alimentando-o com as saídas de outras ferramentas. Por exemplo, um sistema de recuperação de texto (às vezes chamado de RAG ou geração aumentada por recuperação) pode informar o modelo sobre documentos relevantes. Um motor de execução de código, como o Interpretador de Código da OpenAI, pode ajudar o modelo a fazer cálculos matemáticos e executar códigos. Se uma tarefa puder ser feita de maneira mais confiável ou eficiente por uma ferramenta do que por um modelo de linguagem, transfira-a para obter o melhor dos dois mundos.


### 5.1 -  Tática: Use a busca baseada em embeddings para implementar a recuperação eficiente de conhecimento

Um modelo pode aproveitar fontes externas de informação se fornecidas como parte de sua entrada. Isso pode ajudar o modelo a gerar respostas mais informadas e atualizadas. Por exemplo, se um usuário fizer uma pergunta sobre um filme específico, pode ser útil adicionar informações de alta qualidade sobre o filme (por exemplo, atores, diretor, etc.) à entrada do modelo. Embeddings podem ser usados para implementar a recuperação eficiente de conhecimento, de modo que informações relevantes possam ser adicionadas à entrada do modelo dinamicamente em tempo de execução.

Um embedding de texto é um vetor que pode medir a relação entre strings de texto. Strings similares ou relevantes estarão mais próximas do que strings não relacionadas. Este fato, juntamente com a existência de algoritmos de busca de vetores rápidos significa que embeddings podem ser usados para implementar a recuperação eficiente de conhecimento. Em particular, um corpus de texto pode ser dividido em pedaços, e cada pedaço pode ser embutido e armazenado. Então, uma dada consulta pode ser embutida e uma busca de vetor pode ser realizada para encontrar os pedaços de texto embutidos do corpus que são mais relacionados à consulta (ou seja, mais próximos no espaço de embedding).

Implementações de exemplo podem ser encontradas no [OpenAI Cookbook](https://cookbook.openai.com/examples/vector_databases/readme). Veja a tática ["Instrua o modelo a usar conhecimento recuperado para responder a consultas"](https://platform.openai.com/docs/guides/prompt-engineering/tactic-instruct-the-model-to-answer-using-a-reference-text) para um exemplo de como usar a recuperação de conhecimento para minimizar a probabilidade de que um modelo invente fatos incorretos.


### 5.2 - Tática: Use execução de código para realizar cálculos mais precisos ou chamar APIs externas

Modelos de linguagem não podem ser confiáveis para realizar cálculos aritméticos ou longos cálculos com precisão por conta própria. Em casos onde isso é necessário, um modelo pode ser instruído a escrever e executar código em vez de fazer seus próprios cálculos. Em particular, um modelo pode ser instruído a colocar o código que se destina a ser executado em um formato designado, como aspas triplas invertidas. Após a produção de uma saída, o código pode ser extraído e executado. Finalmente, se necessário, a saída do motor de execução de código (ou seja, interpretador Python) pode ser fornecida como uma entrada para o modelo para a próxima consulta.

SISTEMA

Você pode escrever e executar código Python encapsulando-o em aspas triplas invertidas, por exemplo, ```o código vai aqui```. Use isso para realizar cálculos.

USUÁRIO

Encontre todas as raízes de valor real do seguinte polinômio: 3*x**5 - 5*x**4 - 3*x**3 - 7*x - 10.


Outro bom caso de uso para execução de código é chamar APIs externas. Se um modelo for instruído no uso adequado de uma API, ele pode escrever código que faça uso dela. Um modelo pode ser instruído sobre como usar uma API fornecendo-lhe documentação e/ou exemplos de código mostrando como usar a API.

SISTEMA

Você pode escrever e executar código Python encapsulando-o em aspas triplas invertidas. Observe também que você tem acesso ao seguinte módulo para ajudar os usuários a enviar mensagens aos seus amigos: ```python import message message.write(to="John", message="Ei, quer se encontrar depois do trabalho?")```


**AVISO: Executar código produzido por um modelo não é inerentemente seguro e precauções devem ser tomadas em qualquer aplicação que busque fazer isso. Em particular, um ambiente de execução de código em sandbox é necessário para limitar o dano que o código não confiável poderia causar.**


### 5.3 - Tática: Dê ao modelo acesso a funções específicas

A API Chat Completions permite passar uma lista de descrições de funções nas solicitações. Isso permite que os modelos gerem argumentos de função de acordo com os esquemas fornecidos. Argumentos de função gerados são retornados pela API em formato JSON e podem ser usados para executar chamadas de função. A saída fornecida pelas chamadas de função pode então ser alimentada de volta ao modelo na solicitação seguinte para fechar o ciclo. Esta é a maneira recomendada de usar os modelos da OpenAI para chamar funções externas. Para saber mais, veja a [seção de chamada de funções](https://platform.openai.com/docs/guides/function-calling) em nosso guia introdutório de geração de texto e mais [exemplos de chamada de funções](https://cookbook.openai.com/examples/how_to_call_functions_with_chat_models) no OpenAI Cookbook.

