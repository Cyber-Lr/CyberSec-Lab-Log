# 🐧 Aprendizado Linux: Processos, Permissões e Estrutura

Este repositório registra minha jornada de aprendizado no ecossistema Linux. Os conceitos abaixo foram validados na prática utilizando uma máquina virtual com **Debian**, onde explorei desde a hierarquia de diretórios até a manipulação de processos em execução.

---

## 1. Estrutura do Sistema de Arquivos
O Linux segue uma hierarquia organizada a partir do diretório raiz `/`. Abaixo, os diretórios que explorei nesta semana:

* **`/` (Root):** O topo da hierarquia; todos os arquivos estão abaixo dele.
* **`/etc`:** Contém arquivos de configuração do sistema, como o `/etc/passwd`.
* **`/var`:** Armazena dados variáveis, como os logs do sistema em `/var/log/syslog`.
* **`/tmp`:** Destinado a arquivos temporários que podem ser apagados no reboot.
* **`/bin` e `/usr/bin`:** Onde residem os comandos e executáveis dos usuários comuns, como o `ls`.
* **`/root`:** O diretório pessoal (home) do SuperUsuário.

---

## 2. Gerenciamento de Processos
Um processo é a execução de operações que consomem recursos da máquina.

### Tipos de Processos Observados
* **Interativos:** Aguardam a interação direta do usuário.
* **Batch (Lote):** Executam sequências de tarefas programadas.
* **Tempo Real (rt):** Processos críticos com prioridade total.

### Ferramentas de Monitoramento
Para visualizar a saúde do sistema, utilizei:
1.  `top`: Monitoramento dinâmico em tempo real.
2.  `htop`: Versão visual e amigável do top.
3.  `ps aux`: Uma "foto" instantânea de todos os processos atuais, ideal para scripts.

### Estados e Controle
Processos podem estar em estados como **Executável, Dormente, Zumbi ou Parado**. Para gerenciá-los, apliquei os seguintes sinais:
* `KILL`: Finaliza o processo imediatamente.
* `TERM`: Encerra o processo de forma graciosa.
* `STOP` / `CONT`: Interrompe e retoma a execução.

---

## 3. Permissões e Grupos
Aprendi que o Linux gerencia o acesso através de três pilares: **Usuário Dono (u)**, **Grupo (g)** e **Outros (o)**.

### Níveis de Permissão
* **Leitura (r):** Visualizar conteúdo.
* **Escrita (w):** Alterar conteúdo.
* **Execução (x):** Rodar arquivos ou acessar diretórios.

### O Modo Octal
A representação numérica facilita a alteração rápida de permissões:
* **7 (4+2+1):** Leitura, Escrita e Execução.
* **5 (4+1):** Leitura e Execução.

### Comandos Praticados
* `ls -l`: Lista arquivos exibindo suas permissões.
* `chmod -R`: Altera permissões de forma recursiva em pastas e subpastas.
* `chown`: Define o proprietário e o grupo de um objeto.

---

## Reflexões do Aprendizado

### O que observei
* **Cálculo de Prioridade:** A prioridade real de um processo no kernel segue a lógica $Prioridade = 20 + NICE$.
* **Zumbis:** Entendi que um processo vira "Zumbi" quando perde a referência do processo pai.
* **Prática na VM:** Errar comandos de permissão no `/etc` me ensinou a importância do `sudo` e do backup de arquivos de configuração antes de editá-los.

### O que poderia ser explorado
* Automatização de tarefas via **Shell Script**.
* Configuração de permissões especiais (SUID/SGID).
* Gerenciamento de logs avançado com `journalctl`.