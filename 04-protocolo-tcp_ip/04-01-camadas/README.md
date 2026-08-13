# 3. Camada de Acesso à Rede

É a camada inferior do TCP/IP.

Ela corresponde aproximadamente às camadas:

- Física;
- Enlace de Dados;

do modelo OSI.

Sua função é permitir que um dispositivo envie dados para outro dispositivo diretamente conectado à rede.

Ela precisa conhecer características específicas da tecnologia utilizada, como:

- estrutura dos frames;
- endereçamento físico;
- meio de transmissão;
- formato dos pacotes;
- tecnologia da rede.

## Principais funções

Uma das funções fundamentais é encapsular o **datagrama IP** dentro de um **frame** apropriado à tecnologia da rede.

Exemplo conceitual:

```text
Dados
 ↓
Segmento TCP/UDP
 ↓
Datagrama IP
 ↓
Frame Ethernet
 ↓
Bits
```

Outra função importante é relacionar:

```text
Endereço IP → Endereço MAC
```

Essa resolução é realizada, no IPv4, pelo **ARP**.

---

# 4. Camada de Internet

A camada Internet corresponde aproximadamente à camada de Rede do modelo OSI.

Sua principal responsabilidade é permitir o **endereçamento lógico e o roteamento de pacotes entre redes diferentes**.

Os principais protocolos apresentados são:

- IP;
- ARP;
- ICMP;
- IGMP.

---

# 5. Protocolo IP

O **Internet Protocol (IP)** fornece o endereçamento lógico dos hosts e das redes.

Existem duas versões principais:

- IPv4;
- IPv6.

## IPv4 × IPv6

| Característica | IPv4 | IPv6 |
|---|---|---|
| Tamanho do endereço | 32 bits | 128 bits |
| Representação | Decimal, 4 grupos | Hexadecimal, 8 grupos |
| Separador | `.` | `:` |
| Unicast | Sim | Sim |
| Multicast | Sim | Sim |
| Broadcast | Sim | Não |
| Anycast | Não tradicionalmente | Sim |
| Cabeçalho básico | 20 bytes | 40 bytes |
| Configuração | Manual/DHCP | Autoconfiguração disponível |
| IPsec | Suportado | Suporte integrado ao padrão |

Exemplos:

```text
IPv4:
192.168.1.10

IPv6:
2001:db8::1
```

---

# 6. Cabeçalho IPv4

Conhecer o cabeçalho IP é fundamental para **análise de tráfego e CyberSecurity**, pois seus campos permitem compreender como um pacote foi criado, encaminhado e tratado.

Os campos mais relevantes são:

### Version

Indica a versão do protocolo IP.

Para IPv4:

```text
Version = 4
```

### IHL — Internet Header Length

Indica o tamanho do cabeçalho IPv4.

O valor é expresso em unidades de **32 bits**.

O cabeçalho mínimo possui:

```text
20 bytes
```

### Total Length

Indica o tamanho total do datagrama IPv4:

```text
Cabeçalho + Dados
```

### Identification

Identificador utilizado principalmente para permitir que fragmentos pertencentes ao mesmo datagrama sejam posteriormente associados.

### Fragment Offset

Indica a posição de determinado fragmento dentro do datagrama original.

É utilizado em conjunto com os campos relacionados à fragmentação.

### TTL — Time To Live

Determina por quanto tempo, em termos de saltos de roteamento, um pacote pode permanecer na rede.

Cada roteador normalmente reduz o TTL em uma unidade.

Quando chega a:

```text
TTL = 0
```

o pacote é descartado.

Isso ajuda a impedir que pacotes permaneçam indefinidamente circulando em loops de roteamento.

### Protocol

Identifica qual protocolo da camada superior está transportado pelo IP.

Exemplos:

```text
TCP → 6
UDP → 17
ICMP → 1
```

### Header Checksum

Verifica a integridade **do cabeçalho IPv4**, e não dos dados transportados.

> O checksum IPv4 não garante a integridade do payload.

### Source Address

Endereço IPv4 do dispositivo de origem.

### Destination Address

Endereço IPv4 do dispositivo de destino.

---

