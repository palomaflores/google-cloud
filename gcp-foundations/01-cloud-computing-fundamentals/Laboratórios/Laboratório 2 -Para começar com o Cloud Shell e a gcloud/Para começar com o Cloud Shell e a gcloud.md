# Laboratório: Para começar com o Cloud Shell e a gcloud

## Objetivo

Aprender a acessar e gerenciar recursos de computação do Google Cloud usando a ferramenta de linha de comando `gcloud` no ambiente do **Cloud Shell**.

  

## Visão Geral

O **Cloud Shell** fornece um terminal baseado em navegador, conectado diretamente à infraestrutura do Google Cloud. Ele vem com:

  

- Um ambiente Debian com persistência de dados (diretório `$HOME`) de 5 GB

- Ferramentas pré-instaladas, incluindo o SDK do Google Cloud (`gcloud`)

- Acesso direto aos recursos do Google Cloud

  

Neste laboratório, você vai:

  

- Usar comandos `gcloud`

- Conectar-se a serviços de computação na nuvem

- Navegar e interagir com o Cloud Shell

  

### Pré-requisitos

- Conhecimento básico de editores de texto em Linux (`vim`, `nano`, `emacs`)

- Conta de estudante ou de laboratório no Google Cloud

  

## Configuração e Requisitos

##### Antes de começar:

- **Leia todas as instruções antes de clicar em "Começar o laboratório"** — o tempo é limitado e não pode ser pausado

- Use **navegação anônima** para evitar conflitos entre contas

- Use **apenas as credenciais fornecidas pelo laboratório** para evitar cobranças inesperadas

  

##### Iniciando o Laboratório

1. Clique em **Começar o laboratório**

  

2. No painel à esquerda, copie:

    - **Nome de usuário (Username)**

    - **Senha (Password)**

  

3. Clique em **Abrir console do Google Cloud** em uma janela anônima

  

4. Faça login com as credenciais fornecidas:

    - Cole o nome de usuário e senha

    - Aceite os termos

    - Ignore configurações de segurança (conta temporária)

  

5. O Console do Google Cloud será aberto

  

## Ativar o Cloud Shell

1. No topo da interface do Console, clique no ícone do **Cloud Shell** ![Cloud Shell Icon](https://cdn.qwiklabs.com/ep8HmqYGdD%2FkUncAAYpV47OYoHwC8%2Bg0WK%2F8sidHquE%3D)

2. Autorize a ferramenta, se solicitado

3. Aguarde a inicialização do terminal

  

Depois de se conectar, você verá que sua conta já está autenticada e que o projeto está configurado com seu **Project_ID**, `PROJECT_ID`. A saída contém uma linha que declara o projeto **PROJECT_ID** para esta sessão:

```

Your Cloud Platform project in this session is set to "PROJECT_ID"

```

  

## Usando o gcloud

1. Verificar  e autorizar conta autenticada:

```

gcloud auth list

```

  

Saída esperada:

```

ACTIVE: *

ACCOUNT: "ACCOUNT"

  

To set the active account, run:

    $ gcloud config set account `ACCOUNT`

```

  

2. Verificar ID do projeto ativo:

```

gcloud config list project

```

  

Saída esperada:

```

[core]

project = "PROJECT_ID"`

```

  

O `gcloud` também suporta **auto-preenchimento com tabulação** e diversas outras opções interativas

  

* [Documentação completa do `gcloud`](https://cloud.google.com/sdk/gcloud)

## Sobre o diretório $HOME

O diretório `$HOME`  armazena arquivos de vários projetos e sessões do Cloud Shell no disco permanente

- O diretório `$HOME` é **persistente entre sessões**, útil para armazenar arquivos de projetos

- Ele é privado e **não acessível por outros usuários**

  

---

  

# 1. Configurar Ambiente Google Cloud

###### Objetivo

- Configurar o ambiente do Cloud Shell,

- Definir regiões e zonas

- Armazenar variáveis de ambiente

- Criar uma instância de máquina virtual (VM) usando o `gcloud`

  

## Regiões e Zonas

- **Região:** Localização geográfica onde os recursos são alocados

- **Zona:** Subdivisão dentro de uma região

  

| Oeste dos EUA | Central dos EUA | Leste dos EUA | Europa Ocidental | Ásia Oriental |
| ------------- | --------------- | ------------- | ---------------- | ------------- |
| us-west1-a    | us-central1-a   | us-east1-b    | europe-west1-b   | asia-east1-a  |
| us-west1-b    | us-central1-b   | us-east1-c    | europe-west1-c   | asia-east1-b  |
| -             | us-central1-c   | us-east1-d    | europe-west1-d   | asia-east1-c  |
| -             | us-central1-f   | -             | -                | -             |


- **Obs:** Recursos como VMs e discos devem estar na mesma zona para funcionar corretamente

- [Documentação oficial: Regiões e Zonas](https://cloud.google.com/compute/docs/regions-zones)

  

## Configurando Região e Zona

- Substitua `REGION` e `ZONE` pelos valores desejados:

```

gcloud config set compute/region REGION

gcloud config set compute/zone ZONE

```

  

- Para verificar as configurações atuais:

```

gcloud config get-value compute/region

gcloud config get-value compute/zone

```

  

## Encontrar informações do projeto

#### Visualmente

- No Console do Google Cloud > Menu > Visão geral do Cloud > Painel

#### Via terminal

```

gcloud config get-value project

gcloud compute project-info describe --project $(gcloud config get-value project)

```

  

Na saída do segundo comando, verifique se há entradas como `google-compute-default-zone` e `google-compute-default-region`

  

## Definir Variáveis de Ambiente

1.  Crie uma variável de ambiente para armazenar o ID do projeto e a zona

```

export PROJECT_ID=$(gcloud config get-value project)

export ZONE=$(gcloud config get-value compute/zone)

```

  

2. Verifique se as variáveis estão definidas corretamente:

```

echo -e "PROJECT ID: $PROJECT_ID\nZONE: $ZONE"

```

  

Se as variáveis tiverem sido definidas corretamente, os comandos "echo" vão gerar o ID do projeto e a zona

  

## Criar uma Máquina Virtual com `gcloud`

1. Crie uma instância de VM chamada `gcelab2`:

```

gcloud compute instances create gcelab2 --machine-type e2-medium --zone $ZONE

```

  

Saída esperada:

```

Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-04-326fae68bc3d/zones/us-east1-c/instances/gcelab2].

NAME     ZONE           MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP   STATUS

gcelab2  ZONE     e2-medium               10.128.0.2   34.67.152.90  RUNNING

```

  

**Detalhamento do comando:**

- `gcloud compute instances create`: cria a VM

- `--machine-type e2-medium`: define o tipo da VM

- `--zone $ZONE`: define a zona (usando a variável de ambiente)

  

## Acessar Ajuda dos Comandos `gcloud`

1. Ajuda geral:

```

gcloud -h

```

  

2. Ajuda sobre configurações:

```

gcloud config --help

gcloud help config

```

Para sair, digite `Q` e pressione **Enter**

  

Os resultados dos comandos `gcloud config --help` e `gcloud help config` são equivalentes. Ambos retornam uma ajuda longa e detalhada.

  

Há [flags globais](https://cloud.google.com/sdk/gcloud/reference/) na `gcloud` que controlam o comportamento dos comandos por invocação

  

3. Listar configurações e componentes:

```

gcloud config list

gcloud config list --all

gcloud components list

```

  

----

  

# 2. Filtragem da Saída da Linha de Comando no Google Cloud

A CLI `gcloud` é uma ferramenta poderosa para trabalhar na linha de comando. Talvez você queira que informações específicas sejam exibidas

  

1. Listar todas as instâncias de VM do projeto:

```

