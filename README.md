# ![image](https://github.com/user-attachments/assets/7c673f4d-5c21-4104-ad44-4c8ebc5dde53) Microsoft Copilot
No site https://copilotstudio.microsoft.com/ é possível criar a partir de um Ambiente (https://admin.powerplatform.microsoft.com) e Solução (https://make.powerapps.com/) copilotos personalizados.

## :hammer: Como criar copilots

**- :green_book: A partir de um modelo**
Existem diversos modelos com bases de conhecimentos próprias para a criação de copilots: viagens; perguntas e respostas do site; navegador de equipes; assistência técnica de TI; operações de lojas; insights inanceiros; etc...

**- :arrow_forward: A partir do prompt**
A estrutura básica é criada a partir do prompt fornecido pelo usuário

**- :information_source: De ponta a ponta**
O usuário define os diversos pontos para a criação do agente

## :scroll: Tópicos

- São conversas fixas dentro de um copilot, que permitem seguir fluxos pré-definidos de informação, melhorando a experiência na conversa com o usuário
  **Tópicos de sistema** são criados pela própria Microsoft (respostas comuns como saudação, frases não aceitas etc.)
- **Tópicos customizados** são criados para a partir do gatilho com frases do usuário, disparar uma ou mais ações
- Atualmente, têm sido substituído pela inteligência generativa, que consegue gerar respostas a partir de uma base de conhecimento (ações com conectores)

:hammer: Pode-se criar um tópico através de prompt, informando o que se deseja e podendo colocar entre colchetes (**[]**) variáveis que será obtidas da soliciação do usuário.

:link: O site https://aka.ms/power-prompts oferece uma galeria colaborativa de prompts modelo que podem ser aproveitados para a criação de copilots

**:ballot_box_with_check: Boas práticas para criação de tópicos**
- Ter de 5 a 10 frases dentre de um gatilho e que não conflite com outros gatilhos (de preferência vindas dos usuários)
- Ter nomes claros e não repetitivos
- Ter em mente quando dividir os tópitos ou copilotos diferentes, de modo a evitar ramificações grandes demais, favorecendo a manutenção do código com o redirecionamento entre tópicos

**:twisted_rightwards_arrows: Ramificação de tópicos**

Na ramificação, são incluídas condicionais (novas perguntas) a partir da resposta inicial, para levar o usuário para respostas mais detalhadas conforme sua necessidade.
Após definir a pergunta, pode-se criar condicionais e as ações a serem tomadas: uma nova pergunta, retornar ou avançar para um passo específico do tópico (alterar comportamento para "Perguntar toda vez"), ir para outro tópico ou encerrar a conversa.

## :x: Lidando com falhas no Copilot

Atualmente temos duas alternativas para definir ações para falhas no Copilot: utilizar IA Gnerativa para dar uma respota ou utilizar Fallback do Sistema (oferecer um canal de atendimento ou registrar as falhas e encaminhar para uma equipe - escalonar), que é um Tópico do Sistema

##  :symbols: Entidades e Variáveis

### :capital_abcd: Entidades 

Compreende uma parte significtiva ds conversas do copiloto, pois envolve o reconhecimento de linguagem natural, que é a capacidade da IA de compreender a interação do usuário. Uma **entidade** é uma unidade de informação que representa um certo tipo de assunto. Facilitam as entradas do usuário sem a necessidade de usar a parte de Resposta Generativa ou AI Builder dentro do Copilot Studio para reconhecer informações já mapeadas.

O **preenchicmento de slot** é um conceito de reconhecimento de linguagem natural que significa salvar uma entidade extraída para um objeto. No Copilot, significa colocar o **valor da entidade** extraída em uma **variável**.

Existem **entidades predefinidas** como idade, cidade, verdadeiro ou falso, cor; e **entidades personalizadas**, que podem ser criadas através de uma lista fechada (closed list) ou expressão regular (regex para .NET), disponível em **Configurações/Entidades**.

### :abcd: Variáveis 

As **variáveis** servem para salvar respotas do usuário e reutilizar seu conteúdo posteriormente na conversa. Também podem ser empregadas em expressões lógicas que direcionam dinamicamente o usuário por diferentes caminhos na conversa.

As variáveis podem ser **de tópico**, que tem escopo restrito ao tópico no qual sao criadas; **globais** tem escopo de sessão, mantendo-se enquanto a conversa não é encerrada; **de sistema** criadas pela microsoft (dados do usuário, canais); e **de ambiente** variáveis customizadas criadas pela solução ou ambiente.

Os **tipos bases das variáveis** são cadeia de caracteres, booleano, número, tabela, registro, DateTime, opção e em branco.

## :negative_squared_cross_mark: Funções ([Power FX]([url](https://learn.microsoft.com/pt-br/power-platform/power-fx/overview)))

O Power Fx é a linguagem de pouco código, de uso geral, fortemente tipada, declarativa e funcional; com a qual os criadores podem trabalhar diretamente em uma barra de fórmulas semelhante ao Excel ou uma janela de texto do Visual Studio Code.

As fórmulas começam com "=" e podem usar funções como Today() ou Format(), operadores como "&" para concatenação, e referências a variáveis com prefixos específicos (ex.: System.Conversation.Id para acessar o ID da conversa).

No contexto de copilots, há uma ênfase especial no uso de prefixos para indicar o escopo das variáveis, como:
- **System.:** Para variáveis do sistema, como System.Conversation.Id, que acessa o ID da conversa, conforme mencionado em Create expressions using Power Fx.
- **Global.:** Para variáveis globais, úteis para compartilhar dados entre diferentes partes do copilot.
- **Topic.:** Para variáveis específicas de tópicos, usadas em fluxos de conversa.

Exemplos de uso mais comuns:

- **Mostrar a data atual:** = Today().
- **Formatá-la:** = Format(Today(), "dddd, MMMM d, yyyy") (exibe, por exemplo, "Wednesday, February 26, 2025").
- **Decidir respostas com base em condições:** If(Mood = "happy", "Great to hear that!", "Sorry to hear that.").
- **Contar itens em uma lista:** = CountIf(List, Condition).
- **Guardar histórico da conversa:** Concatenate(Global.varHistoricoConversa, "Nova mensagem: ", Topic.VarValorDoServico, Topic.locLinkLugarDeInspiracao)
