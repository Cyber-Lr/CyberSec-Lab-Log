## Relatório Técnico: Pós-Exploração e Gerenciamento de Usuários

### 1. Informações Gerais

* **Data:** 09 de Março de 2026.


* **Ambiente:** Sessão interativa via porta 1524.



### 2. Extração de Dados Sensíveis

Com o acesso privilegiado, foram extraídos dados críticos do sistema alvo:

* **Leitura do `/etc/passwd`:** Listagem completa de usuários e suas respectivas shells (muitos configurados com `/bin/false` ou `/usr/sbin/nologin`).


* **Leitura do `/etc/shadow`:** Acesso aos hashes de senhas dos usuários, incluindo `root`, `msfadmin` e `postgres`.



### 3. Tentativa de Persistência (Criação de Usuário)

Nesta etapa, houve uma tentativa de criar um novo usuário para garantir acesso futuro.

* **Erro de Nomeação:** O comando inicial `sudo adduser civer_l` (ou variações com espaços/caracteres inválidos) falhou. O sistema retornou uma mensagem de erro indicando que o nome não correspondia à expressão regular (`NAME_REGEX`) configurada no Debian/Metasploitable.


* **Resolução do Erro:** Foi sugerido pelo sistema o uso da flag `--force-badname`, porém o usuário optou por corrigir o nome para `ciberl`, que seguiu os padrões permitidos.


* **Configuração:** O usuário `ciberl` foi criado com sucesso, com a senha definida como `ciberl`. Foram preenchidas informações fictícias ("y") para os campos de perfil antes da finalização da sessão.



### 4. Conclusão da Atividade

A sessão foi encerrada às 23:59:49 após a criação do usuário e a tentativa (sem sucesso) de ler o histórico do bash em `/root/.bash_history`.
