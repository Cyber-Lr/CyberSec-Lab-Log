# Resultados de Varredura Nmap - Alvo: 10.0.0.45

## Varredura Agressiva (`-A -T5`)

**Início:** 08 de Março de 2026 às 17:30:15.


| Porta | Estado | Serviço | Versão |
| :--- | :--- | :--- | :--- |
| 21/tcp | open | ftp | vsftpd 2.3.4 (Permite Login Anônimo) |
| 22/tcp | open | ssh | OpenSSH 4.7p1 Debian |
| 23/tcp | open | telnet | Linux telnetd |
| 25/tcp | open | smtp | Postfix smtpd |
| 53/tcp | open | domain | ISC BIND 9.4.2 |
| 80/tcp | open | http | Apache httpd 2.2.8 |
| 1524/tcp | open | bindshell | Metasploitable root shell |
| 3306/tcp | open | mysql | MySQL 5.0.51a-3ubuntu5 |
| 5432/tcp | open | postgresql | PostgreSQL DB 8.3.0 - 8.3.7 |


**Informações do Sistema Operacional:**

* **Kernel:** Linux 2.6.9 - 2.6.33.


* **Hostname:** metasploitable.localdomain.



## Varredura Furtiva (`-sS -sV`)

**Início:** 08 de Março de 2026 às 17:23:08.
Esta varredura confirmou a presença de 23 portas abertas, focando na identificação silenciosa de versões de serviços.

---