gcloud compute instances list

```

  

**Exemplo de saída**:

```

NAME     ZONE         MACHINE_TYPE  PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP     STATUS

gcelab2  us-east1-c   e2-medium     -            10.142.0.2   35.237.43.111   RUNNING

```

  

2.  Listar a máquina virtual gcelab2:

```

gcloud compute instances list --filter="name=('gcelab2')"

```

  

**Exemplo de saída**:

```

NAME     ZONE         MACHINE_TYPE  PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP     STATUS

gcelab2  us-east1-c   e2-medium     -            10.142.0.2   35.237.43.111   RUNNING

```

O parâmetro `--filter` permite aplicar critérios específicos, como nomes, zonas, tipos de máquina, etc

  

3. Listar as regras de firewall do projeto:

```

gcloud compute firewall-rules list

```

  

**Exemplo de saída**:

```

NAME                         NETWORK      DIRECTION  PRIORITY  ALLOW                         DENY  DISABLED

default-allow-icmp           default      INGRESS    65534     icmp                                False

default-allow-internal       default      INGRESS    65534     tcp:0-65535,udp:0-65535,icmp        False

default-allow-rdp            default      INGRESS    65534     tcp:3389                            False

default-allow-ssh            default      INGRESS    65534     tcp:22                              False

dev-net-allow-ssh            dev-network  INGRESS    1000      tcp:22                              False

serverless-to-vpc-connector  dev-network  INGRESS    1000      icmp,udp:665-666,tcp:667            False

vpc-connector-egress         dev-network  INGRESS    1000      icmp,udp,tcp                        False

vpc-connector-health-check   dev-network  INGRESS    1000      tcp:667                             False

vpc-connector-to-serverless  dev-network  EGRESS     1000      icmp,udp:665-666,tcp:667            False

```

  

4. Listar as regras de firewall da rede padrão:

```

gcloud compute firewall-rules list --filter="network='default'"

```

  

**Exemplo de saída**:

```

NAME                  NETWORK  DIRECTION  PRIORITY  ALLOW                         DENY  DISABLED

default-allow-icmp    default  INGRESS    65534     icmp                                False

default-allow-internal default INGRESS    65534     tcp:0-65535,udp:0-65535,icmp        False

default-allow-rdp     default  INGRESS    65534     tcp:3389                            False

default-allow-ssh     default  INGRESS    65534     tcp:22                              False

```

  

5. Listar as regras de firewall da rede padrão em que a regra de permissão corresponde a uma regra ICMP:

```

gcloud compute firewall-rules list --filter="NETWORK:'default' AND ALLOW:'icmp'"

```

  

**Exemplo de saída**:

```

NAME                  NETWORK  DIRECTION  PRIORITY  ALLOW                         DENY  DISABLED

default-allow-icmp    default  INGRESS    65534     icmp                                False

default-allow-internal default INGRESS    65534     tcp:0-65535,udp:0-65535,icmp        False

```

  

---

  

# 3. Conexão com a Instância de VM

Nesta etapa, você aprenderá como se conectar a uma instância de máquina virtual (VM) usando o comando `gcloud compute ssh`, além de instalar um servidor web dentro da VM

  

1. Conectar-se à VM via SSH:

    - Para iniciar uma sessão SSH com a instância chamada `gcelab2`, execute o seguinte comando no Cloud Shell:

```

gcloud compute ssh gcelab2 --zone $ZONE

```

  

**Possível saída inicial** (quando ainda não existem chaves SSH configuradas):

```

WARNING: The public SSH key file for gcloud does not exist.

WARNING: The private SSH key file for gcloud does not exist.

WARNING: You do not have an SSH key for gcloud.

WARNING: [/usr/bin/ssh-keygen] will be executed to generate a key.

This tool needs to create the directory [/home/usuário/.ssh] before being able to generate SSH Keys.

  

