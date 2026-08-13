# Roteiro prático de aprendizagem

Pipeline de atividades para extrair o máximo de conhecimento do conteúdo:

### Atividade 1 — Identificar a arquitetura

- Desenhar as quatro camadas TCP/IP.
- Desenhar as sete camadas OSI.
- Relacionar cada camada OSI com TCP/IP.
- Identificar os principais protocolos de cada camada.

### Atividade 2 — Estudar IPv4

- Identificar um endereço IPv4.
- Converter seus octetos para binário.
- Identificar os campos do cabeçalho IPv4.
- Estudar TTL.
- Estudar Protocol.
- Estudar fragmentação.
- Estudar Source/Destination Address.
- Analisar um pacote IPv4 no Wireshark.

### Atividade 3 — Estudar ARP

- Executar `arp`/ferramenta equivalente no sistema.
- Identificar a tabela ARP.
- Fazer comunicação com outro host.
- Observar a alteração da tabela ARP.
- Capturar um ARP Request no Wireshark.
- Capturar o ARP Reply.
- Identificar IP e MAC presentes nas mensagens.

### Atividade 4 — Estudar ICMP

- Executar `ping`.
- Capturar o tráfego com Wireshark.
- Identificar Echo Request.
- Identificar Echo Reply.
- Observar Type.
- Observar Code.
- Observar Checksum.
- Relacionar ICMP com IPv4.

### Atividade 5 — Estudar UDP

- Identificar portas de origem e destino.
- Observar o campo Length.
- Observar Checksum.
- Comparar UDP com TCP.
- Capturar uma comunicação UDP no Wireshark.

### Atividade 6 — Estudar TCP

- Identificar SYN.
- Identificar SYN/ACK.
- Identificar ACK.
- Observar o three-way handshake.
- Identificar Sequence Number.
- Identificar Acknowledgment Number.
- Identificar Flags.
- Identificar Window.
- Observar o encerramento da conexão.
- Relacionar pacotes aos estados TCP.

### Atividade 7 — Estudar portas e sockets

- Executar `netstat`.
- Identificar portas abertas.
- Identificar conexões estabelecidas.
- Identificar endereços locais.
- Identificar endereços remotos.
- Identificar TCP e UDP.
- Relacionar portas aos serviços.

### Atividade 8 — Montar o laboratório

- Instalar VirtualBox.
- Verificar SHA-256 do instalador.
- Instalar Extension Pack.
- Baixar Debian.
- Verificar a integridade da ISO.
- Criar VM Debian1.
- Configurar CPU/RAM/disco.
- Habilitar virtualização.
- Configurar NAT.
- Habilitar USB.
- Instalar Debian.
- Instalar Guest Additions.
- Instalar `net-tools`.
- Instalar Wireshark.
- Configurar o ambiente.
- Desabilitar IPv6 somente se isso for necessário para o laboratório.

---

# O que explicar ao final?

Ao dominar esse conteúdo, será capaz de explicar tecnicamente:

```text
Como uma aplicação gera dados
        ↓
Como TCP/UDP transporta esses dados
        ↓
Como IP endereça os hosts
        ↓
Como ARP encontra o MAC
        ↓
Como Ethernet transporta o frame
        ↓
Como roteadores encaminham pacotes
        ↓
Como o destino desencapsula os dados
```

Além disso, deverá conseguir olhar para uma captura no Wireshark e responder:

- Qual é o IP de origem?
- Qual é o IP de destino?
- Qual é o MAC de origem?
- Qual é o MAC de destino?
- Qual protocolo está sendo transportado?
- Qual é a porta de origem?
- Qual é a porta de destino?
- É TCP ou UDP?
- Se for TCP, qual é o estado da conexão?
- Quais flags estão presentes?
- Qual é o Sequence Number?
- Qual é o ACK?
- Qual é o TTL?
- Qual é o tamanho do pacote?
- Existe fragmentação?
- É uma mensagem ICMP?
- É um ARP Request ou Reply?

Esse é o ponto em que o estudo deixa de ser apenas **teórico** e passa para **análise real de tráfego de rede**.

---
