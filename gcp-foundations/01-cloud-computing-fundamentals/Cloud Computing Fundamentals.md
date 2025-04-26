# 1. Computação em nuvem

A computação em nuvem é uma forma de usar a tecnologia com 5 características importantes:

1. Os clientes acessam recursos sob demanda e por autoatendimento - Com uma interface web os usuários conseguem processamento, armazenamento e rede quando necessário, sem intervenção humana

2. Os clientes acessam os recursos pela Internet, em qualquer lugar com conexão

3. O provedor tem um grande pool de recursos para atender os usuários - O provedor consegue comprar em massa e repassar a economia aos clientes, sem importar a localização física exata dos recursos.

4. Os recursos são elásticos, aumentando ou diminuindo quando necessário para flexibilidade do cliente - Permite que o cliente amplie ou reduza a escala quando necessário

5. Os clientes pagam apenas o que usam ou reservam

  

### Infraestrutura

A infraestrutura é o framework BÁSICO das instalações e sistemas. Tudo o que envolve a criação e suporte desses serviços faz parte da infraestrutura.

  

- ANALOGIA: Infraestrutura X Cidade

Cidade: Possui transporte, comunicação, eletricidade, água, combustível e outros...

Infraestrutura: As pessoas da cidade são os usuários e os carros, bicicletas e prédios são os aplicativos.

  

### Arquitetura da Nuvem X Arquitetura Tradicional

- 1º Onda - Colocation

Os usuários tinham a eficiência financeira de alugar espaços físicos ao invés de investir em data centers

  

- 2º Onda - Data Centers

Os data centers virtualizados de hoje são semelhantes aos data centers particulares e às instalações de colocation do passado. Seus componentes correspondem aos elementos físicos da computação hospedada: servidores, CPUs, discos, balanceadores de carga, etc. Porém, agora virtualizados

  

Obs: Com a virtualização, as empresas ainda mantinham a infraestrutura e o ambiente ainda era controlado e configurado pelos usuários

  

- 3º Onda - Contêineres

Há alguns anos o Google percebeu que não conseguiria se expandir o suficiente devido aos limites do modelo de virtualização, então adotaram uma arquitetura baseada em contêineres. Uma novem elástica e automatizada que consiste na união de dados escalonáveis e serviços automatizados

Os serviços provisionam e configuram automaticamente a infraestrutura usada para executar aplicativos.

  

- Os data centers do Google foram os primeiros a conseguir certificação IS 14001, norma que estabelece um framework para aumentar a eficiência dos recursos e diminuir desperdícios.

  

### IaaS, PaaS e SaaS

Com os data centers virtualizados, os clientes agora possuem 2 novas formas:

1. IaaS (Infraestrutura de serviço)

- Oferece recursos brutos de computação, armazenamento e rede, organizados virtualmente em recursos semelhantes a data centers físicos

- Os clientes pagam pelos recursos alocados antecipadamente

  

2. PaaS (Plataforma de serviço)

- Vincula código a bibliotecas que dão infraestrutura aos aplicativos

- Os clientes pagam pelos recursos que são usados

  

Com a evolução da computação em nuvem o foco passou a ser a infraestrutura e os serviços gerenciados. Com os recursos e serviços gerenciados, as empresas se concentram nas metas de negócios e gastam manos tempo e dinheiro para criar e manter a infraestrutura técnica. Atendendo com mais rapidez e confiabilidade.

  

- MODELO SEM SERVIDOR

Com a computação sem servidor os desenvolvedores se concentram no código ao invés da configuração do servidor, sem precisar gerenciar a infraestrutura.

Ex:

1. Cloud Functions - Gerencia código acionado por eventos com pagamento de utilização

2. Cloud Run - Ambiente gerenciado para implantar aplicativos baseados em microsserviços conteinerizados

  

3. SaaS (Software em serviço)

Os aplicativos Saas não são instalados nos computadores, eles rodam na nuvem como serviço e são consumidos pelos usuários na Internet.

Ex: Gmail, Documentos e Drive

  

### Arquitetura Google Cloud

A infraestrutura do Google Cloud possui 3 CAMADAS:

- 1º CAMADA - Rede e Segurança (Dão suporte a toda a infraestrutura e aos aplicativos do Google )

- 2º CAMADA - Computação e Armazenamento (O Google desacopla para que eles possam ser usados de maneira independente)

