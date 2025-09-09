# Laboratório 3 - Módulo 3 | Curso AZ-900 (DIO)

Este repositório contém o material prático do *3° laboratório do Módulo 2* do curso *AZ-900* da DIO.

---

## Objetivos do Lab

- Criar uma *Storage Account* para armazenamento de dados na nuvem.  
- Criar uma *Fila (Queue Storage)* para mensageria.  
- Utilizar a ferramenta *AzCopy* para copiar e sincronizar arquivos.  

---

## 1. Criação de uma Storage Account

Uma *Storage Account* no Azure é uma conta que fornece acesso a diversos serviços de armazenamento, como blobs, filas, arquivos e tabelas.  

*Passos realizados:*
1. Acesse o portal do Azure: [https://portal.azure.com](https://portal.azure.com).  
2. Pesquise por *Storage accounts* no menu superior.  
3. Clique em *+ Create* para criar uma nova conta.  
4. Preencha os campos:  
   - *Subscription*: selecione sua assinatura.  
   - *Resource group*: escolha ou crie um grupo de recursos.  
   - *Storage account name*: insira um nome único (minúsculas).  
   - *Region*: selecione a região desejada (ex.: East US).  
   - *Performance*: Standard.  
   - *Redundancy*: LRS.  
5. Clique em *Review + Create* e depois em *Create*.  
6. Aguarde a implantação e acesse a Storage Account criada.

---

## 2. Criação de uma Fila (Queue Storage)

Uma *Queue Storage* permite o envio e recebimento de mensagens de forma confiável, garantindo comunicação assíncrona entre componentes.

*Passos realizados:*
1. Na *Storage Account* criada, acesse a opção *Queues* no menu lateral.  
2. Clique em *+ Queue*.  
3. Defina um nome para a fila (ex.: fila-lab).  
4. Clique em *Create* para finalizar.  

---

## 3. Uso do AzCopy

O *AzCopy* é uma ferramenta de linha de comando usada para copiar dados de/para contas de armazenamento do Azure.

### Instalação
- No *Azure Cloud Shell*, o AzCopy já está instalado.
- Para instalar localmente, siga a documentação: [AzCopy](https://learn.microsoft.com/azure/storage/common/storage-use-azcopy-v10).

### Passos realizados:
1. Gere uma *SAS URL* no container criado na Storage Account.  
2. Execute os comandos no terminal:

```bash
# Upload de arquivos
azcopy copy "C:\caminho\arquivos" "https://<storage-account>.blob.core.windows.net/<container>?<sas>" --recursive=true

# Download de arquivos
azcopy copy "https://<storage-account>.blob.core.windows.net/<container>?<sas>" "./pasta-local" --recursive=true

# Sincronização
azcopy sync "./pasta-local" "https://<storage-account>.blob.core.windows.net/<container>?<sas>" --delete-destination=true