Do you want to continue? (Y/n)

```

Obs: Para continuar, digite **Y**

  

2. Gerar par de chaves SSH:

    - Após confirmar com `Y`, o terminal solicitará a criação de uma senha para proteger sua chave SSH:

```

Generating public/private rsa key pair.

Enter passphrase (empty for no passphrase):

Enter same passphrase again:

```

Obs: Pressione **Enter** duas vezes para deixar a senha em branco

  

3. Sessão SSH iniciada:

    - Depois da autenticação, você verá o prompt de comando da VM, semelhante

```

sa_107021519685252337470@gcelab2:~$

```

**sa_1070215...** → representa a conta de serviço usada na conexão  

**gcelab2** → é o nome da instância da VM em que você está logado

  

4. Instalar o servidor web NGINX:

    - Com a conexão estabelecida, execute o seguinte comando para instalar o NGINX na instância:

```

sudo apt install -y nginx

```

O `-y` confirma automaticamente a instalação

O NGINX será baixado e instalado, pronto para servir páginas web

  

5. Encerrar a sessão SSH:

    - Após a instalação, saia da instância e volte ao terminal local do Cloud Shell com o comando:

```

exit

```

  

Você retornará ao prompt padrão do projeto:

```

username@cloudshell:~$

```

  

---

  

# 4. Atualização do Firewall

Nesta etapa, você aprenderá a configurar regras de firewall para permitir o tráfego HTTP externo para sua instância de máquina virtual (VM) que está executando o servidor web **NGINX**

  

1. Verificar regras de firewall existentes:

    - Para listar todas as regras de firewall do projeto, execute:

```

gcloud compute firewall-rules list

```

  

**Exemplo de saída**:

```

NAME                         NETWORK      DIRECTION  PRIORITY  ALLOW                         DENY  DISABLED

default-allow-icmp           default      INGRESS    65534     icmp                                False

default-allow-internal       default      INGRESS    65534     tcp:0-65535,udp:0-65535,icmp        False

default-allow-rdp            default      INGRESS    65534     tcp:3389                            False

default-allow-ssh            default      INGRESS    65534     tcp:22                              False

...

```

A VM `gcelab2` está localizada na rede `default`, mas **não há regra permitindo tráfego HTTP (porta 80)**

  

2. Testar o acesso ao servidor NGINX:

    - Tente acessar o serviço NGINX da sua VM usando o IP externo:

```

curl http://$(gcloud compute instances list --filter=name:gcelab2 --format='value(EXTERNAL_IP)')

```

**Resultado esperado**: falha na conexão, pois não há regra de firewall liberando a porta TCP 80

  

3. Adicionar tags à VM `gcelab2`:

    - Para que a regra de firewall se aplique apenas a esta VM, adicione tags de destino com:

```

gcloud compute instances add-tags gcelab2 --tags http-server,https-server

```

As tags `http-server` e `https-server` servirão como identificadores para aplicar as regras específicas a essa instância

  

4. Criar regra de firewall para permitir tráfego HTTP

    - Agora, crie uma nova regra para liberar o tráfego de entrada na porta 80:

```

gcloud compute firewall-rules create default-allow-http \

  --direction=INGRESS \

  --priority=1000 \

  --network=default \

  --action=ALLOW \

  --rules=tcp:80 \

  --source-ranges=0.0.0.0/0 \

  --target-tags=http-server

```

Essa regra permite que qualquer IP (0.0.0.0/0) acesse a porta 80 de instâncias com a tag `http-server`

  

5. Validar a regra de firewall criada:

    - Execute o comando abaixo para verificar se a nova regra foi aplicada com sucesso:

```

gcloud compute firewall-rules list --filter=ALLOW:'80'

```

  

**Saída esperada**:

```

NAME                NETWORK  DIRECTION  PRIORITY  ALLOW   DENY  DISABLED

