

# Relatório Consolidado: Infraestrutura de Rede e Segurança

**Estudante:** Cyber_L

**Ambiente:** Debian Linux (VM) | Metasploitable 2

## 1. Configuração do Ambiente de Laboratório

Para a realização dos estudos de penetração e análise de tráfego, foi estruturado um ambiente isolado utilizando o **Oracle VirtualBox**.

### Topologia de Rede (Rede Interna)


**Máquina Principal (Atacante):** Debian Linux.


* **IP:** `10.0.0.46` | **Mascara:** `255.225.255.0`.

 **Máquina Alvo (Vulnerável):** Metasploitable 2.

* **IP:** `10.0.0.45` | **Mascara:** `255.255.255.0`.



### Procedimentos de Configuração

As interfaces foram configuradas manualmente para garantir a persistência durante os testes:

1. **Identificação:** O comando `ip link` foi utilizado para listar as interfaces disponíveis.
2. **Atribuição:** `sudo ip addr add [IP]/[Mascara] dev [interface]` foi aplicado em ambas as máquinas.
3. **Ativação:** As interfaces foram subidas com `sudo ip link set [interface] up`.
4. **Transferência de Arquivos:** Instalado o servidor `vsftpd` e configurado o firewall `ufw` para permitir tráfego na porta **21/TCP**.



## 2. Análise de Protocolos (DNS e TCP)

### O Fluxo de Resolução DNS

O DNS traduz nomes de domínio para endereços IP. O processo observado seguiu estas etapas:


**Verificação de Cache:** O host verifica primeiramente o cache DNS local antes de iniciar a busca externa.
 
**Resolução Recursiva:** A requisição passa pelo **Recursor DNS**, que consulta o **Servidor Raiz**, seguido pelo **Nameserver TLD** e, por fim, o **Nameserver Autoritativo**.



**Protocolo de Transporte:** O DNS utiliza predominantemente **UDP** para priorizar a velocidade na tradução.



### O Handshake TCP

Para a comunicação de dados após a resolução DNS, o protocolo **TCP** estabelece a conexão através do *3-way handshake*:

1. **SYN:** Sincronização inicial.


2. **SYN-ACK:** Confirmação do servidor.


3. **ACK:** Confirmação final do host.

 

## 3. Monitoramento e Diagnóstico (Wireshark)

Utilizando o Wireshark no Debian, foi possível interceptar e interpretar o tráfego real.


**Configuração:** O usuário foi adicionado ao grupo `wireshark` (`sudo usermod -aG wireshark @usuario`) para capturas sem privilégios de root.


 
**Filtros de Captura:** Foram utilizados filtros como `ip.addr == 10.0.2.15` e `tcp` para isolar o tráfego de interesse.


 
**Observações de Campo:** Identificou-se o uso de portas de origem/destino, endereços MAC e protocolos como **TLS**. Foram notadas retransmissões de pacotes (sinalizadas em vermelho), indicando falhas pontuais na comunicação.



---

## 4. Varredura de Vulnerabilidades (Nmap)

Foram realizados scans detalhados contra o alvo `10.0.0.45` para identificar superfícies de ataque.

### Resultados da Varredura Agressiva (`nmap -A -T5`)

A varredura identificou diversas portas críticas abertas:

**Porta 21 (FTP):** vsFTPd 2.3.4 (Permite login anônimo).


**Porta 22 (SSH):** OpenSSH 4.7p1 Debian.


**Porta 80 (HTTP):** Apache httpd 2.2.8.

**Porta 1524 (Bindshell):** Root shell exposto do Metasploitable.


**Porta 3306 (MySQL):** Versão 5.0.51a-3ubuntu5.



### Conclusão Técnica

O ambiente Metasploitable 2 revelou-se extremamente vulnerável, apresentando serviços desatualizados e portas de shell direto (1524), servindo como um excelente estudo de caso para práticas de Red Team.

---
