# Handverse

Plataforma web para o aprendizado de Libras e a comunicação entre pessoas surdas e ouvintes, com vídeo aulas, tradução automática, videochamada em tempo real e um sistema de gamificação.

> Projeto acadêmico (Trabalho de Conclusão de Curso — Ciência da Computação). Este repositório é um fork do projeto original do grupo, mantido aqui por um dos integrantes como parte do portfólio pessoal. Repositório original: [Handverse/Handverse](https://github.com/Handverse/Handverse).

<!-- Se o projeto estiver publicado, troque o link abaixo. Se não estiver mais no ar, remova a linha. -->
🔗 **Demo:** [(https://handverse.netlify.app/)]

---

## Sobre o projeto

No Brasil, cerca de 14,4 milhões de pessoas têm alguma deficiência auditiva, e a maior parte dos ambientes digitais ainda não foi pensada para elas. O Handverse nasceu para reduzir essa barreira: uma plataforma onde qualquer pessoa, com zero conhecimento prévio de Libras, pode aprender os sinais básicos, praticar por chat e videochamada, e se comunicar com a comunidade surda.

O projeto foi validado com pesquisa de campo real — aplicamos um formulário com pessoas surdas, ouvintes interessados em inclusão e estudantes de Libras, e 66% dos entrevistados disseram que usariam a plataforma para comunicação e aprendizado. Esse retorno guiou as funcionalidades priorizadas no desenvolvimento.

## Funcionalidades

- **Cadastro e login seguro** — autenticação via Firebase Authentication, com senhas em hash e tokens JWT.
- **Chat em texto** — comunicação instantânea entre usuários, pensado como porta de entrada para quem está começando a aprender Libras.
- **Videochamada em tempo real** — integração com a API VideoSDK (WebRTC) para conversas por sinais, com foco em qualidade de imagem e estabilidade.
- **Módulo de cursos em vídeo** — seis vídeo aulas gravadas pela própria equipe, do alfabeto a diálogos do dia a dia, hospedadas no YouTube e incorporadas via iframe.
- **Tradução automática** — plugin VLibras (Governo Federal) traduz o conteúdo em português para Libras através de um avatar 3D.
- **Gamificação** — questionário ao final de cada módulo; quem atinge 80% de acerto ganha um cupom de desconto na loja integrada.
- **E-commerce** — loja via NuvemShop, conectada ao sistema de recompensas.

## Tecnologias

| Camada | Tecnologia | Uso |
|---|---|---|
| Front-end | HTML5, CSS3, JavaScript | Estrutura, estilo responsivo (mobile first) e lógica no cliente |
| Backend / dados | Firebase (Realtime Database / Firestore) | Banco NoSQL, sincronização em tempo real |
| Autenticação | Firebase Authentication | Login, sessão e tokens JWT |
| Armazenamento | Firebase Cloud Storage | Imagens e outros ativos |
| Hospedagem | Netlify | Deploy contínuo (CI/CD) a partir do repositório Git |
| Vídeo sob demanda | YouTube | Repositório e streaming dos módulos de curso |
| Videochamada | VideoSDK | Comunicação em tempo real (RTC / WebRTC) |
| Acessibilidade | VLibras | Tradução automática português → Libras |
| E-commerce | NuvemShop | Loja e sistema de recompensas |
| Pesquisa | Google Forms | Coleta de dados com usuários reais |
| Design | Canva | Wireframes, mockups e identidade visual |
| Gestão de projeto | Trello (Kanban) | Organização de tarefas e cronograma |

Optamos por um banco NoSQL em vez de um relacional pela flexibilidade de schema, pelo custo menor de escalabilidade horizontal e pelo desempenho em operações de leitura/escrita em tempo real — sem a rigidez e o custo de manutenção de um banco relacional tradicional para esse volume e esse estágio do projeto.

## Modelagem do banco de dados

O Realtime Database está organizado em três coleções principais:

- **Users** — criada automaticamente pelo Firebase Authentication a cada novo cadastro: e-mail, senha em hash, ID único e data de criação.
- **Questions** — perguntas do quiz de gamificação: enunciado, alternativas, resposta correta e código da questão.
- **QuestionsXUsers** — tabela de relacionamento entre usuário e pergunta: se acertou, quando respondeu, e-mail do usuário e código da questão.

## Minha contribuição

<!-- Substitua pela descrição real e específica do que você fez. Alguns exemplos de como detalhar: -->
Trabalhei em diferentes frentes do sistema, incluindo **[preencher: ex. cadastro/login, tela de videochamada, integração do quiz de gamificação com o banco de dados, pesquisa de campo]**.

## Equipe

Projeto desenvolvido para a disciplina de TCC do curso de Ciência da Computação, sob orientação do Prof. Me. Gregorio Perez Peiro.

- Henrique Nicolae Di Sciascio - [@HenriqueSciascio](https://github.com).
- Lucas Martins da Silva - [@LucHalls](https://github.com).
- Matheus Nicacio de Moura - [@Nickka07](https://github.com).
- Vagner Marques de Souza Lopes - [@DS-Vagner](https://github.com).


## Como executar localmente

O projeto é front-end estático (sem build step), então basta servir os arquivos:

```bash
git clone https://github.com/DS-Vagner/HandVerse.git
cd HandVerse
```

Abra `index.html` com uma extensão de live server (ex: Live Server do VS Code), ou rode um servidor simples:

```bash
npx serve .
```

> As funcionalidades que dependem de backend (login, chat, gamificação) exigem um projeto próprio no Firebase configurado com suas credenciais. As chamadas de vídeo dependem de uma chave de API do VideoSDK.

## Trabalhos futuros

- Reconhecimento de gestos em tempo real por webcam, com IA e modelos de deep learning (a pasta `API WebCam` deste repositório é o início dessa frente).
- Expansão da tradução automática para outras línguas de sinais (ASL, LSF, BSL, LGP).
- Módulo de simulação de entrevistas e processos seletivos em Libras.
- Aplicativo mobile / PWA para tradução em tempo real.

## Contexto acadêmico

Este projeto foi apresentado como Trabalho de Conclusão de Curso. O artigo completo, com fundamentação teórica, metodologia de pesquisa e referências, está disponível [neste repositório](#) <!-- adicione o link ou arquivo do TCC, se quiser publicá-lo -->.
