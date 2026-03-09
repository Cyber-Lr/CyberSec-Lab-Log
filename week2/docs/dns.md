# DNS - Relatório Técnico

Este relatório documenta o estudo e a estruturação do entendimento sobre como um domínio é "traduzido" na internet, utilizando uma VM **Debian**. Para a análise, foram utilizados o comando `dig` e o software **Wireshark**.

## Compreensão do Tráfego DNS

O serviço DNS traduz nomes de domínio para endereços IP que os servidores compreendam.

### Fluxo de Comunicação

1. **Cache Local:** O host verifica primeiramente o cache DNS. Se o alvo for encontrado, o processo externo é interrompido.


2. **Protocolo ARP:** Caso necessário, o host emite um broadcast para obter o endereço MAC do gateway, estabelecendo a comunicação entre equipamentos da rede.


3. **NAT:** O roteador encaminha a requisição ao recursor DNS, trocando o IP privado pelo público via tabela NAT.


4. **Hierarquia de Resolução:**

* **Recursor DNS:** Recebe a requisição inicial.


* **Servidor Raiz:** Direciona o recursor para o nameserver TLD.


* **TLD:** Indica o servidor responsável pelo hostname.


* **Nameserver Autoritativo:** Fornece o endereço IP final vinculado ao domínio.





## Protocolos de Transporte

* **UDP:** Utilizado na resolução DNS para priorizar velocidade.


* **TCP (3-way handshake):** Estabelece a conexão com o servidor de destino através das etapas **SYN**, **SYN-ACK** e **ACK**.

