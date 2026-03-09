# Wireshark - Relatório Técnico

Análise detalhada de fluxos de comunicação TCP/UDP e identificação de FLAGS utilizando uma VM **Debian**.

## Configuração do Ambiente

* **Instalação:** `sudo apt install wireshark`.


* **Permissões:** O usuário foi adicionado ao grupo do Wireshark para permitir a interceptação de dados por não-superusuários.


* **Filtros Aplicados:**
    * Filtro inicial por host: `ip.addr == 10.0.2.15`.

    * Filtro por protocolo: `tcp`.





## Observações de Tráfego

Durante o acesso ao domínio `uol.com.br`, foram identificados:

* **Endereços:** IPs de origem/destino e endereços MAC (Camada 2 do modelo OSI).


* **Protocolos:** Além do TCP, foi interceptado o protocolo **TLS**.


* **Saúde da Conexão:** Identificadas retransmissões e perdas de dados onde a conexão foi encerrada (sinalizadas em vermelho pelo programa).



---