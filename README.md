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


## Miniguia de Estudo:
