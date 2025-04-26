# Laboratório - Introdução ao Console do Google Cloud

Este laboratório apresenta a plataforma Qwiklabs, seus principais recursos, e ensina a acessar o console do Google Cloud com credenciais temporárias.
- **Nível:** Introdutório
- **Atualizado em:** 07/01/2025
- [Acesse a página do laboratório](https://www.cloudskillsboost.google)

### Objetivos

Durante este laboratório, você aprenderá a:

- Acessar o console do Google Cloud com credenciais específicas para uso temporário.

- Explorar o ambiente de laboratório da Qwiklabs e seus principais recursos.

- Identificar diferentes projetos no Google Cloud.

- Navegar pelos serviços usando o menu do Console.

- Verificar e modificar papéis de acesso (IAM).

- Ativar APIs utilizando a biblioteca do console.

  

# 1. Acessar o Console do Google Cloud

1. **Iniciar o laboratório

2. **Abrir console do Google Cloud**

    - Clicar em "Abrir console do Google Cloud" > "Usar outra conta" > Usar credenciais temporárias > Próximo

3. Aceitar os **Termos de Serviço** e acessar o painel inicial do Cloud

  

Obs: O usuário  `estudante-xx-xxxxxx@qwiklabs.net` é uma conta google criada para o usuário usar como estudante. Ele tem o nome de domínio `qwiklabs.net` e papéis do IAM que permitem acessar o projeto do Google Cloud

  

### Usuário e senha

São as credenciais que identificam o usuário no serviço **Cloud Identify and Acess Management (Cloud IAM)**, ela tem permissões que dão acesso aos recursos do Google Cloud no projeto alocado.

Obs: Para realizar os laboratórios as credenciais são temporárias e só funcionam durante a realização do laboratório

  

### ID do projeto

Os projetos do Google Cloud têm configurações e permissões que especificam regras de segurança e quem tem acesso a quais recursos. O ID do projeto é um identificador usado para vincular recursos do Google Cloud a um projeto. Eles são únicos no Google Cloud, podendo ser globalmente identificados

  

# 2. Explorar Projetos do Google Cloud

### Ver todos os projetos

Este laboratório tem acesso a mais de um projeto do Google Cloud. Em alguns laboratórios é possível receber mais de um projeto para concluir as tarefas atribuídas

  

1. Verificar o projeto atribuído e seu identificador (nome, número e ID):

2. Visualizar outros projetos disponíveis:

    - Console do Google Cloud > Menu suspenso

    - Selecionar um projeto > Todos

    - Irá exibir uma lista com o projeto "Qwiklabs Resources"

  

### Menu de navegação e serviços

1. Menu de navegação > Conferir todos os produtos

    - Navegar pelos serviços do Google Cloud por categoria

Consulte a [página de visão geral dos produtos do Google Cloud](https://cloud.google.com/products/?hl=en#top_of_page) para conferir a documentação de cada uma dessas categorias com mais detalhes

  

# 3. Analisar e Modificar Papéis IAM

### Conferir  papéis e permissões

1. Menu de navegação > **IAM e Admin > IAM**

    - Será aberta a página que contém uma lista de usuários, permissões e papéis concedidos a contas específicas

    - Encontrar o usuário "@qwiklabs"

2. Verificar o papel atribuído à conta do estudante (ex: `Editor`)

3. Atribuir o papel de `Leitor` a outro usuário (`User 2`)

  

![Lista de contas com seu nome de usuário em destaque](https://cdn.qwiklabs.com/VpeV7knPXEDf39QBcfOJuAZpDB7zPgjzMSFmmCy2avk%3D)

  

- Explicação:

    - Principal - Mostra e-mail correspondente ao nome de usuário no login

    - Nome - Mostra usuário

    - Papel - Mostra os papéis concedidos oferecidos pelo Google Cloud, eles definem as permissões para os envolvidos no projeto e controlam o acesso e gerenciamento de todos os serviços do Google Cloud

| Papel        | Permissões                                    |
| ------------ | --------------------------------------------- |
| Leitor       | Apenas leitura                                |
| Editor       | Leitura e modificação                         |
| Proprietário | Editor + controle de permissões e faturamento |


Obs: Como editor, você pode criar, modificar e excluir recursos do Google Cloud. No entanto, não é possível adicionar ou excluir membros de projetos do Google Cloud.

  

###  Conceder um papel do IAM

1. Conceder ao principal o papel de `leitor` no projeto:

    - Menu de navegação > IAM e Admin > IAM

    - Selecionar "Conceder acesso"

    - Na sessão 'Adicionar principais' > Inserir identificador `User 2` para principal

    - Em Selecionar um papel > Atribuir papéis > Selecionar `Leitor` > Salvar

    - Verificar se o principal e o papel correspondente estão listados na página IAM

  

# 4. Ativar APIs e Serviços

As APIs são _interfaces de programação de aplicativo_ que você pode chamar diretamente ou nas bibliotecas de cliente. As APIs do Cloud usam os princípios de criação orientados a recursos, conforme descrito no [Guia de design de APIs](https://cloud.google.com/apis/design/).

A maioria das APIs do Cloud apresenta informações detalhadas sobre o uso de determinada API no seu projeto, inclusive níveis de tráfego, taxas de erros e até latências. Assim você identifica rapidamente os problemas com os aplicativos que usam os serviços do Google.

  

1. Menu de navegação > APIs e serviços > Biblioteca

    - Em Categoria são exibidas as diferentes categorias disponíveis

2. Barra de pesquisa > Buscar e ativar  "Dialogflow"

3. Confirmar que a API foi ativada e explorar sua documentação

4. Clique em Testar esta API

    - O navegador vai abrir uma nova guia com a documentação da API Dialogflow

5. Menu de navegação . Visão Geral do Cloud

  

![Bloco de Dialogflow com a API habilitada em destaque](https://cdn.qwiklabs.com/eTgnbsNvLaqrex7qumvUuzQEc114GwncM%2FV8xL4j594%3D)

  

#### Para saber mais sobre as APIs

-  [Diretório de APIs Explorer do Google](https://developers.google.com/apis-explorer/#p/)

- O laboratório [APIs Explorer: Qwik Start](https://google.qwiklabs.com/catalog_lab/1241) também traz experiência prática com a ferramenta, usando exemplos simples, como níveis de tráfego, taxas de erro e até latências

  

## Observações

- As credenciais e projetos são **temporários** e expiram ao fim do tempo do laboratório

- O botão **Verificar meu progresso** permite monitorar o cumprimento das tarefas

- Ao fim, a API Dialogflow deve estar ativada e um papel IAM deve ter sido atribuído corretamente

  

## Recursos adicionais

- [IAM no Google Cloud](https://cloud.google.com/iam/)

- [Guia de Design de APIs](https://cloud.google.com/apis/design/)

- [Visão geral dos produtos Google Cloud](https://cloud.google.com/products)

- [Qwiklabs APIs Explorer: Qwik Start](https://google.qwiklabs.com/catalog_lab/1241)

  

# Conclusão

  

Este laboratório introduz os conceitos fundamentais da plataforma Google Cloud. Ao concluir, você será capaz de navegar no console, entender como os projetos são estruturados, e manipular permissões básicas com o IAM