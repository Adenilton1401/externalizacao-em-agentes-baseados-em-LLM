# Externalização em Agentes Baseados em LLM

Esse repositório tem por objetivo centralizar fontes de conhecimento para um NotebookLM que auxilie no estudo de assuntos de IA como agentes, memória, skills, protocolos e engenharia de harness e outros

## Contexto e Ojbetivo:
O estudo acerca de temas relacionados a Inteligência Artificial ganha novos tópicos diariamente, haja vistos que IA, embora não seja uma área do conecimento humano tão recente, tem ganhado cada vez mais importância na sociedade moderna, uma vez que a aplicação dessa tecnologia vem sendo utilizada por empresas para resolver problemas que tocam diretamente o cidadão comum.

Os estudos de IA que antes era mais restrido a um grupo muito menor de pessoas apenas em centros de pesquisas de grandes empresas, governos e universidades, hoje já está mais disperso e vem sendo objeto de estudo de pessoas que desejam trabalhar com ou desenvolver soluções que utilizem modelos de linguagem de grande escala como uma peça fundamenta no processo de execução da solução. Nesse processo de apredizagem, nos deparamos com novos termos todos os dias e precisamos entende-los a fundo para que possamos construir soluções robustas e confiáveis com IA.

Termos com agentes, engenharia de prompt, engenharia de contexto, memória, observalidade, skills, protocolos e harness são alguns dois quais as pessoas que querem aprimorar seuas conhecimentos sobre inteligência artificial vai se deparar no processo de aprendizagem principalmente se olha para os elementos que orbitam os LLMs. 

Para auxiliar nesse processo de aprendizagem, a utilização de um NotebookLM que centralize a definição de alguns desses termos pode ser uma ferramenta facilitadora por tazer cosigo recursos como resumos em áudio, apresentações, mapas mentais, cartões didáticos e outros.

## Curadoria de Fontes:
### - PDFs
Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering - disponível em: https://arxiv.org/pdf/2604.08224

### - Links
https://www.ibm.com/br-pt/think/topics/artificial-intelligence

https://www.anthropic.com/news/model-context-protocol

https://blog.dsacademy.com.br/alem-do-prompt-um-guia-definitivo-sobre-context-engineering-engenharia-de-contexto/

https://www.anthropic.com/news/model-context-protocol

https://www.ibm.com/br-pt/think/topics/artificial-intelligence

## Engenharia de Prompts e "Cicatrizes":

### Zero-Shot Prompting:
Entrada: O que é janela de contexto?

Saida: "A janela de contexto é o espaço efêmero de entrada de dados onde um grande modelo de linguagem (LLM) recebe, mantém e processa informações durante uma interação ou etapa de raciocínio. Ela atua como uma superfície de trabalho na qual desenvolvedores e sistemas organizam instruções locais, esquemas de saída, regras de domínio e documentos recuperados para que o modelo possa agir sobre eles
. Segundo os documentos fornecidos, a janela de contexto possui as seguintes características e limitações centrais no design de agentes autônomos:
É o recurso mais escasso do sistema: A janela de contexto é finita e custosa em larga escala. Elementos como recuperação de memórias passadas, carregamento de habilidades, chamadas de ferramentas e os próprios traços de raciocínio do modelo competem simultaneamente pelo mesmo orçamento limitado de tokens.

É inerentemente efêmera: Os LLMs são geradores sem estado (stateless), o que significa que cada nova chamada se inicia com um contexto limpo. A menos que o estado da tarefa seja explicitamente salvo em um armazenamento externo, todo o progresso ou histórico de conversas desaparece assim que a sessão termina ou é interrompida, resultando em "amnésia parcial".

É vulnerável à degradação de desempenho: Embora a capacidade das janelas de contexto tenha se expandido drasticamente (indo de 2 mil para mais de 100 mil tokens), inserir informações em excesso pode degradar a performance em vez de melhorá-la.

O excesso de dados causa ruído e desencadeia o fenômeno de "lost in the middle" (perdido no meio), onde a capacidade de atenção do modelo falha e a precisão de recuperação cai drasticamente para informações posicionadas no centro de um prompt longo.
Tentar forçar o modelo a carregar todo o seu histórico, ferramentas e raciocínio dentro de uma janela de contexto efêmera e limitada cria um problema estrutural de continuidade.

