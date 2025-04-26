# Laboratório - Criando e Gerenciando Instâncias no Compute Engine
### Visão Geral
Neste laboratório prático, você aprenderá a criar instâncias de máquinas virtuais (VMs) no Google Cloud usando o **Console do Cloud** e a **ferramenta de linha de comando `gcloud`**. Também instalará o servidor web **NGINX** em uma VM e entenderá conceitos fundamentais como **zonas, regiões e tipos de máquina**

### Objetivos do Laboratório
- Criar uma VM usando o Console do Google Cloud
- Criar uma VM usando o terminal via `gcloud` no Cloud Shell
- Instalar e conectar um servidor NGINX a uma VM
- Compreender regiões, zonas e configurações básicas de rede no GCP

### Pré-Requisitos
- Conhecimento básico de editores de texto no Linux: `nano`, `vim`, `emacs`
- Acesso a um navegador
- Conta de estudante fornecida pelo laboratório (não usar conta pessoal)

# Configuração e Requisitos
### Antes de Começar
- Os laboratórios são **cronometrados** e **não podem ser pausados**
- Ao clicar em **"Iniciar laboratório"**, o tempo começa a contar
- Você receberá **credenciais temporárias** para acesso ao ambiente do Google Cloud
- É um ambiente real, não uma simulação

### Requisitos para Realização do Laboratório
- Utilize um **navegador de internet** (recomenda-se o **Google Chrome**)
- **Use uma janela anônima** do navegador para evitar conflitos de contas (estudantil vs. pessoal)
- **Somente use a conta temporária fornecida** pelo laboratório
- Se utilizar outra conta do Google Cloud, você poderá receber **cobranças indevidas**

### Como Iniciar o Laboratório e Acessar o Console
1. Clique em **"Começar o laboratório"**
2. Se for necessário, selecione uma forma de pagamento
3. No painel **Detalhes do Laboratório**, veja:
    - O botão **"Abrir Console do Google Cloud"**
    - **Tempo restante**
    - **Credenciais temporárias** (usuário e senha)
4. Clique com o botão direito no link “Abrir Console” e selecione **abrir em janela anônima**.
5. Na tela de login:
    - Clique em **"Usar outra conta"**
    - Copie o **"Username"** fornecido
    - Clique em **"Próxima"**
    - Cole a **"Password"** fornecida
    - Clique novamente em **"Próxima"**

### Acessando o Google Cloud Console
- Após o login, o Console abrirá automaticamente
- Use o **Menu de Navegação** ou o **campo de pesquisa** para acessar serviços
- Para abrir o terminal, clique em **"Ativar Cloud Shell"** na parte superior

### Usando o Cloud Shell
- O Cloud Shell é uma máquina virtual com:
    - Diretório principal de **5GB**
    - Ferramentas pré-instaladas, como a **gcloud**

- Após ativar:
    - Clique em **“Continuar”**
    - Clique em **“Autorizar”**
    - A conta e o projeto serão automaticamente configurados

#### Comandos úteis
- Ver conta ativa:
```
gcloud auth list
```

- Ver ID do projeto:
```
gcloud config list project
```

### Regiões e Zonas
- Recursos do Compute Engine estão localizados em **regiões** e **zonas**
- Exemplos:
    - `us-central1` (região) → `us-central1-a`, `us-central1-b` (zonas)
- Recursos zonais, como VMs e discos, **devem estar na mesma zona**

#### Configurar região e zona
```
gcloud config set compute/region REGION
export REGION=REGION
export ZONE=ZONE
```
- Obs: No Cloud Shell, **essas variáveis precisam ser redefinidas** a cada nova sessão

![[Pasted image 20250426140524.png]]
# 1. Criar uma instância no Console do Cloud
Nesta etapa do laboratório será criada uma **instância de VM predefinida** usando o **Compute Engine** no Console do Google Cloud

### Acesso ao Compute Engine
1. Em **Console do Google Cloud** > **Menu de navegação** (☰) >  **Compute Engine** > **Instâncias de VM**

### Criando a Instância de VM
1. Clicar em  **“CRIAR INSTÂNCIA”** > Preencha os campos com os dados >  **"Criar"**

| **Campo**                  | **Valor**                                                        | **Detalhes**                                                                     |
| -------------------------- | ---------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Nome**                   | `gcelab`                                                         | Nome da instância                                                                |
| **Região**                 | `<REGION>`                                                       | Ex: `us-central1`, `europe-west1` — verifique a região definida anteriormente    |
| **Zona**                   | `<ZONE>`                                                         | Ex: `us-central1-a` — lembre da zona definida no início                          |
| **Série**                  | `E2`                                                             | Escolha a série de máquinas **E2**                                               |
| **Tipo de máquina**        | 2 vCPUs                                                          | Instância com 2 núcleos de CPU e 4 GB de RAM                                     |
| **Disco de inicialização** | Disco permanente de 10 GB com **Debian GNU/Linux 11 (bullseye)** | Use a imagem Debian padrão                                                       |
| **Firewall**               | Marque **Permitir tráfego HTTP**                                 | Necessário para permitir o acesso à aplicação web que será instalada futuramente |

