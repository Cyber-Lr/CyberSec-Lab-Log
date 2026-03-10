## Relatório Técnico : Exploração de Bind Shell (Vulnerabilidade Port 1524)

### 1. Informações Gerais

* **Data:** 09 de Março de 2026.


* **Alvo:** Metasploitable 2 (IP: `10.0.0.45`).


* **Ferramenta:** Netcat (`nc`).



### 2. Descrição da Atividade

O objetivo foi validar a presença de um *bind shell* na porta **1524**, comumente associada ao serviço `ingreslock` em sistemas deliberadamente vulneráveis.

### 3. Execução e Erros de Sintaxe

* **Erro Inicial:** Tentativa de conexão utilizando notação CIDR (`10.0.0.45/24`) no Netcat. O utilitário retornou erro de *parsing*, pois espera um endereço IP único, não um intervalo de rede.


* **Correção:** O comando foi corrigido para `nc -n -vv 10.0.0.45 1524`, estabelecendo conexão imediata com privilégios de **root**.



### 4. Coleta de Informações (Enumeration)

* **Identificação:** O comando `whoami` confirmou acesso como superusuário (`root`).


* **Diretórios:** Foi realizada a listagem do diretório `/home`, identificando os usuários: `ftp`, `msfadmin`, `service` e `user`.