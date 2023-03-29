# Desafio Carefy

- [Repositório Frontend](https://github.com/JordanVScher/desafio-carefy-frontend)
- [Repositório Backend](https://github.com/JordanVScher/desafio-carefy-backend)

Na nuvem:

- [Projeto Frontend](https://desafio-carefy-frontend.onrender.com)
- [Projeto Backend](https://desafio-carefy-backend.onrender.com/)


### Sobre

O desafio foi feito em Node.js (através do framework Nest.js) e em React. 
Os projetos estão rodando no Free Tier do Render.

Para acessar a tela de CRUD de pacientes o usuário deverá fazer login através de sua conta do Github, esse login também é necessário para acessar os endpoints referentes à manipulação dos pacientes. Na tela de CRUD é possível ver, adicionar, editar e deletar pacientes da base de dados.

A parte do frontend se mostrou particularmente desafiadora já que eu nunca havia mexido tanto com React. Por conta das minhas limitações de tempo (eu trabalho e estudo de noite), algumas coisas poderiam ser feitas de outra forma e outras receberam prioridade. Alguns pontos de melhoria são:

### Frontend:

- Um detalhe estranho acontece na versão rodando na nuvem: ao fazer login e ser redirecionado, às vezes é necessário atualizar a página para que os dados apareçam, mesmo que a requisição tenha dado certo. Suspeito que isso aconteça graças ao alto tempo de resposta do tier gratuito do Render. Rodando localmente isso não acontece.
- Me parece que um grande problema aqui é o armazenamento do access_token do Github sendo salvo no LocalStorage.
- Faltam testes unitários, como eu nunca mexi com React antes, creio que eles me tomariam muito tempo, então eles tiveram a menor prioridade de todos os itens.

### Backend:

- Algumas mudanças estruturais para separar melhor cada camada do projeto. Por exemplo: A conexão com o banco é feita com o Mongo através do módulo Mongoose do próprio Nest.js. Ele é chamado diretamente pelo service mas idealmente eu o separaria em um módulo de repositório para facilitar reuso e testagem. Outro exemplo: separar as chamadas à api do Github em outro módulo.
- Faltaram testes unitários. Os que existem são apenas para mostrar uma estrutura base que poderia ser usada para dar seguimento no desenvolvimento de novos testes dentro dos requisitos do framework Nest. Se eu tivesse tido mais tempo, teria desenvolvido os endpoints já com os testes simultaneamente. Primeiro os unitários para validar configuração, chamadas e lógica nas controllers e services para depois adicionar testes de E2E, testando diretamente cada endpoint e seus resultados com, por exemplo, supertest. Nesse caso, seria interessante o uso de uma lib para mockar o banco em memória, como o mongo-memory-server.
- Melhorias no tratamento de erros e de retornos de status HTTP.
- Melhorias no armazenamento (talvez até cacheamento) do access_token para evitar a validação direta no github a cada requisição.

<br>

### Rodar Localmente

<br>

```bash
# Clone o repositório backend: 
git clone https://github.com/JordanVScher/desafio-carefy-backend

# Vá para o diretório:
cd ./desafio-carefy-backend

# Instale os pacotes:
npm i

# Preencha o arquivo .env com suas chaves
- NODE_ENV='dev'
- NODE_PORT='3500'
- MONGO_URL=<YOUR_MONGO_URL>
- GITHUB_OAUTH_CLIENT_ID=<GET_THIS_FROM_YOUR_GITHUB_OAUTH_APP>
- GITHUB_OAUTH_REDIRECT_URI=<GET_THIS_FROM_YOUR_GITHUB_OAUTH_APP>
- GITHUB_OAUTH_CLIENT_SECRET=<GET_THIS_FROM_YOUR_GITHUB_OAUTH_APP>

# Rode o projeto
npm run start

---------

# Clone o repositório frontend: 
git clone https://github.com/JordanVScher/desafio-carefy-frontend

# Vá para o diretório:
cd ./desafio-carefy-frontend

# Instale os pacotes:
npm i

# Preencha o arquivo .env com suas chaves
- REACT_APP_ENV='dev'
- REACT_APP_BACKEND_URL='http://localhost:3500' # aponta para o backend
- REACT_APP_GITHUB_OAUTH_CLIENT_ID=<GET_THIS_FROM_YOUR_GITHUB_OAUTH_APP>

# Rode o projeto
npm run start

```