- Obs: A VM **gcelab** leva cerca de **1 minuto** para ser criada. Após criada, ela vai aparecer  na lista de instâncias de VM
- Se quiser usar **SSH** para conectar à VM, clique em **SSH** à direita do nome da instância `gcelab`. Isso vai abrir o terminal SSH direto no navegador
- [Documentação Oficial](https://cloud.google.com/compute/docs/connect/standard-ssh?hl=pt-br)

![[Pasted image 20250426143435.png]]
![[Pasted image 20250426143450.png]]

# 2. Instalar um Servidor da Web NGINX
Nesta etapa do laboratório será instalado e verificado o funcionamento do servidor web **NGINX** na instância de VM criada anteriormente

1.  Atualizar o Sistema Operacional:
```
sudo apt-get update
```

**Saída esperada:**
```
Get:1 http://security.debian.org stretch/updates InRelease [94.3 kB]
Get:2 http://deb.debian.org stretch-updates InRelease [91.0 kB]
...
```

2. Instalar o NGINX:
```bash
sudo apt-get install -y nginx # Instala o servidor NGINX
```

**Saída esperada:**
```
Reading package lists… Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
...
```

3. Verificar se o NGINX Está em Execução:
```bash
ps auwx | grep nginx # Verifica se o NGINX está rodando
```

**Saída esperada:**
```
root      2330  0.0  0.0 159532  1628 ?        Ss   nginx: master process
www-data  2331  0.0  0.0 159864  3204 ?        S    nginx: worker process
www-data  2332  0.0  0.0 159864  3204 ?        S    nginx: worker process
```

4. Visualizar a Página Web:
	- No Console do Google Cloud, localize a coluna **IP externo** da instância `gcelab`
	- Clique sobre o link ou abra manualmente no navegador:
`
```
http://EXTERNAL_IP/
```

- Resultado esperado: A página padrão do NGINX será exibida com a mensagem **"Welcome to nginx!"**

![[Pasted image 20250426145350.png]]
![[Pasted image 20250426145418.png]]

# 3. Criar uma Nova Instância com a gcloud
Esta etapa vai usar o **CLI gcloud**, disponível no **Cloud Shell**, para criar uma nova instância de VM chamada `gcelab2` diretamente via terminal, sem usar a interface gráfica

1. No **Cloud Shell**, executar o comando:
```bash
gcloud compute instances create gcelab2 --machine-type e2-medium --zone=$ZONE
```

Obs: O valor da variável `$ZONE` deve ter sido definido anteriormente com:
```bash
export ZONE=us-central1-a  # exemplo
```

**Saída esperada (exemplo):**
```
Created [https://www.googleapis.com/compute/v1/projects/.../zones/us-central1-a/instances/gcelab2].
NAME: gcelab2
ZONE: us-central1-a
MACHINE_TYPE: e2-medium
INTERNAL_IP: 10.128.0.3
EXTERNAL_IP: 34.136.51.150
STATUS: RUNNING
```

### Detalhes da Instância Criada
- **Nome:** `gcelab2`
- **Imagem:** Debian GNU/Linux 11 (bullseye)
- **Tipo de máquina:** `e2-medium` (2 vCPUs, 4 GB RAM)
- **Disco:** Disco permanente raiz de 10 GB
- **IP externo:** Atribuído automaticamente

##### Dica: Verificar Padrões da gcloud
```
gcloud compute instances create --help
```
Para sair do modo de ajuda, pressione `Ctrl+C`


### Definir Zona e Região como Padrão
Para evitar repetir as flags `--zone` e `--region`:
```bash
gcloud config set compute/zone ZONE
gcloud config set compute/region REGION
```

Exemplo:
```bash
gcloud config set compute/zone us-central1-a
gcloud config set compute/region us-central1
```

### Verificar Instâncias no Console
1. Menu de Navegação > **Compute Engine > Instâncias de VM**
2. Verificar se a instância `gcelab2` foi criada com sucesso ao lado da `gcelab`

### Conectar-se via SSH com gcloud
```bash
gcloud compute ssh gcelab2 --zone=$ZONE
```
- Digitar `Y` para continuar
- Pressionar **Enter** quando for perguntado por uma senha (deixar em branco)

### Sair da Sessão SSH
```bash
exit
```

![[Pasted image 20250426145649.png]]
![[Pasted image 20250426145814.png]]
![[Pasted image 20250426145926.png]]

#### Pergunta
Por quais das opções a seguir você pode criar uma instância de VM no Compute Engine?
- [x] A ferramenta de linha de comando gcloud
- [x] O Console do Cloud