default-allow-http  default  INGRESS    1000      tcp:80        False

```

  

6. Verificar o acesso ao servidor NGINX:

```

curl http://$(gcloud compute instances list --filter=name:gcelab2 --format='value(EXTERNAL_IP)')

```

**Resultado esperado**: resposta padrão do NGINX, indicando que o serviço está acessível via HTTP

  

---

  

# 5. Exibição dos Registros do Sistema

Nesta etapa, você aprenderá a utilizar o **Cloud Logging** via CLI `gcloud` para visualizar registros que ajudam a entender o funcionamento da infraestrutura do seu projeto, principalmente das instâncias de máquina virtual

  

1. Listar todos os registros disponíveis no projeto:

    - Execute o seguinte comando para ver os registros gerados pelos diversos serviços do Google Cloud em seu projeto:

```

gcloud logging logs list

```

  

**Exemplo de saída**:

```

NAME: projects/qwiklabs-gcp-01-xxxx/logs/GCEGuestAgent

NAME: projects/qwiklabs-gcp-01-xxxx/logs/OSConfigAgent

NAME: projects/qwiklabs-gcp-01-xxxx/logs/cloudaudit.googleapis.com%2Factivity

...

```

  

Esses nomes indicam fontes específicas de logs, como agentes do sistema (GuestAgent, OSConfigAgent), auditoria (Cloud Audit), e execução de aplicações (stdout/stderr)

  

2. Filtrar registros relacionados a recursos de computação:

    - Para visualizar apenas os registros relacionados ao serviço Compute Engine

```

gcloud logging logs list --filter="compute"

```

  

**Exemplo de saída**:

```

NAME: projects/qwiklabs-gcp-01-xxxx/logs/compute.googleapis.com%2Fautoscaler

NAME: projects/qwiklabs-gcp-01-xxxx/logs/compute.googleapis.com%2Finstance_group_manager_events

NAME: projects/qwiklabs-gcp-01-xxxx/logs/compute.googleapis.com%2Fshielded_vm_integrity

```

  

Esses logs ajudam a monitorar recursos como balanceadores de carga, escaladores automáticos e a integridade de VMs protegidas

  

3. Visualizar registros do tipo de recurso `gce_instance`:

    - Esse comando retorna registros gerados por qualquer instância de VM do Compute Engine

```

gcloud logging read "resource.type=gce_instance" --limit 5

```

  

O parâmetro `--limit` é usado para retornar apenas os 5 registros mais recentes

  

4. Visualizar registros de uma VM específica (`gcelab2`):

    - Para filtrar registros de uma única instância, use o filtro com o nome da instância

```

gcloud logging read "resource.type=gce_instance AND labels.instance_name='gcelab2'" --limit 5

```

  

Isso permite isolar logs de uma VM específica, facilitando o diagnóstico de problemas ou a verificação de atividades recentes

  

---

  

# 6. Teste de Conhecimentos

- Três maneiras básicas de interagir com os serviços e recursos do Google Cloud são:

- [ ] GLib

- [x] Client libraries

- [x] Cloud Console

- [x] Command-line interface

- [ ] GStreamer

  

### Saiba mais

-  [Documentação do Cloud Shell](https://cloud.google.com/shell/docs/)

-  [Using Google Cloud Shell (YouTube)](https://www.youtube.com/watch?v=hBMcAKzGt3w)

-  [Documentação da gcloud](https://cloud.google.com/sdk/gcloud/)

- [Getting Help with gcloud (YouTube)](https://www.youtube.com/watch?v=oTIK9OvQBxQ)

  

### Laboratórios Relacionados

- [Provisionar serviços com o Google Cloud Marketplace](https://google.qwiklabs.com/catalog_lab/339)

- [Como criar um disco permanente](https://google.qwiklabs.com/catalog_lab/559)

- [Como configurar redes usando a gcloud](https://google.qwiklabs.com/catalog_lab/2047)