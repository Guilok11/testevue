# Projeto "Faça seu lanche" - Documentação

## Descrição do Projeto
---
O projeto "Faça seu lanche" é uma aplicação web que permite aos usuários montarem seus próprios lanches personalizados. O Cliente na Home da página, irá informar o seu nome e em seguida ele terá a opção de escolher entre 4 opções de pães, o cliente também terá a opção de escolher entre 4 tipos de carnes e por fim o cliente poderá escolher 4 opções de opcionais para seu lanche. É obrigatório a inserção do nome do cliente, assim como escolha do pão, carne e pelo menos 1 ingrediente opcional. Após a escolha do seu lanche o usuário a clicar no botão de “Criar meu lanche!” que fará com que o lanche montado pelo cliente seja armazenado no sistema.

Já na parte da gerência dos pedidos, que é referente a página dos pedidos, é possível visualizar todos os pedidos realizados, sendo possível visualizar a ordem/número do pedido, o nome do cliente, o tipo do pão escolhido, o tipo da carne, os opcionais e o status atual do pedido. É possível a realização da alteração do status do pedido assim como também é possível cancelar um pedido a qualquer momento.
Por fim, é possível voltar para home clicando no logo da página ou clicando no botão Home.

---

## Como executar
---
1. Verifique se o Node.js e o Vue.js estão instalados em seu sistema.
2. Clone o repositório do projeto.
3. Navegue até o diretório do projeto e execute o comando `npm install` para instalar as dependências.
4. Em um terminal aberto no diretorio raiz do projeto execute o comando `npm run backend` para iniciar a API.
5. Em um outro terminal, também aberto no diretorio raiz do projeto execute o comando `npm run serve` para iniciar o servidor de desenvolvimento.
6. Acesse a aplicação no navegador através do endereço http://localhost:8080.

---


## Componentes

---
O projeto é composto por vários componentes Vue.js, que são:
1. `Banner.vue`:
   Este componente é responsável por exibir o banner principal da aplicação, que contém um título "Faça seu lanche" e uma imagem   de fundo de um hambúrguer.
   
3. `BurgerForm.vue`:
   O componente BurgerForm é responsável por renderizar o formulário de criação de lanches personalizados. Ele possui campos para inserir o nome do cliente, selecionar o tipo de pão, escolher a carne do lanche e selecionar os opcionais desejados. Após preencher o formulário, o usuário pode enviar o pedido, e o lanche é registrado no sistema.
   
4. `Dashboard.vue`:
   O componente Dashboard é responsável por exibir os pedidos de lanches já realizados e seus respectivos status. Neste componente, é possível visualizar os pedidos, atualizar o status e também cancelar um pedido.
   
5. `Footer.vue`:
   O componente Footer é responsável por renderizar o rodapé da aplicação, exibindo o texto "Faça seu lanche © 2023".

6. `Message.vue`:
   Este componente é genérico Message, utilizado para exibir mensagens temporárias na aplicação. Ele recebe uma mensagem como prop e a exibe em um balão na tela. É utilizado para exibir mensagens de sucesso ou erro após realizar alguma ação.
   
8. `Navbar.vue`:
   O componente Navbar é responsável por renderizar a barra de navegação no topo da página. Ele contém o logotipo da aplicação e os links para as páginas "Home" e "Pedidos".
9. `HomeView.vue`:
   Este é o componente da página inicial da aplicação. Ele inclui o componente Banner e o BurgerForm. O Banner é responsável por exibir o título principal da aplicação, enquanto o BurgerForm é responsável por renderizar o formulário de criação de lanches personalizados.
11. `Pedidos.vue`:
    Este é o componente da página de gerenciamento de pedidos. Ele inclui o componente Dashboard, que exibe os pedidos de lanches já realizados e permite a atualização de seus status.
---

## Roteamento
---
No arquivo index.js localizado na pasta routers, são definidas as rotas da aplicação usando o Vue Router:

- Rota padrão '/': Aponta para o componente HomeView.
- Rota 'pedidos': Aponta para o componente Pedidos.

---

## Conclusão
---

Com os componentes HomeView e Pedidos, a aplicação está estruturada para exibir as páginas inicial e de gerenciamento de pedidos. Cada página possui seus próprios componentes, que facilitam a manutenção e reutilização do código. O roteamento implementado permite que o usuário navegue facilmente entre as páginas e interaja com a aplicação de forma intuitiva. Com isso, o projeto "Faça seu lanche" proporciona uma experiência interativa para que os usuários possam criar e gerenciar seus pedidos de lanches personalizados.

---

