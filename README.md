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
- **Tópicos de sistema** são criados pela própria Microsoft (respostas comuns como saudação, frases não aceitas etc.)
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

### Entidades 

Compreende uma parte significtiva ds conversas do copiloto, pois envolve o reconhecimento de linguagem natural, que é a capacidade da IA de compreender a interação do usuário. Uma **entidade** é uma unidade de informação que represnta um certo tipo de assunto.

O **preenchicmento de slot** é um conceito de reconhecimento de linguagem natural que significa salvar uma entidade extraída para um objeto. No Copilot, significa colocar o **valor da entidade** extraída em uma **variável**.

### Variáveis 