É justamente por causa das limitações da janela de contexto que os sistemas de IA modernos passaram a focar na externalização: transferir esse peso cognitivo para infraestruturas externas (como sistemas de memória persistentes e bibliotecas de habilidades), permitindo uma curadoria seletiva e dinâmica do que realmente precisa ser inserido na janela de contexto a cada nova decisão."

### Few-Shot Prompting
Entrada: Crie uma lista de chave/valor para os principais elementos da janela de contexto seguindo o padão chave (elemento) -> Valor (conceito).

Saída: "Instruções de Sistema / Prompt de Sistema -> O conjunto fundamental de regras e a definição da persona do modelo, que estabelecem o cenário, o comportamento esperado e as diretrizes que guiarão o LLM.

Prompt do Usuário -> A tarefa ou pergunta imediata e específica fornecida pelo usuário, sendo o principal componente trabalhado na Engenharia de Prompt tradicional.

Histórico da Conversa (Memória de Curto Prazo) -> O registro com estado da interação atual (entradas do usuário e respostas do modelo), que é fundamental para manter a coerência da conversa e processar perguntas de acompanhamento.

Informações Recuperadas (RAG) -> O conhecimento externo buscado dinamicamente em documentos e bancos de dados para fornecer informações factuais, atualizadas e específicas de um domínio para fundamentar a resposta.

Memória de Longo Prazo -> O armazenamento de conhecimento persistente ao longo de múltiplas sessões, responsável por reter preferências do usuário, resumos de projetos e fatos importantes indefinidamente.

Ferramentas Disponíveis e Respostas de API -> As definições de funções e ferramentas externas que o modelo tem permissão para invocar, além dos resultados obtidos por essas chamadas que são reinseridos para a próxima etapa de raciocínio.

Esquemas de Saída Estruturada -> As definições prévias do formato exigido para a resposta final (como JSON ou XML), servindo para guiar o modelo a produzir saídas previsíveis e legíveis por máquina."

### Zero-Shot Prompting
Entrada: Por que o harness funciona como uma camada de unificação?

Saída: "O harness (ambiente de orquestração ou "chicote/arnês" de engenharia) funciona como uma camada de unificação porque ele fornece o ambiente de execução (runtime) contínuo que hospeda, coordena e governa todas as infraestruturas externalizadas de um modelo de linguagem, unindo a memória, as skills e os protocolos em um fluxo de trabalho coeso. Sem ele, esses módulos existiriam apenas como recursos isolados, carecendo de uma estrutura com princípios definidos para coordenar suas interações ao longo do tempo.
Em vez de ser visto como um quarto tipo de externalização, o harness é a própria infraestrutura persistente que envolve o modelo e atua como seu "ambiente cognitivo". Ele desempenha essa função unificadora através das seguintes frentes:

Orquestração do Ciclo do Agente (Agent Loop): O harness fornece a espinha dorsal temporal do sistema, alinhando de maneira contínua a percepção do ambiente, o acesso à memória, a seleção e execução de skills e o monitoramento de resultados. Ele define as rotas exatas pelas quais o LLM deve receber contexto, invocar ferramentas e interagir com o mundo.

Superfícies de Operação e Governança: Um modelo fundacional por si só possui apenas a capacidade de inferência, mas não entende limites de infraestrutura. O harness unifica a operação através de três superfícies críticas: Permissão (sandboxing, isolamento de sistema de arquivos e redes), Controle (limites de recursão, teto de custos e timeouts) e Observabilidade (registro de traces de execução, logs estruturados e métricas de feedback). Isso garante que a atuação do agente seja sempre delimitada, segura e auditável.

Gerenciamento do Orçamento da Janela de Contexto: Como a janela de contexto é o recurso compartilhado mais escasso do sistema, o harness atua como o alocador central. Ele orquestra o que entra no prompt em cada fase da execução, balanceando a injeção de históricos da memória, a carga progressiva de detalhes de uma skill e os esquemas dos protocolos, evitando que o modelo sofra com ruído de informações.

Dessa forma, a unificação proporcionada pelo harness transforma a inteligência de um LLM. O modelo deixa de ser apenas um gerador de texto que tenta resolver toda a carga de trabalho de forma efêmera e se torna um agente autônomo governado, onde o estado temporal (memória), os procedimentos (skills) e as estruturas de comunicação (protocolos) operam de modo sincronizado e seguro."

### Role-Playing (adoção de persona)
Entrada: Aja como um experiente engenheiro de harness e descreva um workflow ótimo para um harness.