# 7. ARP — Address Resolution Protocol

O **ARP** resolve uma diferença fundamental existente no IPv4/Ethernet.

O IPv4 utiliza:

```text
IP = 32 bits
```

Enquanto o Ethernet utiliza:

```text
MAC = 48 bits
```

Assim, um host pode saber:

```text
IP do destino
```

mas precisar descobrir:

```text
MAC correspondente
```

O ARP realiza essa associação.

## Funcionamento

Imagine:

```text
Host A
IP: 192.168.1.10

precisa comunicar com:

Host B
IP: 192.168.1.20
```

Host A consulta sua tabela ARP.

Se não encontrar:

```text
192.168.1.20 → MAC desconhecido
```

envia um:

```text
ARP Request
```

normalmente em **broadcast**.

O host que possui aquele endereço IP responde:

```text
ARP Reply
```

contendo seu endereço MAC.

A associação passa a ser armazenada na tabela ARP.

```text
192.168.1.20 → AA:BB:CC:DD:EE:FF
```

Essa informação permanece em cache por determinado período e é posteriormente atualizada/expirada.

---

# 8. Estrutura da mensagem ARP

Uma mensagem ARP contém informações relacionadas às camadas 2 e 3.

## Hardware Type

Identifica o tipo de tecnologia de hardware utilizada.

Exemplos:

```text
Ethernet
IEEE 802
Frame Relay
```

Para Ethernet, o valor tradicional é:

```text
1
```

## Protocol Type

Identifica o protocolo da camada de rede utilizado.

No caso mais comum:

```text
IPv4
```

## Hardware Address Length

Define o tamanho do endereço da camada 2.

Para Ethernet:

```text
48 bits = 6 bytes
```

## Protocol Address Length

Define o tamanho do endereço da camada 3.

Para IPv4:

```text
32 bits = 4 bytes
```

## Operation

Indica o tipo de operação ARP.

Principalmente:

```text
Request
Reply
```

## Source Hardware Address

MAC do dispositivo de origem.

## Source Protocol Address

IP do dispositivo de origem.

## Destination Hardware Address

MAC do dispositivo de destino.

## Destination Protocol Address

IP do dispositivo de destino.

---

# 9. Encapsulamento ARP

Depois de construída, a mensagem ARP é entregue à camada de enlace.

Ela se transforma no **payload de um frame Ethernet**.

Conceitualmente:

```text
Frame Ethernet
├── Cabeçalho Ethernet
│   ├── MAC destino
│   ├── MAC origem
│   └── EtherType
│
└── Payload
    └── Mensagem ARP
```

Em uma implementação Ethernet/IPv4 tradicional, uma mensagem ARP possui normalmente:

```text
28 bytes
```

---

# 10. ICMP — Internet Control Message Protocol

O **ICMP** é um protocolo associado ao IP e definido originalmente pela **RFC 792** para IPv4.

Seu objetivo é permitir o envio de:

- mensagens de erro;
- informações de controle;
- diagnósticos;
- feedback;
- testes de conectividade.

As mensagens ICMP podem ser divididas em:

### Mensagens de erro

Informam ao remetente que alguma condição impediu ou afetou o processamento do pacote.

### Mensagens informativas

São utilizadas para consultas, diagnósticos e testes.

---

# 11. ICMP e PING

> **PING não é um protocolo.**

O PING é uma **ferramenta** que utiliza mensagens ICMP para verificar conectividade.

O fluxo típico é:

```text
Host A
   │
   │ ICMP Echo Request
   ↓
Host B
   │
   │ ICMP Echo Reply
   ↓
Host A
```

Portanto:

```text
PING
 ↓
ICMP
 ↓
IP
 ↓
Ethernet
```

---

# 12. Cabeçalho ICMP

## Type

Campo de 8 bits que identifica o tipo de mensagem.

Exemplos:

```text
8  → Echo Request
0  → Echo Reply
3  → Destination Unreachable
5  → Redirect
11 → Time Exceeded
```

## Code

Fornece informações adicionais sobre o tipo da mensagem.

Por exemplo, uma mensagem `Destination Unreachable` pode utilizar diferentes códigos para indicar a razão específica da falha.