- 3º CAMADA - Big Data e Machine Learning (Permite executar tarefas para ingerir, armazenar, processar e entregar insights de negócios, pipelines de dados e modelos de machine learning)

  

Graças ao Google Cloud não é preciso gerenciar e escalonar a infraestrutura para realizar essas tarefas. Além de que essa capacidade será cada vez mais necessária para as organizações.

  

##### Serviços de computação

- Compute Engine

- Google Kubernetes Engine

- App Egine

- Cloud Functions

- Cloud Run

  

##### Opções de armazenamento gerenciado

- Cloud Storage

- Cloud SQL

- Cloud Bigtable

- Firestone

  

Obs: O Cloud SQL e o Cloud Spanner são bancos de dados relacionais, já o Bigtable e o Firestore são bancos de dados NoSQL

  

##### Produtos Big Data e ML

- Cloud Storage

- Dataproc

- Bigtable

- Bigtable

- BigQuery

- Dataflow

- Firestone

- Pub/Sub

- Looker

- Clou Spanner

- AutoML

- Vertex AI (Plataforma de machine learning unificada)

  

A rede do Google faz parte da base que apoia toda a infraestrutura e os aplicativos da empresa, e a maior da categoria, foi projetada para oferecer aos clientes maior capacidade de processamento e menor latência possível para seus aplicativos, usando mais de 100 nós em todo o mundo, onde o conteúdo de alta demanda é armazenado em cache para responder a solicitações de usuários no local com menor tempo de resposta

Possui 5 localizações geográficas base: América do Norte, América do Sul, Europa, Ásia e Austrália

Cada localização é dividida em regiões e zonas diferentes, as regiões são as áreas geográficas independentes e são compostas pelas zonas. Já as zonas são as áreas onde os recursos do Google Cloud são implantados.

Ex: Londres (europe-west2) é uma região que abrange 3 zonas diferentes.

  

Ex2: Supondo que eu iniciei uma VM usando Compute Engine na zona que eu especifiquei para garantir a redundância de recursos, os recursos zonais operam em uma única zona, então se ela ficar indisponível, eles também ficarão.

  

Porque tantas regiões?

Ter vários locais de serviço permite escolher a localização dos aplicativos, alterando propriedades como disponibilidade, durabilidade e latência, que mede o tempo um pacote de informações leva para percorrer da origem até o destino

  

- O Cloud permite especificar localizações geográficas para executar serviços e recursos. Além da localização do nível da zona, região e multirregião. Isso é útil pois aproxima os aplicativos dos usuários de todo o mundo para proteção caso haja algum problema na região inteira, como um desastre natural

- Alguns serviços permitem usar recursos em uma multirregião. As configurações multirregionais permitem replicar dados do banco em várias zonas de diferentes regiões, como definido pela configuração da instância. Essas outras réplicas permitem que eu leia os dados com baixa latência de vários locais próximos/dentro da região na configuração, como Bélgica e Países Baixos.

- Google tem 103 zonas em 34 países

---

# 2. Console, Cloud Shell e APIs

### [Console do Cloud](console.cloud.google.com)

- Há 4 formas de interagir com o Google Cloud: console; SDK Cloud e Cloud Shell; APIs e aplicativo móvel em nuvem

- O console é a interface gráfica do usuário (GUI) do Google Cloud, ele é uma interface da web para implantação, escalonamento e solução de problemas. Com ele é fácil encontrar recursos, verificar status e ter controle total sobre eles e definir orçamentos para controle de gasto.

- O console também possui pesquisa para encontra rapidamente os recursos e se conectar a instâncias no navegador pelo protocolo Secure Shell (SSH)

  

### Noções básicas de projetos

O console é usado para acessar e usar recursos, que são organizados em projetos. O Google Cloud possui uma hierarquia de recursos com 4 níveis:

1. Recursos - Máquinas virtuais, buckets do Cloud Storage, tabelas do BigQuery ou qualquer outra coisa no Google Cloud

2. Projetos - Os recursos são organizados em projetos, são a base dos serviços de Cloud, como: gerenciar APIs, ativar cobranças, adicionar/remover colaboradores e ativar outros serviços do Google

        Cada projeto é um compartimento separado, onde cada recurso pertence somente a 1 projeto.

        Os projetos podem ter usuários diferentes pois a cobrança e o gerenciamento são separados

        Os projetos do Google Cloud possuem 3 atributos de identificação: ID, nome e número

            - ID: identificador exclusivo atribuído pelo Google (não pode ser alterado), imutável e usado para informar ao Google Cloud em qual projeto trabalhar

            - Nomes: São criados pelos usuários, não são imutáveis (podem ser criados e alterados pelos usuários)

            - Número: É um número exclusivo criado pelo Google Cloud para cada projeto. São usados pelo Google Cloud para controlar os recursos

3. Pastas - Organizam os projetos da organização em hierarquia.

    Ex: Uma organização possui vários departamentos com recursos próprios do Google Cloud, com as pastas eu consigo agrupar esses recursos por departamentos. As equipes podem delegar a administração para trabalhar de forma independente.

4. Nó organizacional - Inclui todos os projetos, pastas e recursos da organização

  

###### Como gerenciar projetos?

O Resource Manager do Google Cloud permite fazer isso programaticamente, ela é uma API que identifica todos os projetos associados e também cria, altera, exclui e recupera projetos.

  

### Faturamento no Google Cloud

- O faturamento é feito em projetos, ao definir um projeto é associada uma conta de faturamento a ele. Nessa conta são definidos todos os dados de faturamento, incluindo as opções de pagamento

- As contas podem ser associadas a um ou mais projetos, mas os projetos sem conta só podem usar serviços gratuitos do Google Cloud

- A cobrança e fatura automática é realizada a cada mês ou no limite estabelecido

- É possível usar subcontas para separar os faturamentos por projetos, como os clientes que revendem serviços do Google Cloud que usam subcontas para cada cliente

  

###### Como evitar grandes cobranças acidentais?

É possível definir orçamentos em contas de faturamento ou projetos, o orçamento pode ser um limite fixo ou estar vinculado a outra métrica, como porcentagem do gasto do mês anterior. Eu posso criar um alerta emitindo quando o orçamento se aproxima do limite

Ex: Com limite de US$ 20.00e alerta de 90% eu vou receber uma notificação quando a despesa chegar a US$ 18.000

Os alertas geralmente são definidos com 50%, 90% e 100%, podendo ser personalizados

  

- Os relatórios são uma ferramenta visual no console do Google Cloud para monitorar o gasto em projetos ou serviços. O Google Cloud também tem contas que evitam o consumo excessivo devido a erro ou ataque, protegendo os proprietários da conta e a comunicação do Google Cloud

  

Tipos de cotas aplicadas a projetos:

1. Taxa - São zeradas depois de um tempo

Ex: O serviço GKE tem cota de 1.000 chamadas para a API de cada projeto do Google Cloud a cada 100 segundos, após esse tempo ela é zerada

  

2. Alocação - Determinam o número de recursos nos projetos

Ex: Cada projeto do Google Cloud tem uma cota que só permite 5 redes de nuvem privada virtual

  

Os projetos começam com as mesmas cotas, mas podem ser realizadas solicitações de alteração ao suporte do Google Cloud.

  

### Cloud Shell

- Dá acesso aos recursos através da linha de comando em um navegador

- É uma VM como Debian, com diretório principal permanente de 5GB, facilitando a gestão de projetos e autenticadas

- Com o Cloud Shell o comando gcloud do Clous SDK e outras ferramentas são instaladas, disponibilizadas, atualizadas e autenticadas

- Para iniciar o Cloud Shell: Acessar console.cloud.google.com -> Ativação barra de tarefas

- É conveniente para trabalhar com aplicativos com foco em código ou cargas de trabalho de contêineres, porque você edita arquivos sem baixar e carregar mudanças

- Também pode usar editores de texto no prompt de comando do Cloud Shell

  

### APIs Google Cloud

As **APIs** oferecem interfaces bem definidas para interagir com os serviços, ocultando complexidades da implementação, permitindo que o software permaneça estável mesmo com mudanças internas

O **Google Cloud APIs Explorer** ajuda a visualizar as versões disponíveis dessas APIs. Para facilitar o uso das APIs em aplicações, o Google fornece **bibliotecas de cliente** em várias linguagens, como **Java, Python, PHP, C#, Go, Node.js, Ruby e C++**, evitando a necessidade de começar o código do zero

  

### App para dispositivos móveis

O **aplicativo móvel em nuvem**, que permite gerenciar serviços diretamente do celular, sem custo extra

Com ele, é possível>

- Controlar instâncias do **Compute Engine** e **Cloud SQL**

- Acessar via **SSH**

- Administrar aplicativos do **App Engine**

- Monitorar **faturamento**

- Criar **gráficos personalizados** com métricas de uso

- Gerenciar **alertas e incidentes**

  

[cloud.google.com/console-app](https://cloud.google.com/console-app)

  ---

# 3. Criar apps com o google cloud
- Objetivo: Aprender a criar aplicativos diretamente no Google Cloud
- Conteúdo: Opções de computação em nuvem, máquina virtual, escalonamento automático, PaaS com Kubernetes (GKE) e Cloud Run para aplicativos escalonáveis
- Inclui _5 laboratórios_

### Opções de computação na nuvem
O Google Cloud oferece várias opções de computação para diferentes necessidades
- **Compute Engine** - é ideal para cargas de trabalho gerais com recursos dedicados
- **App Engine** - fornece uma solução de plataforma como serviço (PaaS)
- **Cloud Functions** - permite executar código baseado em eventos sem servidor
- **Google Kubernetes Engine (GKE)** - roda contêineres com Kubernetes
- **Cloud Run** - permite implantar aplicativos conteinerizados de forma escalável e sem gerenciar servidores

### Como usar o IaaS com o Compute Engine
- O Compute Engine é a solução de infraestrutura como serviço (IaaS) do Google Cloud, permitindo a criação e execução de máquinas virtuais (VMs) nos data centers globais da empresa, sem necessidade de investimento inicial. As VMs podem ser totalmente configuradas (CPU, memória, armazenamento e sistemas operacionais) e usadas para vários tipos de cargas de trabalho, como hospedagem de servidores web e backends de aplicativos
- As VMs podem ser criadas via Google Cloud Console ou linha de comando (gcloud), com suporte a imagens Linux, Windows e sistemas personalizados. A cobrança é feita por segundo, com descontos automáticos por uso prolongado ou compromisso de uso (até 57%) sobre o preço normal
- Além disso, o Compute Engine oferece VMs preemptivas, ideias para tarefas temporárias como jobs em lote, com economia de até 90%, embora possam ser interrompidas a qualquer momento. A calculadora de preços online pode ser usada para estimular custos e simular diferentes configurações
- A VM preemptiva só tem uma diferença em relação a uma VM normal do Compute Engine:
	- O Compute Engine tem permissão para encerrar um job se precisar dos recursos em outro lugar
	- Nas VMs preemptivas é preciso garantir que o job possa ser interrompido e reiniciado

### Configuração de aplicativos elásticos com escalonamento automático
 O **Compute Engine** permite criar aplicativos elásticos com **escalonamento automático**, ajustando dinamicamente a quantidade de **VMs** com base em métricas de carga. Os usuários podem escolher entre **tipos de máquinas predefinidos ou personalizados**, com diferentes combinações de CPU e memória.

Além do escalonamento, o serviço oferece **balanceamento de carga** integrado via **VPC**, distribuindo o tráfego entre as VMs. Embora seja possível configurar **VMs grandes** para cargas intensas, como bancos de dados em memória ou análises pesadas, a prática comum é usar o **escalonamento horizontal** (aumentar o número de VMs).

O número de CPUs por VM depende da **família de máquinas** e da **cota disponível na zona**

- [cloud.google.com/compute/docs/machine-types](https://cloud.google.com/compute/docs/machine-types)
  
### Como usar o PaaS com o App Engine
O App Engine é uma plataforma gerenciada pela Google Cloud que permite desenvolver e executar aplicativos escaláveis sem a necessidade de gerenciar servidores ou infraestrutura. Ela é ideal para desenvolvedores que desejam focar apenas no código, com alta disponibilidade e escalonamento automático
##### Recursos
- Suporte a linguagens a populares (Java, Python, Go, PHP, Node.js, Ruby)
- Ferramentas integradas (Eclips, IntelliJ, Maven, Git, Jenkins, etc)
- Serviços integrados (NoSQL, Memcache, balanceamento de carga, verificações de integridade, logs e autenticação)
- SDK local para desenvolvimento, testes e implantação

#### Ambientes disponíveis
1. Padrão
	- Rápido
	- Executa apps em contêineres e com restrição à sandbox
	- Suporte limitado a infraestrutura (sem SSH ou disco local)
	- Cobrança por uso com desligamento automático
	- Ideal para apps que rodam bem com configurações pré-definidas

2. Flexível
	- Lento, mas com acesso a VMs via SSH, uso de Dockerfiles personalizados e instalação de software
	- Suporte a microsserviços, SQL,NoSQL, divisão de tráfego e etc
	- Cobrança por alocação de recursos por hora, sem desligamento automático
	- VMs gerenciadas e atualizadas automaticamente pelo Google

#### Comparação com GKE
- O App Engine padrão é idal p ara quem quer zero gestão da infraestrutura
- O GKE (Google Kubernetes Engine) oferece controle total sobre os contêineres
- O App Engine flexível possui mais flexibilidade que o padrão, mas menos complexidade que o GKE

### Programas voltados para eventos com o Cloud Functions
O Cloud Functions é um serviço severliess e orientado a eventos do Google Cloud, ideal para executar funções de objetivo único em esposta a eventos específicos, como upload de arquivos, mensagens do pub/sub ou chamadas HTTP
##### Principais características
- Executa funções pequenas e independentes sem necessidade de gerenciar servidores
- Responde a eventos assíncronos do Cloud Storage, Pub/Sub e requisições HTTP síncronas
- Ideal para processamento de imagens, lógica ne negócios leve, automações e integração entre serviços
- Cobrança por tempo de execução, em incrementos de 100 ms
- Suporte para JavaScript, Node.js, Python e Go
- Execução em ambiente gerenciado do Google Cloud

### Conteinerizar e orquestrar aplicativos com o GKE
Essa seção aborda o uso de **contêineres** e do **Google Kubernetes Engine (GKE)** para criar, implantar e escalar aplicativos de forma eficiente e flexível

##### **Principais pontos:**
- **Contêineres** são unidades leves que empacotam código e dependências, isolando o app do SO e do hardware. Eles iniciam rapidamente e escalam como processos, mantendo alta portabilidade    
- Comparados a **VMs**, contêineres são menores, mais rápidos e mais econômicos    
- O **Kubernetes** é uma plataforma de código aberto que orquestra e gerencia clusters de contêineres, lidando com escalonamento, balanceamento de carga, atualizações e integridade do sistema    
- O **GKE** é a versão gerenciada do Kubernetes no Google Cloud, permitindo usar contêineres com produtividade, flexibilidade e eficiência aprimorada    
- Ele combina os benefícios da **IaaS** (infraestrutura configurável) com a **PaaS** (escalabilidade automática), ideal para arquiteturas de **microsserviços**   
- O Google executa todos os seus serviços em contêineres, incluindo Gmail e Search, e lança mais de **2 bilhões de contêineres por semana**
- Ferramentas como **Docker** facilitam o empacotamento e o envio de apps em contêineres para qualquer ambiente compatível    

Contêineres + Kubernetes (via GKE) = escalabilidade, portabilidade e gerenciamento eficiente de aplicações modernas em nuvem

### Computação gerenciada sem servidor com o Cloud Run

### Teste
1. Qual serviço de computação seria considerado IaaS?
- [ ] App Engine
- [x] Compute Engine
- [ ] Google Kubernetes Engine
- [ ] Cloud Functions

2. Qual opção a seguir é um ambiente leve de execução sem servidor e totalmente gerenciado para desenvolver e conectar serviços na nuvem?
- [x] Cloud Functions
- [ ] App Engine
- [ ] Google Kubernetes Engine
- [ ] Compute Engine

3. Qual opção a seguir é um ambiente gerenciado para implantar apps conteinerizados?
- [ ] Cloud Functions
- [x] Google Kubernetes Engine
- [ ] Cloud Run
- [ ] App Engine

4. Qual é o recurso do Compute Engine que permite adicionar ou subtrair VMs de um aplicativo com base em métricas de carga?
- [ ] Balanceamento de carga
- [x] Discos permanentes
- [ ] Network Time Protocol (NTP)
- [ ] Escalonamento automático

5. Qual opção a seguir é uma plataforma gerenciada de computação que permite executar contêineres sem estado usando solicitações da Web ou eventos do Pub/Sub?
- [ ] Google Kubernetes Engine
- [x] Cloud Run
- [ ] Cloud Functions
- [ ] App Engine

6. Qual ambiente do App Engine é baseado em instâncias pré-configuradas de contêineres?
- [ ] Os ambientes padrão e flexível
- [ ] Ambiente flexível
- [x] Ambiente padrão