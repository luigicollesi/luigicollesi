# Oi, eu sou o Luigi 👋

Sou estudante de **Engenharia da Computação no Instituto Mauá de Tecnologia**, com formação prevista para o fim de 2027, e venho direcionando meus projetos para desenvolvimento de software full-stack.

Tenho trabalhado principalmente com **TypeScript, React, Next.js e Node.js**, além de React Native, NestJS e integrações de IA. Gosto especialmente da parte que começa quando a primeira versão já funciona: organizar responsabilidades, sincronizar estado, estruturar persistência, lidar com falhas e manter a base de código compreensível conforme ela cresce.

## Projetos em destaque

### [WAR Brasil](https://github.com/luigicollesi/war-brasil)

Um jogo de estratégia multiplayer em um mapa interativo do Brasil, com 42 territórios, salas, lobbies sincronizados e as regras do jogo funcionando dentro de uma aplicação web completa.

[Versão online](https://war-brasil.vercel.app)

Esse se tornou um dos meus maiores projetos e também um espaço onde tenho trabalhado de forma mais intencional na arquitetura da aplicação. O código separa responsabilidades entre `client`, `server` e `shared`, enquanto os Route Handlers do Next.js funcionam como a fronteira HTTP para a lógica executada no servidor.

O estado das salas e dos jogadores é persistido em PostgreSQL, que funciona como fonte de verdade para informações como configuração dos jogadores, estado de prontidão e inicialização das partidas. O projeto também possui migrations de banco de dados, testes automatizados, workflows de CI e documentação separada para decisões de arquitetura.

**Alguns dos problemas em que trabalhei aqui:** estado multiplayer, regras de jogo por turnos, persistência, separação de responsabilidades e organização de uma base de código com um conjunto cada vez maior de funcionalidades.

---

### [Contrapista](https://github.com/luigicollesi/Contrapista)

Um jogo de dedução online em que os jogadores entram em uma sala, recebem um caso com pistas verdadeiras e falsas, discutem o que aconteceu e competem para encontrar a solução correta.

[Jogar Contrapista](https://contrapista.vercel.app)

A aplicação possui autenticação por email e senha, Google e GitHub, salas privadas, matchmaking casual e ranqueado, fases de jogo com tempo determinado e um desafio diário.

Uma parte importante desse projeto é o pipeline de IA responsável pelos casos. A geração e a avaliação das respostas passam pelo OpenRouter, mas eu não queria que o funcionamento do jogo dependesse de um único modelo se comportando perfeitamente. Por isso, o backend consegue trabalhar com múltiplos modelos e chaves de API, colocar temporariamente combinações com falha em cooldown, validar respostas estruturadas localmente e realizar novas tentativas quando determinado provedor não suporta algum parâmetro solicitado.

Também mantenho o acompanhamento de uso das requisições sem armazenar as chaves de API, utilizo filas por sessão para evitar picos de gerações simultâneas dentro do mesmo fluxo e separo as partes estáveis dos prompts do contexto variável para aproveitar melhor o cache de prompts.

A sincronização multiplayer atualmente utiliza polling com o estado do jogo persistido em PostgreSQL, em vez de WebSockets. Essa escolha permitiu manter a infraestrutura mais simples, ao mesmo tempo em que todos os jogadores continuam compartilhando uma única fonte de verdade.

**Este projeto envolve:** autenticação, estado multiplayer, matchmaking, PostgreSQL, orquestração de LLMs, tratamento de falhas e integração com APIs externas.

---

### [Audiolivros](https://github.com/luigicollesi/audiolivros) + [backend](https://github.com/luigicollesi/audiolivros-server)

Uma aplicação multiplataforma de audiolivros que estou desenvolvendo com **React Native e Expo**, conectada a uma API separada construída com NestJS.

No aplicativo, utilizo Expo Router, Redux Toolkit e TanStack Query, além das APIs de áudio e sistema de arquivos do Expo. Uma parte interessante desse desenvolvimento tem sido manter o estado vindo do servidor separado do estado local da aplicação.

O backend é organizado em módulos relacionados a autenticação, usuários, livros, áudio, favoritos, avaliações, resumos e insights. Ele utiliza NestJS com Passport/JWT para autenticação e integra serviços externos como Supabase e Speechify.

Esse projeto traz um conjunto de restrições diferente das aplicações web acima: navegação mobile, reprodução de áudio, cache, estado local e uma API que evolui de forma independente do cliente.

## Tecnologias com que tenho trabalhado

Minha stack atual gira principalmente em torno de:

`TypeScript` · `React` · `Next.js` · `React Native` · `Expo` · `Node.js` · `NestJS` · `PostgreSQL`

Também trabalho com frequência com autenticação e OAuth, APIs REST, gerenciamento de estado, testes automatizados, workflows de CI e APIs de LLMs.

Tenho menos interesse em acumular tecnologias em uma lista e mais em entender onde cada uma delas faz sentido. Muitos dos meus projetos começam como uma ideia que quero testar e, aos poucos, acabam se tornando uma oportunidade para aprender os problemas de engenharia envolvidos em tornar aquela ideia confiável.

## Um pouco sobre como eu desenvolvo

Procuro manter as fronteiras da aplicação explícitas, em vez de deixar frontend, backend e lógica de domínio se misturarem aos poucos. Conforme um projeto cresce, prefiro documentar decisões, manter comportamentos importantes testáveis e deixar o fluxo de dados claro o suficiente para conseguir voltar ao código meses depois sem precisar redescobrir a aplicação inteira.

Também gosto de projetos que trazem restrições reais de produto. Jogos multiplayer têm sido especialmente interessantes nesse sentido: funcionalidades aparentemente simples rapidamente se transformam em questões de concorrência, persistência, responsabilidade sobre o estado, recuperação de falhas e o que o usuário deve enxergar quando alguma coisa dá errado.

Ainda há bastante coisa nesses projetos que continuo evoluindo — e essa é uma das razões pelas quais mantenho esses repositórios públicos.