## Checksum

Verifica a integridade da mensagem ICMP.

## Message Body

Contém informações específicas da mensagem.

---

# 13. Principais mensagens ICMPv4

| Tipo | Mensagem | Finalidade |
|---:|---|---|
| 0 | Echo Reply | Resposta a Echo Request |
| 3 | Destination Unreachable | Destino inalcançável |
| 5 | Redirect | Sugestão de rota alternativa |
| 8 | Echo Request | Teste de conectividade |
| 11 | Time Exceeded | TTL excedido |
| 13 | Timestamp Request | Solicitação de timestamp |
| 14 | Timestamp Reply | Resposta ao timestamp |

---

# 14. IGMP — Internet Group Management Protocol

O **IGMP** é utilizado para gerenciamento de grupos **multicast IPv4**.

Um host pode:

- entrar em um grupo;
- permanecer associado;
- sair do grupo.

Um mesmo host pode participar de vários grupos multicast simultaneamente.

Exemplo conceitual:

```text
              ┌── Host A
              │
Grupo Multicast ── Host B
              │
              └── Host C
```

O IGMP permite gerenciar a participação nesses grupos.

Do ponto de vista de segurança, o material destaca que o IGMP pode ser desabilitado quando não é necessário, reduzindo funcionalidades que poderiam ser exploradas em determinados cenários.

---

# 15. Camada de Transporte

A camada de transporte fornece comunicação **processo-a-processo**.

Não basta saber:

```text
Computador A → Computador B
```

É necessário determinar:

```text
Processo X no computador A
        ↓
Processo Y no computador B
```

Para isso são utilizadas **portas**.

A camada de transporte também pode fornecer:

- controle de fluxo;
- controle de erros;
- ordenação;
- entrega confiável;
- multiplexação de processos.

Os principais protocolos abordados são:

```text
UDP
TCP
```

---

# 16. UDP — User Datagram Protocol

O UDP é um protocolo:

- sem conexão;
- simples;
- de baixo overhead;
- sem garantia de entrega;
- sem garantia de ordenação;
- sem estabelecimento prévio de conexão.

Isso não significa que o UDP seja "ruim". Ele é adequado quando a aplicação prefere baixa sobrecarga e pode lidar com perdas ou implementar seus próprios mecanismos.

---

# 17. Cabeçalho UDP

### Source Port

Porta utilizada pelo processo de origem.

### Destination Port

Porta utilizada pelo processo de destino.

### Length

Indica o tamanho total do datagrama UDP:

```text
Cabeçalho + Dados
```

### Checksum

Permite verificar a integridade do datagrama UDP.

---

# 18. TCP — Transmission Control Protocol

O TCP é um protocolo:

- orientado à conexão;
- confiável;
- baseado em comunicação processo-a-processo;
- capaz de controlar fluxo;
- capaz de detectar perdas;
- capaz de ordenar dados.

Antes de transmitir dados normalmente, TCP estabelece uma conexão lógica.

Depois:

```text
Estabelecimento
      ↓
Transferência
      ↓
Encerramento
```

---

# 19. Principais campos do cabeçalho TCP

### Source Port / Destination Port

Identificam os processos envolvidos na comunicação.

### Sequence Number

Identifica a posição dos dados dentro do fluxo TCP.

Permite:

- ordenar dados;
- identificar segmentos;
- detectar perdas.

### Acknowledgment Number

Indica ao remetente quais dados foram recebidos/qual sequência é esperada.

### Data Offset

Indica o tamanho do cabeçalho TCP e, consequentemente, onde começam os dados.

### TCP Flags

Controlam diferentes aspectos da conexão.

As principais são:

```text
SYN
ACK
FIN
RST
PSH
URG
```

### Window

Indica a quantidade de dados que o receptor está preparado para receber sem confirmação adicional, participando do **controle de fluxo**.

---

# 20. TCP Three-Way Handshake

O estabelecimento de uma conexão TCP ocorre por meio do chamado **three-way handshake**.

Fluxo simplificado:

```text
Cliente                         Servidor
   │                                │
   │ -------- SYN ----------------> │
   │                                │
   │ <------- SYN + ACK ----------- │
   │                                │
   │ -------- ACK ----------------> │
   │                                │
   │       ESTABLISHED              │
```

### Etapa 1 — SYN

O cliente solicita o estabelecimento da conexão.

### Etapa 2 — SYN + ACK

O servidor aceita a solicitação e confirma o SYN recebido.

### Etapa 3 — ACK

O cliente confirma a resposta.

A conexão passa para:

```text
ESTABLISHED
```

---

# 21. Estados TCP

Uma conexão TCP é gerenciada pelo sistema operacional por meio de **sockets** e de uma **máquina de estados finitos (FSM)**.

## CLOSED

Não existe conexão ativa.

## LISTEN

O servidor está aguardando uma conexão.

## SYN-SENT

O host enviou SYN e aguarda resposta.

## SYN-RECEIVED

O host recebeu SYN e está aguardando a confirmação correspondente.

## ESTABLISHED

A conexão está estabelecida e os dados podem ser transferidos.

## FIN-WAIT-1

O host iniciou o encerramento da conexão.

## FIN-WAIT-2

O host recebeu confirmação do seu FIN e aguarda o FIN do outro lado.

## CLOSE-WAIT

O host recebeu solicitação de encerramento e aguarda que a aplicação local finalize.

## LAST-ACK

O host enviou seu FIN final e aguarda o ACK correspondente.

## CLOSING

Ambos os lados enviaram FIN e aguardam a confirmação final.

---

# 22. Camada de Aplicação

É a camada que fornece serviços de rede diretamente utilizados por aplicações.

> A camada de aplicação do TCP/IP não significa que programas como Word ou Excel sejam "protocolos de aplicação".

Um navegador, por exemplo, utiliza protocolos da camada de aplicação.

Exemplo:

```text
Navegador
   ↓
HTTP
   ↓
TCP
   ↓
IP
   ↓
Ethernet
```

---

# 23. Portas

As portas permitem identificar processos e serviços.

A comunicação pode ser representada por:

```text
IP:PORTA
```

Exemplo:

```text
192.168.1.10:80
```

Entretanto, tecnicamente, uma conexão é melhor representada pelo conjunto de informações que compõe um **socket**, normalmente envolvendo:

```text
IP origem
Porta origem
IP destino
Porta destino
Protocolo de transporte
```

---

# 24. Faixas de portas

A IANA organiza as portas em três grandes faixas:

### System / Well-Known Ports

```text
0–1023
```

Utilizadas por serviços amplamente padronizados.

### Registered Ports

```text
1024–49151
```

Associadas a aplicações e serviços registrados.

### Dynamic / Private Ports

```text
49152–65535
```

Normalmente utilizadas dinamicamente por aplicações clientes e outros usos privados.

---

# 25. Principais portas

| Serviço | Transporte | Porta | Função |
|---|---|---:|---|
| SSH | TCP | 22 | Acesso remoto seguro |
| Telnet | TCP | 23 | Acesso remoto sem criptografia |
| SMTP | TCP | 25 | Envio/transferência de e-mail |
| DNS | UDP/TCP | 53 | Resolução de nomes |
| DHCP | UDP | 67/68 | Configuração dinâmica |
| HTTP | TCP | 80 | Web |
| POP3 | TCP | 110 | Recebimento de e-mail |
| NTP | UDP | 123 | Sincronização de relógio |
| FTP | TCP | 21 | Transferência de arquivos |

> **Observação técnica:** o material apresenta "65353" para o limite de portas, mas o correto é **65535**, pois uma porta possui 16 bits: `2¹⁶ = 65.536 valores`.

---

# 26. Socket

Um socket representa um **endpoint de comunicação**.

De maneira simplificada:

```text
IP + Porta
```

Exemplo:

```text
200.177.9.120:80
```

Em uma comunicação TCP real:

```text
Cliente
192.168.1.10:53000
        │
        │ TCP
        ↓
Servidor
200.177.9.120:80
```

O sistema operacional mantém informações sobre esses endpoints e seus estados.

Uma ferramenta tradicional para observar essas conexões é:

```text
netstat
```

---