Saída: "omo engenheiro de harness, minha premissa fundamental é que o modelo de linguagem (LLM) por si só não é o agente completo; ele é apenas o "motor cognitivo". A verdadeira inteligência e confiabilidade do sistema emergem do ambiente estruturado que orquestra suas ações
. Para transformar a capacidade bruta do modelo em uma operação segura e contínua, o workflow ótimo de um harness deve alinhar dinamicamente a memória, as skills e os protocolos, governando cada etapa do processo.

Abaixo, descrevo a arquitetura ideal desse ciclo de execução temporal (o Agent Loop), desde o recebimento de uma tarefa até a consolidação do aprendizado:

1. Captura de Intenção e Gestão do Orçamento de Contexto Quando a solicitação do usuário chega, o harness não passa o texto livre imediatamente para o modelo. A primeira etapa é a captura e normalização da intenção, mapeando a solicitação para objetos de protocolo validados e checando as permissões iniciais
. Neste momento, o harness atua como o alocador do orçamento da janela de contexto — que, como discutimos antes, é escassa e suscetível à degradação se sobrecarregada
. Ele resume o histórico da conversa e limpa variáveis obsoletas, mantendo apenas o estado de trabalho ativo (o working context) e as abstrações relevantes na "memória quente".
2. Recuperação de Estado (Memória) e Descoberta de Skills Em seguida, o harness consulta o sistema de memória para recuperar trajetórias passadas, regras do projeto e preferências do usuário aplicáveis à tarefa
. Usando esses dados, o sistema busca no registro de skills quais procedimentos são adequados
. Para otimizar o prompt, aplicamos a estratégia de divulgação progressiva (progressive disclosure): o harness insere no contexto apenas o nome, os pré-requisitos e o escopo da skill; o guia detalhado e as rotinas só são carregados se o modelo confirmar que aquele procedimento é necessário.
3. O Ciclo de Raciocínio Governado (Agent Loop & Control Flow) Com a informação certa disponível, o agente inicia seu ciclo de perceber-recuperar-planejar-agir-observar
. Como engenheiro, não posso confiar que o modelo saiba parar sozinho ou evitar loops infinitos. Por isso, o harness impõe controles de infraestrutura estritos sobre este loop:
- Limites operacionais: Aplicamos limites de passos (step counts), profundidade máxima de recursão, tetos de custo financeiro e timeouts de segurança.
- Isso define o "envelope operacional", garantindo que a deliberação do modelo ocorra sempre dentro de limites computacionais e financeiros aceitáveis.
4. Binding de Protocolos, Sandboxing e Portões de Aprovação Quando o modelo decide realizar uma ação usando uma skill carregada, o harness deve traduzir essa intenção em realidade. Isso é feito vinculando a skill a uma interface executável governada por protocolos padronizados, como o Model Context Protocol (MCP) para ferramentas, ou protocolos de delegação (A2A) para se comunicar com subagentes
. Nesta fase, a segurança é a prioridade:
- Sandboxing: Se a ação altera arquivos ou exige chamadas de sistema, a execução é roteada para um ambiente isolado (sandbox), com restrições rígidas de rede e de sistema de arquivos.
- Supervisão Humana (Human-in-the-loop): Para ações críticas ou irreversíveis (como manipulação de banco de dados ou envios de e-mail), o harness possui portões de aprovação, pausando a execução até que um operador humano valide o rastro de ações.
5. Assimilação de Resultados, Observabilidade e Evolução Contínua A execução produzirá sucessos, dados brutos ou mensagens de erro. O harness assimila esses resultados e os normaliza, traduzindo-os de volta em um estado que atualiza a memória de longo e curto prazo
. Simultaneamente, a camada de observabilidade entra em ação registrando logs estruturados de toda a trajetória: quais ferramentas falharam, os custos gerados e os ramos de decisão escolhidos.
  
É esse último passo que permite a evolução do sistema: os logs estruturados são destilados em novas memórias episódicas, que, mais tarde, podem ser usadas para revisar uma skill falha, alterar uma política de roteamento ou promover uma tática improvisada de sucesso em um novo procedimento operacional padrão.

Em resumo, este fluxo garante que a carga de lidar com formatos sintáticos, limites computacionais, restrições de tempo e segurança permaneça no sistema de infraestrutura
. O modelo de linguagem trabalha de forma central, mas focado exclusivamente na interpretação cognitiva, enquanto o harness funciona como seu corpo cibernético e seu supervisor rigoroso."

## Miniguia de Estudo:
